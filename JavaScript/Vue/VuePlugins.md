## Qrcode 生成二维码
    npm i qrcode.js

    import QRCode from 'qrcode';
    let img =
    QRCode.toDataURL('I love you!')
    .then(url => {
        console.log(url)
        this.img = url
    })
    .catch(err => {
        console.error(err)
    })

    <img :src="img" alt="">

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

## vue-lazyload 图片懒加载(vue2使用 1.3.4版本)
    npm i vue-lazyload@1.3.4

    main.js
        import VueLazyload from 'vue-lazyload'
        Vue.use(VueLazyload, {
            loading: require('@/assets/GIF.gif')  // 懒加载默认图片
        })

    <img v-lazy="img" alt="">