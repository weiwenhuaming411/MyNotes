## Vue组件间通信方式

### props(父←→子)
    <Home :name="name"></Home>
    props(['myCar'])
    props({myCar: String, data: String})
    props({
        myCar: {
            type: String, 
            required: true, 
            default: '奥迪'
        }
    })

    路由中的props
        方式：对象、布尔值、函数

### 自定义事件(子→父)
    <Father @msg="callback"/>  or  this.$on('msg', ()=>{})
    beforeDestroy(){
        this.$off('msg')
    }

    <Child>
        this.$emit('msg', data)
    </Child>

    *组件绑定原生DOM事件时，需要使用@click.native=""修饰符。
            
### $bus(全能)
    main.js:
        Vue.prototype.$bus = this;

    Child1.vue:
        this.$bus.$on('msg', ()=>{})
        beforeDestroy(){
            this.$bus.$off('msg')
        }

    Child2.vue:
        this.$bus.$emit('msg', data)

### pubsub-js
    场景：全能
        npm i pubsub-js
        import PubSub form 'pubsub-js';
        Vue.use(PubSub)

        PubSub.subscribe('msg', callback(msg, data))
        PubSub.publish('msg', data)

        PubSub.unsubscribe(pid)

### vuex(全能)

### v-model(场景:封装UI组件)
    <标签>:
        <input type="text" v-model="data">
        <input type="text" :value='date' @input='data=$event.target.value'>

    <组件>:
        <Father v-model='data'></Father>
        <Father :value='data' @input='data=$event'></Father>
    
        <Child>
            <input type='text' :value=value @input="@emit('input', $event.target.value)">
            props: ['value']
        </Child>

### .sync修饰符(与v-model相似)
    <Home :money='money' @update:money='money = $event'></Home>
    <Home :money.sync='money'></Home>

    <button @click="@emit('update', money - 100)">
    props: ['money']

    :money.sync="money"
        传递props: ['money']
        绑定自定义事件：@update:money='money = $event'

### this.$attrs(祖←→孙)/$listeners
    this.$attrs:
        <Father/>  <Child/>  <Son/>
        
        <Child v-bind="$attrs"/>  // 获取祖组件传递的props数据并传递给孙组件
    
    $listeners:
        获取父组件传递的自定义事件
        v-on="$listeners"

### $children/$parent
    $children
        获取当前组件中全部子组件  //当组件过多时[0]索引值并非按顺序排列

    $parent
        获取当前组件的父组件

### 混入mixin
        export default {}

        import myMixin from ''
        mixins: [myMixin]

## API
    Vue2:
        export default {
            name: 'app',
            components: {},
            props: ['data'],
            data(){return{}},
            methods:{},
            computed:{},
            watch:{}
        }

    ### this.$options
        vue的实例属性，是一个对象，获取vue组件的方法和数据。
        this.$options.data()这个是vue原始的数据，就是你页面刚加载时的data
        this.$data这个是现在阶段的vue数据，就是你改变data的数据

### composition API
    Vue.component()  // 注册全局组件
        import Home from ''
        Vue.component('Home', Home)

    Vue.

### 样式

    深度选择器
        原生CSS  >>> .class
        less  /deep/ .class
        scss  ::v-deep .class

    封装的过渡与动画
        元素进入的样式
        .v-enter：进入的起点  // Vue3: .v-enter-from
        .v-enter-active：进入过程
        .v-enter-to：进入的终点

        元素离开的样式
        .v-leave：离开的起点  // Vue3: .v-leave-from
        .v-leave-active：离开过程
        .v-leave-to：离开的终点

        2.使用<transition>包裹要过渡的元素，并配置name属性：
            <transition-group name="hello" appear>
                <h1 v-show="!isShow" key="1">你好啊！<h1>
                <h1 v-show="!isShow" key="2">你好啊！<h1>
            </transition-group>

        备注：若有多个元素需要过渡，则需要使用：<transition-group>,且每个元素都要指定key值

