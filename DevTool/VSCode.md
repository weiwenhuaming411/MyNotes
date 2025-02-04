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
    js语法检测高亮

<!-- Vue -->
## Vue-Official

## Element UI Snippets
    标签补全

<!-- 扩展 -->
## 扩展
    ## px to rem & rpx & vw (cssrem)
        屏幕适配
