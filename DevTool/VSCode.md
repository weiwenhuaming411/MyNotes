运行脚本文件
        以管理员权限打开windows powershell，输入set-ExecutionPolicy RemoteSigned，选择y或者a即可。

## VSCode配置:
        Explorer: Compact Folders  // 控制文件夹是否紧凑显示
        Workbench › Editor: Enable Preview  // 把替换窗口设置为打开新窗口
        Workbench: External Browser  // 配置浏览器

    <!-- 代码片段 -->
        文件→首选项→配置用户代码片段
            {
                "Print to console": {
                    "scope": "",
                    "prefix": "vue3",
                    "body": [
                        "<template>",
                        "",
                        "</template>",
                        "",
                        "<script setup lang='ts'>",
                        "",
                        "</script>",
                        "",
                        "<style scoped>",
                        "",
                        "</style>"
                    ],
                    "description": "Log output to console"
                }
            }

<!-- 基本配置 -->
## Auto Rename Tab
    自动闭合标签

## Chinese
    中文

## Live Server
    保存自动刷新浏览器

## Open in browser
    打开默认/指定浏览器

## ESLint
    js语法检测高亮


<!-- Vue -->
## Vue-Official


<!-- 样式 -->
## Live Sass Compiler
    sass转css
        扩展设置: 配置sass


<!-- 扩展 -->
## 扩展
    ## vsc-nvm
        nvm自动切换对应版本
        .nvmrc:
            v18.18.0

    ## Vscode-element-helper
        ElementUI组件标签提示

    ## Prettier - Code formatter
        代码格式化

    ## px to rem & rpx & vw (cssrem)
        屏幕适配
