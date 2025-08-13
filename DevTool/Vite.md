## 初始化项目
    pnpm create vite
        >>> name
        >>> Vue
        >>> Ts

## vite.config.js
<!-- // 配置代理服务器 -->
    server: {
        proxy: {
            '/api': {
                target: 'http://jsonplaceholder.typicode.com',
                changeOrigin: true,
                rewrite: (path) => path.replace(/^\/api/, '')  // 重写路径
            }
        }
    },

<!-- // src别名配置 -->
    import path from 'path'
    resolve: {
        alias: {
        '@': path.resolve("./src")  // 相对路径别名配置
        },
    },

    <!-- tsconfig.app.json: -->
        "baseUrl": "./",
        // 用于设置模块名到基于baseUrl的路径映射
        "paths": {
            "@/*": ["src/*"]
        },

## eslint(保证代码质量)
    pnpm add eslint -D  // 下载语法检测工具 pnpm create @eslint/config@latest
    npx eslint --init  // 生成配置文件
        >>> Js
        >>> To check syntax and find problems  // 检查语法并找出错误
        >>> Js 模块
        >>> Vue
        >>> Yes
        >>> Browser
        >>> Js
        >>> Yes
        >>> pnpm

    <!-- 检测语法插件 -->
        eslint
        eslint-plugin-vue  // vue插件,解析vue文件,校验vue语法
        typescript-eslint  // Ts包(包含@typescript-eslint/parser解析器和@typescript-eslint/eslint-plugin规则)

    <!-- vue3环境代码校验插件 -->
        pnpm i -D
        @eslint/js  // 提供一些基础的 JavaScript 规则
        globals  // 定义全局变量,避免因未定义变量而导致的错误提示

<!-- 
    eslint-plugin-node  // node.js插件，提供额外规则，校验node.js环境的代码问题
    eslint-plugin-import  // import插件，校验模块导入(import) 和导出(export) 的路径和名称
    @babel/eslint-parser  // 让ESLint 能够解析和检查由Babel 转换过的JavaScript 代码 
-->

    <!-- package.json新增运行脚本 -->
        "scripts": {
            "lint": "eslint . --fix"  // 对不符合的语法进行纠正
        }

#### eslint.config.ts
    import { globals } from 'globals'  // 引入全局变量
    import tseslint  from "typescript-eslint"  // 引入ts相关包
    import { defineConfig, globalIgnores } from "eslint/config";
    export default defineConfig([
        {
            name: '',  // 配置对象名称，方便错误消息提示
            basePath: '',  // 配置基础路径
            files: [],  // 指定校验哪些文件
            ignores: [],  // 指定不校验哪些文件
            plugins: {},  // 应用哪些插件
            extends: [  // 继承规则
                "plugin:prettier/recommended",  // 继承prettier规则
            ],
            languageOptions: {  // 语言配置
                ecmaVersion: 'latest',  // ECMA 最新版
                sourceType: 'module',  //  JS 源代码的类型。"script"/"module"/"commonjs"
                globals: globals.browser,  // 添加全局作用域对象（browser浏览器）
                parser: '',  // 指定解析器
                parserOptions: {}  // 指定解析器配置
            },
            rules: {}  // 规则

            linterOptions: {  // 包含与代码检查过程相关的设置的对象。
                noInlineConfig: true/false,  // 布尔值，指示是否允许内联配置。
                reportUnusedDisableDirectives: 'warn/off',  // 指示是否报告未使用的禁用和启用指令。（默认值："warn"）
                reportUnusedInlineConfigs: 'off/warn'  // 指示是否报告未使用的内联配置。（默认："off"）
            }
            processor:  // 指示插件内处理器名称的字符串（即 "pluginName/processorName"）
            settings - 一个包含名称-值对信息的对象，所有规则都应使用这些信息。
        }
        tseslint.configs.recommended,  // 应用ts推荐规则
        globalIgnores(["dist", "node_modules"]),  // 配置全局ESLint忽略文件
    ])

<!-- 
    // 继承规则
    "extends": [
        // 全部规则默认是关闭的，这个配置项开启推荐规则，推荐规则参照文档
        "eslint:recommended",  // eslint推荐规则
        "plugin:vue/vue3-essential",  // vue3语法规则
    ],
    // 指定解析器 Esprima(默认解析器)、Babel-ESLint(babel解析器Js语法)、@typescript-eslint/parser(ts解析器)
    "parser": '@typescript-eslint/parser',
    // 指定解析器选项(优先级低于parser配置)
    "parserOptions": {
        "ecmaVersion": "latest",  // 设置ECMAScript为最新版本
        "sourceType": "module",  // 设置为“script”(默认)，或者“module”
        "parser": "@typescript-eslint/parser",  // ts解析器；Esprima默认解析器、Babel-Eslint(babel解析器)
    }, 