### Vue语令
    v-bind(单向):  
        v-bind:name="data"
            <input type='text' :name="data">  // 简写
            <Father v-bind='{name:'杨超越',age:18}'/>  // 对象形式
        
    v-model(文本框、单选、复选)
        文本框: 收集value
        单选: 收集value值，且要给标签配置value值
            <input type="radio" v-model="radio" value='足球'>
            <input type="radio" v-model="radio" value='篮球'>
        复选: 
            1.没有配置input的value属性，收集的是布尔值
            2.配置input的value属性：
                1.v-model的初始值是非数组，那么收集的是布尔值
                2.v-model的初始值是数组，那么收集的就是value组成的数组

        v-model的三个修饰符：
            .lazy  // 失去焦点再收集数据
            .number  // 输入字符串转为有效的数字
            .trim  // 输入首尾空格过滤

### 事件语令
    <Home @click.native></Home>  // 组件绑定原生事件，不加修饰符相当于自定义事件

    v-onclick="function()"  // 简写@click="",

    v-on 修饰符：
        @click.prevent=""  // 取消默认行为
        @click.noce=""  // 只触发一次
        .stop  // 阻止事件冒泡
        .capture  // 使用事件的捕获模式
        .self  // 只有event.target是当前操作的元素时才触发事件
        .passive  //事件的默认行为立即执行，无需等待事件回调执行完毕
        .native  // 自定义事件变成原生事件(组件使用时)  // vue3移除


## vue.config.js
    配置代理服务器：
        devServer:{
            proxy:{
                '/api':{
                    target:'http://127.0.0.1:8080',
                    pathRewrite:{'^/api':''},  // 正则匹配重写路径
                    ws:true,  // 用于支持websocket
                    changeOrigin:true  // 用于控制请求头中的host值
                }
            }
        }

## Vue-Vuex
    ## 基本使用
        npm i vuex@3

        src/store/index.js
            import Vue from 'vue'
            import Vuex from 'vuex'
            Vue.use(Vuex)

            import Home from './Home'

            export default new Vuex.Store({
                modules: {
                    Home
                }
            })

        src/store/Home/index.js
            const actions = {}
            const mutations = {}
            const state = {}
            const getters = {}

            export default {
                namespaced: true,
                actions,
                mutations,
                state,
                getters
            }

        main.js:
            import store from './store'

            new Vue({
                el:'#app',
                render: h => h(App),
                store
            })

    ## API
        读取vuex中的数据：$store.state.sum
        修改vuex中的数据：$store.dispatch('函数',数据)或$store.commit('函数',数据)

        function(context){}:小仓库

        map方法的使用
            import {mapState,mapGetters,mapActions,mapMutations} from 'vuex'

            1.mapState方法：
                computed:{
                    ...mapState({he:'sum',xuexiao:'school',xueke:'subject'})
                    ...mapState(['sum','school','subject'])
                }

            2.mapGetters方法：
                computed:{
                    ...mapGetters({bigSum:'bigSum'})
                    ...mapGetters(['bigSum'])
                }

            3.mapActions方法：用于帮助我们生成与actions对话的方法，即包含：$store.dispatch(xxx)的函数
                methods:{
                    ...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'}),
                    ...mapActions(['jiaOdd','jiaWait']),
                }

            4.mapMutations方法：用于帮助我们生成与mutations对话的方法，即包含：$store.commit(xxx)的函数
                methods:{
                    ...mapMutations({increment:'JIA',decrement:'JIAN'})
                    ...mapMutations(['JIA','JIAN'])
                }

    ##  开启命名空间后，组件中读取state数据：
            1.方法一：this.$store.state.Count.sum
            2.方法二：...mapState('Count',['sum','school','subject'])

        开启命名空间后，组件中读取getters数据：
            1.方法一：this.$store.getters['Person/fistPersonName']
            2.方法二：...mapGetters('Count',['bigSum'])

        开启命名空间后，组件中读取dipatch数据：
            1.方法一：this.$store.dispatch('Home/function', data)
            2.方法二： ...mapActions('Count',['jiaOdd','jiaWait']),

        开启命名空间后，组件中读取commit数据：
            1.方法一：this.$store.commit('Person/ADD_PERSON',personObj)
            2.方法二：...mapMutations('Count',['JIA','JIAN']),

