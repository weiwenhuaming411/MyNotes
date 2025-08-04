## vite.config.js
    // 配置代理服务器
    server: {
        proxy: {
            '/api': {
                target: 'http://jsonplaceholder.typicode.com',
                changeOrigin: true,
                rewrite: (path) => path.replace(/^\/api/, '')  // 重写路径
            }
        }
    },
    // src别名配置
    resolve: {
        alias: {
        '@': fileURLToPath(new URL('./src', import.meta.url))
        },
    },

## 
    ### eslint(保证代码质量)
        pnpm i eslint -D  // 下载语法检测工具
            npx eslint --init  // 生成配置文件

        ##vue3环境代码校验插件
            pnpm i -D eslint-plugin-import eslint-plugin-vue eslint-plugin-prettier eslint-plugin-node @babel/eslint-parser

            配置rules:
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
                '@typescript-eslint / no - non - null - assertion' : 'off',
                '@typescript-eslint/no-namespace': 'off',  // 禁止使用自定义TypeScript模块和
                '@typescript-eslint/semi': 'off',

                // eslint-plugin-vue (https://eslint.vuejs.org/rules/)
                'vue/multi-word-component-names': 'off',  // 要求组件名称始终为“_”链接的单词
                'vue / script - setup - uses - vars': 'error',  // 防止 < script setup > 使用的变量 < templa
                'vue / no - mutating - props': 'off',// 不允许组件 prop的改变
                'vue / attribute - hyphenation': 'off'  // 对模板中的自定义组件强制执行属性命名样式  
            }

            生成.eslintignore忽略文件:
                dist
                node_modules

            package.json新增两个运行脚本
                "scripts": {
                    "linx": "eslint src",
                    "fix": "eslint src --fix"
                }

    ### 配置prettier(保证代码美观)
        pnpm i -D prettier eslint-plugin-prettier eslint-config-prettier

        .prettierrc.json:
            {
                "singleQuote": true,
                "semi": false,
                "bracketSpacing": true,
                "htmlWhitespaceSensitivity": "ignore",
                "endOfLine": "auto",
                "trailingComma": "all",
                "tabWidth": 2
            }
        
        .prettierignore忽略文件:
            /dist/* 
            /html/*
            .local
            /node_modules/**
            **/*.svg
            **/*.sh 
            /public/*

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
