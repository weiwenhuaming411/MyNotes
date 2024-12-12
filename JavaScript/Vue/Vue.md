## 安装流程 √
    npm create vue@latest  // 通过vite创建Vue3项目
    npm i  // 安装项目依赖
    npm run dev
    npm run build  // 项目打包

    Vue.js devtools  // Chrome安装扩展程序

## API
    <component :is="Count"></component>  // 组件

<!-- v-bind(单向) -->
    v-bind:data="data"  // 简写(:data='data')
        
<!-- v-model -->
    v-model='data'
        .lazy  // 失去焦点再收集数据
        .number  // 输入字符串转为有效的数字
        .trim  // 输入首尾空格过滤

<!-- v-on -->
    @click='fn'
        .prevent=""  // 取消默认行为
        .noce=""  // 只触发一次
        .stop  // 阻止事件冒泡
        .capture  // 使用事件的捕获模式
        .self  // 只有event.target是当前操作的元素时才触发事件
        .passive  //事件的默认行为立即执行，无需等待事件回调执行完毕

<!-- 生命周期 -->
    setup()  // 创建

    onBeforeMount(()=>{})  // 真实DOM挂载之前（虚拟DOM完成）
    onMounted(()=>{})  // 挂载完毕(虚拟DOM替换成真实DOM)

    onBeforeUpdate(()=>{})  // 更新数据：更新之前（页面尚未和数据保持同步）  
    onUpdated(()=>{})  // 更新数据：更新之后（页面和数据保持同步）

    onBeforUnmounted(()=>{})  // 卸载之前
    onUnmounted(()=>{})  // 卸载之后

    this.$nextTick(()=>{})  // 模板下一次更新后????
    
#### ref()/reactive()/toRef()/toRefs()/computed()/watch()/watchEffect() √
    import {ref, reactive, toRef, toRefs, computed, watch, watchEffect, useTemplateRef} from 'vue'

<!-- 配置/props -->
    defineOptions({name: '', inheritAttrs: false})  // 设置组件名
    defineProps(['data'])  // props
    withDefaults(defineProps<{msg:any}>(), {msg:{name:'Tony'}})  // 设置props默认值(Ts)
    defineExpose({})  // 允许外部访问数据

<!-- ref(ID)属性 -->
    <div ref='DIV'></div>
    let title = useTemplateRef('DIV')
    onMounted(()=>{title.value})  // 获取dom元素
        
    <Child1 ref='CHILD'></Child1>
    let CHILD = useTemplateRef(CHILD)
    onMounted(()=>{CHILD.value?.person})  // 获取子组件数据

<!-- 定义数据 -->
    ref()  // 定义基础数据类型(.value取值)
    reactive()  // 定义对象/数组数据类型(重新分配新对象用Object.assgin(obj, obj2))
    toRef(obj, '属性')  // let name = toRef(person, 'name')  // 让其指向另一个对象
    toRefs(obj)  // let {name, age} = toRefs(person)  // 让其指向另一个对象

<!-- 计算函数 -->
    computed(()=>{})  // 只读
    computed({get(){}, set(value){}})  // 读写

<!-- 监视函数  -->
    let stopWatch = watch(data/()=>data.name, (newValue, oldValue)=>{}, {deep:true,immediate:false})
    stopWatch()  // 停止监视

    watchEffect(()=>{})  // 函数中用到哪个属性就监视哪个属性

