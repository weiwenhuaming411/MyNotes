### Vite
    npm create vue@latest  // 通过vite创建Vue3项目
    npm i  // 安装项目依赖

    npm run dev

## Vite(pnpm)
    pnpm create vite  // 项目初始化
    pnpm i  // 下载依赖

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
