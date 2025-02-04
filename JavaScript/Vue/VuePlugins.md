## element Plus
    pnpm i element-plus

    pnpm install @element-plus/icons-vue  // icon图标
        import { Search } from '@element-plus/icons-vue';










    

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

## ECharts
    import * as echarts from 'echarts';

    <div class="charts" ref="charts"></div>
    mounted(){
        // 初始化实例
        const lineCharts = echarts.init(this.$refs.charts)
        // 配置对象
        lineCharts.setOption({
            title: {
                text: '',  // 标题
                subtext: '',  // 子标题
                left: 'center',  // 位置
            }
            <!-- 图表配置 -->
            grid: {
                top: 0,
                right: 0,
                bottom: 0,
                left: 0,
                width: 0,
                height: 0
            },
            // x轴配置
            xAxis: {
                data: [],  // 数据
                // show: false,
                // type: 'category'  // 类目轴
            },
            // y轴配置
            yAxis: {
                // show: false,
                // 是否显示y轴轴线
                axisLine: {
                    show: true
                },
                // 是否显示y轴刻度
                axisTick: {
                    show: true
                }
            },
            // 系列的设置： 绘制图表类型、数据展示
            series: [
                {
                    type: 'line',
                    data: [50, 65, 35, 99, 33, 66, 40, 75, 20, 82],
                    // 拐点样式
                    itemStyle: {
                        opacity: 0
                    },
                    // 线条样式
                    lineStyle: {
                        color: 'pink'
                    },
                    // 填充颜色
                    areaStyle: {
                        color: {
                            type: 'linear',
                            x: 0,
                            y: 0,
                            x2: 0,
                            y2: 1,
                            colorStops: [{
                                offset: 0, color: 'pink' // 0% 处的颜色
                            }, {
                                offset: 1, color: 'white' // 100% 处的颜色
                            }],
                            global: false // 缺省为 false
                        }
                    },
                    // 平滑曲线
                    smooth: true
                },
                {
                    type: 'bar',
                    data: [50, 65, 35, 99, 33, 66, 40, 75, 20, 82],
                    color: 'cyan'
                },
                {
                    name: '饼状图',
                    type: 'pie',
                    data: [
                        {name: '衣服', value: 10},
                        {name: '直播', value: 20},
                        {name: '游戏', value: 30},
                        {name: '电影', value: 40}
                    ],
                    width: 250,
                    height: 250,
                    radius: 50,
                    left: 700,
                }
            ],
            // 提示组件
            tooltip: {},
            // 切换组件
            legend: {
                data: ['柱状图', '折线图', '饼状图']
            },
            // 工具栏组件
            toolbox: {
                show: true,
                feature: {
                dataZoom: {
                    yAxisIndex: "none"
                },
                dataView: {
                    readOnly: false
                },
                magicType: {
                    type: ["line", "bar"]
                },
                restore: {},
                saveAsImage: {}
                }
            }
        })
    }

## Eslint
    .eslintrc.js:
        module.exports = {
            root: true,
            // 继承其他规则
            extends: [
                "plugin:vue/vue3-essential",  // vue3规则  npm i eslint-plugin-vue -D
                "eslint:recommended",  // eslint官方规则
            ],
            parser: "@babel/eslint-parser",  // 支持最新的ECMAScript标准
            env: {
                browser: true,  // 浏览器全局变量
                node: true,  // nodejs全局变量
                es6: true,  // 启用es6新特性
            },
            // 解析选项
            parserOptions: {
                ecmaVersion: 6, // ES语法版本
                sourceType: "module", // ES模块化
            },
            // 具体检查规则
            rules: {
                "no-var": 1
            },
            plugins: ["import"],  // 动态导入import
            ignorePatterns: [
                "dist",
                "node_modules"
            ]
        }

## Eslint(Vite)
    module.exports = {
        // 运行环境
        "env": {
            "browser": true,  // 浏览器全局变量
            "es2021": true,  // es2021
            "node": true,
            "jest": true
        },
        // 继承其他规则
        "extends": [
            // 全部规则默认是关闭的，这个配置项开启推荐规则，推荐规则参照文档
            // 比如：函数不能重名、对象不能出现重复key
            "eslint:recommended",  // eslint官方规则
            "plugin:@typescript-eslint/recommended",  // ts语法规则
            "plugin:vue/vue3-essential",  // vue3语法规则
            "plugin:prettier/recommended"
        ],
        // 要为特定类型的文件指定处理器
        "overrides": [
            {
                "env": {
                    "node": true
                },
                "files": [
                    ".eslintrc.{js,cjs}"
                ],
                "parserOptions": {
                    "sourceType": "script"
                }
            }
        ],
        "parser": 'vue-eslint-parser',
        // 指定解析器选项
        "parserOptions": {
            "ecmaVersion": "latest",  // 检验ECMA最新版本
            "parser": "@typescript-eslint/parser",  // ts解析器；Esprima默认解析器、Babel-Eslint babel解析器
            "sourceType": "module"  // 设置为“script”(默认)，或者“module”代码在ECMAScript模块中
        },
        // 第三方插件，需要pnpm安装
        // 该eslint-plugin-前缀可以从插件名称被省略
        "plugins": [
            "@typescript-eslint",
            "vue"
        ],
        /*
            "off" 或 0  ==>  关闭规则
            “warn" 或 1  ==>  打开的规则作为警告（不影响代码执行）
            *“error” 或 2  ==>  规则作为一个错误（代码不能执行，界面报错）
        */
        // 具体检查规则
        "rules": {
            // eslint (https://eslint.bootcss.com/docs/rules/)
            'no-var':'error',  // 要求使用 let 或 const而不是 var 
            'no-multiple-empty-lines': ['warn', {max: 1}],  // 不允许多个空行
            'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
            'no-debugger': process. env.NODE_ENV === 'production' ? 'error': 'off',
            'no-unexpected-multiline':'error',  // 禁止空余的多行
            'no-useless-escape': 'off',  // 禁止不必要的转义字符

            // typeScript （https://typescript-eslint.io/rules）
            '@typescript-eslint/no-unused-vars': 'error', //禁止定义未使用的变量
            '@typescript-eslint/prefer-ts-expect-error': 'error', // K1:1&/) @ts-ignore
            '@typescript-eslint/no-explicit-any':'off',// 禁止使用 any 类型
            '@typescript-eslint/no-non-null-assertion' : 'off',
            '@typescript-eslint/no-namespace': 'off',  // 禁止使用自定义TypeScript模块和
            '@typescript-eslint/semi': 'off',

            // eslint-plugin-vue (https://eslint.vuejs.org/rules/)
            'vue/multi-word-component-names': 'off',  // 要求组件名称始终为“_”链接的单词
            'vue/script-setup-uses-vars': 'error',  // 防止 < script setup > 使用的变量 < templa
            'vue/no-mutating-props': 'off',// 不允许组件 prop的改变
            'vue/attribute-hyphenation': 'off'  // 对模板中的自定义组件强制执行属性命名样式  
        }
    }