<!-- 
    hook自定义函数
        hooks/usePerson.js:
            export default ()=>{fn}

            import usePerson from '../hooks/usePerson.js'
            let {fn} = usePerson()

    composition API
        shallowRef()  // 只处理基本类型数据,不进行对象的响应书处理
        shallowReactive()  // 只处理第一层数据
        shallowReadonly()  // 第一层只读
        readonly()  // 让一个响应式数据变更为只读(深只读),p = readonly(person)

    toRaw/markRaw
        toRaw()  // 将一个由reactive生成的响应式对象转变为普通对象
        markRaw()  // 标记一个对象,使其永远不会再成为响应式对象

    customRef(自定义的ref)
        import {customRef} from 'vue'
        let name = myRef('hello')
            function myRef(value){
                return customRef((track, trigger)=>{
                    return {
                        get(){
                            track()  // 通知vue追踪value的变化
                            return value
                        },
                        set(newValue){
                            value = newValue
                            trigger()  // 通知vue去重新解析模板
                        }
                    }
                })
            }

    Teleport(传送门)
        能让html结构移动到指定位置
        <teleport to='body'>html</teleport>

    Suspense(异步组件)
        等待异步组件时渲染一些额外内容,让应用有更好的用户体验
        import {Suspense} from 'vue'
        <Suspense>
            <template v-slot='default'>  // 需要展示的组件
                <Child/>
            </template>
            <template v-slot='fallback'>  // 展示正在加载中...
                <div>正在加载中...</div>
            </template>
        </Suspense>

    defineAsyncComponent()动态引入组件
        const child = defineAsyncComponent(()=>import('./'))

    isRef()  // 检查一个值是否为ref对象
    isReactive()  // 检查一个值是否为isReactive响应式代理
    isReadonly()  // 检查一个值是否为isReadonly只读代理
    isProxy()  // 检查一个值是否为isReactive响应式代理、isReadonly只读代理

#### 缓存路由组件，让不展示的路由组件保持挂载，不被销毁。
    <keep-alive include="Person">  // include匹配缓存组件/exclude匹配不需要缓存组件
        <component :is="view"></component>
    </keep-alive>
            
#### 两个新的生命周期钩子（路由组件独有）
    import { onActivated, onDeactivated } from 'vue'

    onActivated(()=>{})  // 路由组件激活时触发
    onDeactivated(()=>{})  // 路由组件失活时触发

#### 组件内守卫: 进入之前，离开之前
    beforeRouteEnter(to, from, next){}
    beforeRouteLeave(to, from, next){}
 -->

## Vue-router √
    src/views/...  // 路由组件

    $route： 每个组件都有自己的$route（路由），获取路由信息【path、query、params等等】
    $router： 整个应用只有一个$router（路由器），进行编程式导航进行路由跳转【push|replace】

<!-- 基本配置 -->
    npm i vue-router
    src/router/index.ts:
        import {createRouter, createWebHistory} from 'vue-router'
        improt Home from 'path'  // 引入路由组件
        const router = createRouter({
            history: createWebHistory(),  // 指定路由器的工作模式,createWebHashHistory()  // 带#号
            routes: [
                {
                    // name: '',
                    path: '/home',  // 路径
                    component: Home,  // 匹配组件  // component: ()=>import('path'),  // 按需引入
                    // children:[{path:'child',component: Child}],  // 嵌套路由
                    // meta: {},
                    // beforeEnter: ()=>{}  // 路由独享守卫,进入之前
                },
                {path: '/',redirect: '/person'}  // 重定向
            ]
        })
        router.beforeEach((to, from, next) => {})  // 全局前置路由守卫--初始化的时候被调用、每次路由切换之前被调用
        router.afterEach((to, from) => {})  // 全局后置路由守卫--每次路由切换之后被调用
        export default router

    main.js:
        import router from 'path'
        createApp(App).use(router).mount('#app')

 <!--展示/切换  -->
    <RouterLink to='/home'></RouterLink>  // 字符串
    <RouterLink to='{path: '/home'/name:'首页'}'></RouterLink>  // 对象
    <RouterView></RouterView>

<!-- 样式 -->
    <RouterLink replace active-calss="active" to=""></RouterLink>  // replace无痕模式

#### query/params传参 √
    import {useRoute} from 'vue-router'
    const route = useRouter()

    query传参:
        <RouterLink :to="`/home?id=${person.id}&title=${person.name}`"></RouterLink>  // 字符串写法
        <RouterLink :to="{path:'/home',query:{id:person.id}}"></RouterLink>  // 对象写法
        
    params参数：
        routes: [{path:'home/:id/:name?'}]  // 路由占位,占位符声明接受params参数
        传递参数:
            <RouterLink :to="`/home/${person.id}/${person.name}`"></RouterLink>  // 字符串写法

            // 对象写法
            <RouterLink :to="{
                name:'hello',  // params对象写法，必须使用name配置，不能使用path
                params:{id:id,title: '' || undefined}  // 当参数是空串的时候，用undefined解决
            }">
            </RouterLink>

    获取参数:
        route.query.id
        route.params.id
        let {query} = toRefs(route)  // 解构赋值