## Vue-router

### 基本使用
    vue2:
        npm i vue-router@3  //安装
        src/router/index.js
            import Vue from 'vue';
            import VueRouter from 'vue-router';
            Vue.use(VueRouter)  // 应用
            import Home from '@/views/Home'
            const router = new VueRouter({mode: 'history/hash',routes:[{}]})
            export default router

        main.js
            import route from '@/router'
            new Vue({el:'#app',render: h => h(App),router})

### 展示/切换
    vue2:
        <router-link to=""></router-link>  // 字符串
        <router-link :to="{}"></router-link>  // 对象
        <router-view></router-view>  // 展示位置

    编程式路由导航:
        this.$router.push()
        this.$router.replace()
        
        this.$router.back()  // 后退
        this.$router.forward()  // 前进
        this.$router.go(-1/2/3)  // 前进/后退

### query/params传参/路由props
    query传参
        <router-link :to="`/about?id=${m.id}&title=${m.title}`"></router-link>  // 字符串写法
        <router-link :to="{path:'/about',query:{id:m.id,title:m.title}}"></router-link>  // 对象写法

    params参数
        路由占位：
            routes: [{path:'detail/:id/:title?'}]  //占位符声明接受params参数
        传递参数
            <router-link :to="`/about/${m.id}/${m.title}`"></router-link>  // 字符串写法

            // 对象写法
            <router-link :to="{
                name:'hello',  //params对象写法，必须使用name配置，不能使用path
                params:{id:m.id,title: '' || undefined}  //当参数是空串的时候，用undefined解决
            }">
            </router-link>

    接收参数
        this.$route.query.id
        this.$route.params.id

    路由props
        {
            path:'/detail',
            component:Detail,
            props:{a:1,b:'hello'},  //值为对象，该对象中的所有key-value都会以props的形式传给组件
            props:true,   //值为布尔值，若布尔值为真，就会把该路由组件收到的所有params参数，以props的形式传给组件
            //值为函数，该函数返回的对象中每一组key-value都会通过props传给组件
            props($route){
                return{
                    id:$route.query.id,
                    title:$route.params.title
                }
            }
        }

### 缓存路由组件，让不展示的路由组件保持挂载，不被销毁。
    1.具体编码：
        <keep-alive include="News">
            <router-view></router-view>
        </keep-alive>
            
    ## 两个新的生命周期钩子（路由组件独有）
        activated(){}  //路由组件激活时触发
        deactivated(){}  //路由组件失活时触发

    ## 组件内守卫: 进入之前，离开之前  // 不能获取当前组件实例this，因为组件实例还没创建
        beforeRouteEnter(to, from, next){}
        beforeRouteLeave(to, from, next){}

### 重写push|replace
    let originPush = VueRouter.prototype.push;
    let originReplace = VueRouter.prototype.replace;

    VueRouter.prototype.push = function(location, resolve, reject){
        if(resolve && reject){
            // call,改变this指向
            originPush.call(this, location, resolve, reject);
        }else{
            originPush.call(this, location, () => {}, () => {});
        }
    }
    VueRouter.prototype.replace = function(location, resolve, reject){
        if(resolve && reject){
            originReplace.call(this, location, resolve, reject);
        }else{
            originReplace.call(this, location, () => {}, () => {});
        }
    }

## 项目应用
    菜单联动、轮播图、分页器、放大镜、面包屑、登录、注册、日历