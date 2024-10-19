## less-loader
    npm i less-loader

## animate.css 动画库
    npm i anitate.css
    import 'anitate.css'

## 删除文件包插件
    npm i rimraf
    rimraf xxxxnp

## nprogress 进度条
    npm i nprogress

    import nprogress from 'nprogress';  // 引入进度条
    import 'nprogress/nprogress.css';  // 引入进度条样式
    
    nprogress.start();  // 进度条开始
    nprogress.done();  // 进度条结束

## lodash防抖与节流
    npm i lodash

    import _ from 'lodash'  //引入lodash
    import throttle from 'lodash/throttle'  // 引入节流
    import debounce from 'lodash/debounce'  // 引入防抖
    import cloneDeep from 'lodash/cloneDeep'  // 引用lodash的深拷贝

    throttle(()=>{}, 50),  // 防抖

    data1 = cloneDeep(data)  // 深度克隆

    节流： 在规定的时间范围内不会重复触发回调，只有大于这个时间间隔才会触发。(设置cd)
        _.throttle(function(){}, 1000)

    防抖： 前面的所有的触发都被取消，最后一次执行在规定的时间之后才会触发。（回城）
        _.debounce(function(){}, 1000)

## swiper 轮播图
    npm i swiper@5

    main.js
        import 'swiper/css/swiper.min.css'

    <template>
        <div class="swiper-container">
            <div class="swiper-wrapper">
                <div class="swiper-slide"></div>
                <div class="swiper-slide"></div>
                <div class="swiper-slide"></div>
            </div>

            <!-- 如果需要分页器 -->
            <div class="swiper-pagination"></div>

            <!-- 如果需要导航按钮 -->
            <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div>
        </div>
    </template>

    <script>
        import Swiper from 'swiper/js/swiper.min'

        export default {
            mounted() {
                const swiper = new Swiper('.swiper-container', {
                    loop: true, // 循环模式选项

                    autoplay:true,//等同于以下设置

                    // 如果需要分页器
                    pagination: {
                        el: '.swiper-pagination',
                        clickable: true
                    },

                    // 如果需要前进后退按钮
                    navigation: {
                        nextEl: '.swiper-button-next',
                        prevEl: '.swiper-button-prev',
                    }
                })
            }
        };
    </script>

    <style scoped>
        .swiper-container{
            width: 600px;
            height: 400px;
        }
    </style>

## vue-lazyload 图片懒加载(vue2使用 1.3.4版本)
    npm i vue-lazyload@1.3.4

    main.js
        import VueLazyload from 'vue-lazyload'
        Vue.use(VueLazyload, {
            loading: require('@/assets/GIF.gif')  // 懒加载默认图片
        })

    <img v-lazy="img" alt="">

## moment.js/dayjs  生成日期对象
    npm i moment

    import moment from 'moment'

    moment().format('YYYY年MM月DD日, hh:mm:ss a')  // 2023年06月16日, 02:49:16 am

    moment().day(0).format('YYYY-MM-DD')  // 获取现在的周数
    
    moment().startOf('month').format('YYYY-MM-DD')  // 获取开始时间

    moment().endOf('year').format('YYYY-MM-DD')  // 获取结束时间

## qrcode 二维码
    npm i qrcode.js

    import QRCode from 'qrcode';
    QRCode.toDataURL('I love you!')
    .then(url => {
        console.log(url)
        this.img = url
    })
    .catch(err => {
        console.error(err)
    })

    <img :src="img" alt="">

## vee-validate 表单验证
    npm i vee-validate@2  //vue2.0使用2 or 3 版本

    import VeeValidate from 'vee-validate';
    import zh_CN from 'vee-validate/dist/locale/zh_CN';  // 显示中文信息
    Vue.use(VeeValidate);

    // 校验规则
    VeeValidate.Validator.localize('zh_CN', {
    messages: {
        ...zh_CN.messages,
        is: (field) => `${field}必须与密码相同`,  //修改内置规则的 message，让确认密码与密码相同
    },
    attributes: { //给校验的 field 属性名映射中文名称
        phone: '手机号',
        code: '验证码',
        password: '密码',
        password1: '确认密码',
        agree: '协议'
    }
    })

    // 自定义校验规则
    VeeValidate.Validator.extend('agree', {
    validate: (value) => {
        return value;
    },
    getMessage: (field) => field + "必须同意"
    })

    账号<input type="text" v-model="username" name="username" v-validate="{ required: true, regex: /^[a-z][a-z][0-9]{5}$/}" :class="{ invalid: errors.has('username')}">
    <p>
        <span class="error">{{ errors.first('username') }}</span>
    </p>

    const success = await this.$validator.validateAll();  // 全部表单验证通过才可以注册
    if(success){}