<!-- 路由中的props -->
    方式：对象、布尔值、函数
    {
        path: '/home/:id',
        component: Home,
        props: true,   // 布尔值，把该路由组件收到的所有params参数，以props的形式传给组件
        // props: {a:1,b:'hello'},  //对象，所有key-value都会以props的形式传给组件
        // props($route){
            return{
                id:$route.query.id,
                title:$route.params.title
            }
        }  // 函数，每一组key-value都会通过props传给组件
    }

#### push()/replace()编程式导航 √
    import {useRouter} from 'vue-router'
    const router = useRouter()

    router.push({path:'/color',query:{id:color.id}})  // 有历史记录
    router.replace()  // 无痕模式
    
    router.back()  // 后退
    router.forward()  // 前进
    router.go(-1/2/3)  // 前进/后退

<!-- 重写push|replace -->???
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

## pinia数据集中式管理(全能) √
    npm i pinia  // 安装pinia

    main.js:
        import {createPinia} from 'pinia'  // 引入
        const pinia = createPinia()  // 创建
        app.use(pinia)  // 应用

    store/count.ts:
        import {defineStore} from 'pinia'
        
        import { ref,computed } from 'vue'
        export default defineStore('count',()=>{
            let sum = ref(0)  // 相当state
            let bigSum = computed(()=>{return sum.value*10})  // 相当getters
            function increment(value:number){sum.value += value}  // 相当actions
            return {sum, increment, bigSum}
        })
    
    import {storeToRefs} from 'pinia'  // 方便解构赋值,只会转换数据
    import useCountStore from '@/store/count'
    const countStore = useCountStore()
    let {sum,bigSum} = storeToRefs(countStore)

<!-- 修改数据 -->
    countStore.sum = ''
    countStore.$patch({sum: 666})
    countStore.increment()

<!-- $subscribe: (订阅) -->
    contStore.$subscribe((mutate, state)=>{})

<!-- 
    export default defineStore('count',{
        // 动作函数
        actions: {
            increment(value){this.sum += value}  // countStore.increment()调用
        },
        // 状态管理
        state(){
            return {sum:0}
        },
        getters:{
            bigSum(state){return this.sum += 10}  // 直接用值
            // bigSum: state => state.sum * 10
        }
    })
 -->

## Vue组件间通信方式 √
<!-- defineProps(父←→子) -->
        <Home :name="name"></Home>
        defineProps(['myCar'])
        defineProps({myCar: String, data: String})
        defineProps({
            myCar: {
                type: String, 
                required: true, 
                default: '奥迪'
            }
        })

        路由props:
            方式：对象、布尔值、函数

<!-- defineEmits自定义事件(子→父) -->
        <Child @send-data="getData"></Child>
        function getData(){}

        let emit = defineEmits(['send-data'])
        emit('send-data', data)

<!-- $refs(所有子组件实例)/$parent(获取父组件实例) -->
    $refs:
        <Child ref='CHILD'/>
        <button @click="getAllChild($refs)"></button>  // 获取组件所有的子组件实例
        $refs.CHILD.data  // 获取数据

    $parent:
        <button @click="getParent($parent)"></button>  // 获取父组件实例
        $parent.data  // 获取数据
            
<!-- $attrs(祖←→孙) -->
    没有声明接收的props参数会存到$attrs里
    <Father :data='data'/>  <Child v-bind="$attrs"/>  <Son/>

<!-- provide()/inject()(祖←→孙) -->
    import {provide/inject} from 'vue'
    provide('name', data)  // 父组件provide提供数据
    let name = inject('name', default)  // 孙组件, default:默认值(子组件inject使用数据)

