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
                        "  <div>",
                        "",
                        "  </div>",
                        "</template>",
                        "",
                        "<script setup lang='ts'>",
                        "",
                        "</script>",
                        "",
                        "<style scoped lang='scss'>",
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
    js语法检测

## Error Lens
    ESLint报错

## prettier(Js代码格式化)

## stylelint(csslint工具，格式化css代码)

<!-- Vue -->
## Vue-Official
    为 Vue 单文件组件提供了开箱即用的格式化功能

<!-- git -->
## GitHub Copilot
    Ai 代码预生成

## GitHub Copilot Chat
    Ai 聊天框

## GitHub Pull Requests
    请求推送权限

<!-- 扩展 -->
## Live Sass Compiler 
<!-- 将Sass转化为Css -->
    配置：
    // 定制样式
    "liveSassCompile.settings.formats":[
        // This is Default.
        {
            "format": "expanded",  //可定制的出口css样式（expanded展开格式、compact紧凑格式、compressed压缩格式、nested嵌套格式）
            "extensionName": ".css",
            "savePath": null  //为null，表示当前目录
        }
    ],
    // 排除目录
    "liveSassCompile.settings.excludeList": [
        "/**/node_modules/**",
        "/.vscode/**"
    ],
    //是否添加兼容前缀 例如：-webkit- -moz- ...等
    "liveSassCompile.settings.autoprefix": [
        "> 1%",
        "last 2 versions"
    ]

## 扩展
    ## px to rem & rpx & vw (cssrem)
        屏幕适配