-->

<!-- 
    "rules": {
        'no-var':'error',  // 要求使用 let 或 const而不是 var

        // eslint (https://eslint.bootcss.com/docs/rules/)
        "no-console": "warn",  // 不允许console.log
        'no-multiple-empty-lines': ['warn', {max: 1}],  // 不允许多个空行
        'no-debugger': 'error',  // 不允许断点

        // typeScript （https://typescript-eslint.io/rules）
        '@typescript-eslint/no-unused-vars': 'error',  //禁止定义未使用的变量
        '@typescript-eslint/no-explicit-any':'off',  // 禁止使用 any 类型

        // eslint-plugin-vue (https://eslint.vuejs.org/rules/)
    }
-->                 

## 配置prettier(保证代码美观)格式化工具配置
    
    pnpm i -D 
        prettier 
            eslint-plugin-prettier  // eslint插件
        eslint-config-prettier  // 适配esllint,避免与eslint冲突

    .prettierrc.json:
        {
            "singleQuote": true,  // 统一单引号
            "semi": false,  // 取消分号
            "bracketSpacing": true,
            "htmlWhitespaceSensitivity": "ignore",
            "endOfLine": "auto",
            "trailingComma": "all",
            "tabWidth": 2  // 缩进占2个位置
        }
    
    .prettierignore忽略文件:
        所在的目录中存在 .gitignore 文件，那么它将遵循该文件中指定的规则。
        dist
        node_modules
        .local

    <!-- 运行脚本 -->
    "scripts": {
        "format": "prettier --write .",
    }

## 配置stylelint(csslint工具，格式化css代码)
    https://stylelint.bootcss.com/
    pnpm add sass
        sass-loader
        stylelint
        postcss
        postcss-scss
        postcss-html
        stylelint-config-prettier  // 适配prettier,避免冲突
        stylelint-config-recess-order
        stylelint-config-recommended-scss
        stylelint-config-standard
        stylelint-config-standard-vue
        stylelint-scss
        stylelint-order
        stylelint-config-standard-scss -D

    .stylelintignore忽略文件
        /node_modules/*
        /dist/*
        /html/*
        /public/*

    <!-- 运行脚本 -->
    "scripts": {
        "lint:eslint": "eslint src/**/*.{ts,vue} --cache --fix",
        "lint:style": "stylelint src/**/*.{css,scss,vue} --cache --fix"
    }

## 配置husky(提交github代码前执行格式化代码)
    pnpm i husky -D
    npx husky-init  // 生成.husky目录(git钩子)
        pnpm run format  // 添加此代码

## 配置commitlint(规范commit信息)
    pnpm add @commitlint/config-conventional @commitlint/cli -D

    添加commitlint.config.cjs文件：
        extends: ['@commitlint/config-conventional'],
        rules: {
            'type-enum': [
                2,
                "always",
                [
                    'feat',  // 新特性、新功能
                    'fix',  // 修改bug
                    'docs',  // 文档修改
                    'style',  // 代码格式修改，注意不是css修改
                    'refactor',  // 代码重构
                    'perf',  // 优化相关，比如提升性能
                    'test',  // 测试用例修改
                    'chore',  // 其他修改，比如改变构建流程、或者增加依赖库、工具等
                    'revert',  // 回滚到上一个版本
                    'build',  // 编译相关的修改，例如发布版本、对项目构建或者依赖的改动
                ]
            ],
            'type-case': [0],
            'type-empty': [0],
            'scope-empty': [0],
            'scope-case': [0],
            'subject-full-stop': [0, 'never'],
            'subject-case': [0, 'never'],
            'header-max-length': [0, 'always', 72]
        }

    <!-- 运行脚本 -->
    "scripts": {
        "commitlint": "commitlint --config commitlint.config.cjs -e -v"
    }

    npx husky add .husky/commit-msg  // 生成commit-msg文件(git钩子)
        pnpm commitlint  // 添加此代码

    <!-- 提交信息规范： -->
        commit -m "fix: xxx"

## 强制使用pnpm包管理工具
    scripts/preinstall.js: (npm钩子)
        if(!/pnpm/.test(process.env.npm_execpath || '')) {
            console.warn(
                `\u001b[33mThis repository must using pnpm as the package manager ` + 
                `for script to work properly.\u001b[39m\n`,
            )
            process.exit(1)
        }

    <!-- 运行脚本 -->
    "scripts": {
        "preinstall": "node ./scripts/preinstall.js"
    }