<!-- mitt(全能) -->
    npm i mitt

    src/utils/emitter.ts:
        import mitt from 'mitt'
        export default mitt()

    Child.vue:
        import emitter from 'path'
        emitter.on('event', (value)=>{})  // 绑定事件
        onUnmounted(()=>{emitter.off('event')})  // 解绑事件

    Child1.vue:
        emitter.emit('event', data)  // 触发事件

    emitter.all  // 获取所有事件
    emitter.all.clear()  // 清除所有事件

<!-- 插槽(父子结构通信) -->
    <默认插槽>
        父组件：
            <Child>
                <div>html结构、数据、样式</div>
            </Child>
        子组件：
            <slot>插槽默认内容</slot>  // 插槽展示位置

    <具名插槽: v-slot:/#简写>
        父组件：
            <Child>
                <template v-slot:center>
                    <div>html结构</div>
                </template>
                <template #center>
                    <div>html结构</div>
                </template>
            </Child>

        子组件：
            <slot name="center">插槽默认内容</slot>

    <作用域插槽>
        父组件：
            <Child>
                <template #="data">
                    <div>{{data}}</div>
                </template>
            </Child>

        子组件：
            <slot :data="data"></slot>  //回传数据

#### v-model(父子组件通信)
    <Father v-model='data'></Father>  // 原型
    <Father
        :modelValue='data'   // props
        @update:modelValue='data=$event'  // 自定义事件名($event:触发自定义事件回传的值)
    ></Father>  // v-model底层原理

    <Child>:
        <input type='text'
            :value=modelValue  // 接收props
            @input="emit('update:modelValue', (<HTMLInputElement>$event.target).value)"  // 触发自定义事件
        >
        defineProps(['modelValue'])
        let emit = defineEmits(['update:modelValue'])
    </Child>

    同时传多个model:
        <Father v-model:username='data' v-model:pasworrd='pas'></Father>  // 定义modelValue名称

<!-- 
    <input标签>:
        <input type="text" v-model="data">  // 原型
        <input type="text" :value='data' @input="data=$event.target.value">  // v-model底层原理
-->

## 数据代理原理
    原生js Object.defineProperty()、Reflect.definePropety():
        Object.defineProperty(obj, 'name'){
            value: '杨超越',  // 设置初始值,默认值undefine
            enumerable: true,  // 控制属性是否可以枚举，默认值false
            writable: true,  // 控制属性是否可以修改，默认值false
            configurable: true,  // 控制属性是否可以被删除，默认值false
            get(){},  // 读取时触发
            set(value){}  // 修改时触发
        }  // 没有返回值,不方便捕获错误

        Reflect.definePropety(obj, 'name', {})  // 反射对象,有返回值,方便捕获错误

    es6 Proxy(代理): 
        const p = new Proxy(person, {
            get(target, propName){return Reflect.get(target, propName)},  // 读取属性时触发
            set(target, propName, value){return Reflect.set(target, propName, value)},  // 添加、修改属性时触发
            deleteProperty(target, propName){return Reflect.deleteProperty(target, propName, value)}  // 删除属性时触发
        })

    通过Proxy(代理): 拦截对象中任意属性的变化。
    通过Reflect(反射)：对被代理对象属性进行操作。

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

## 项目应用
    菜单联动、轮播图、分页器、放大镜、面包屑、登录、注册、日历

## 样式
    深度选择器
        原生CSS  >>> .class
        less  /deep/ .class
        scss  ::v-deep .class

    封装的过渡与动画
        元素进入的样式
        Vue3: .v-enter-from
        .v-enter-active：进入过程
        .v-enter-to：进入的终点

        元素离开的样式
        .v-leave-from
        .v-leave-active：离开过程
        .v-leave-to：离开的终点

        2.使用<transition>包裹要过渡的元素，并配置name属性：
            <transition-group name="hello" appear>
                <h1 v-show="!isShow" key="1">你好啊！<h1>
                <h1 v-show="!isShow" key="2">你好啊！<h1>
            </transition-group>

        备注：若有多个元素需要过渡，则需要使用：<transition-group>,且每个元素都要指定key值