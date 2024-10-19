## CSS
    拾色器
        https://www.runoob.com/tags/html-colorpicker.html  RGB
        https://www.runoob.com/html/html-colornames.html  颜色名
        https://www.runoob.com/tags/colors-mixer.html  颜色渐变

    优先级
        内联样式 > 内部样式 > 外部样式 > 默认样式

    初始化配置
        *{
            margin: 0;
            padding: 0;
        }
        ul, ol, li{
            list-style: none;
        }
        a, a:active, a:hover, a:link{
            text-decoration: none;
        }
        input, button, select, textarea{
            outline: none;
        }
        img{
            width: 100%;
            height: 100%;
            display: block;
        }

### css函数：
    https://www.runoob.com/cssref/css-functions.html

    calc()  // 函数用于动态计算长度值
        width: calc(100% - 100px);

    rgb()  // 使用红(R)、绿(G)、蓝(B)三个颜色的叠加来生成各式各样的颜色
        background-color: rgba(255, 0, 0,);
    rgba()  // 使用红(R)、绿(G)、蓝(B)、透明度(A)的叠加来生成各式各样的颜色
        background-color:rgba(255, 0, 0, 0.3);
    hsl(hue, saturation, lightness)  // 使用色相、饱和度、亮度来定义颜色
        色相（H）是色彩的基本属性，就是平常所说的颜色名称，如红色、黄色等
        饱和度（S）是指色彩的纯度，越高色彩越纯，低则逐渐变灰，取 0-100% 的数值
        亮度（L）取 0-100%，增加亮度，颜色会向白色变化；减少亮度，颜色会向黑色变化
        hue - 色相	定义色相 (0 到 360) - 0 (或 360) 为红色, 120 为绿色, 240 为蓝色
        saturation - 饱和度	定义饱和度; 0% 为灰色， 100% 全色
        lightness - 亮度	定义亮度 0% 为暗, 50% 为普通, 100% 为白
        background-color:hsl(120,100%,50%);
    hsla(hue, saturation, lightness, alpha)  // 使用色相、饱和度、亮度、透明度来定义颜色
        透明度（A） 取值 0~1 之间， 代表透明度
        alpha - 透明度	定义透明度 0（透完全明） ~ 1（完全不透明）

    max()  // 从一个逗号分隔的表达式列表中选择最大的值作为属性的值
        width: max(50%, 300px);
    min()  // 从一个逗号分隔的表达式列表中选择最小的值作为属性的值
        width: min(50%, 300px);

    minmax()  // 定义了一个长宽范围的闭区间(grid)
        函数定义了一个长宽范围的闭区间， 它与 CSS 网格布局一起使用
        grid-template-columns: minmax(max-content, 300px) minmax(200px, 1fr) 150px;
        length	非负长度
        percentage	非负百分比
        flex  1fr
        max-content  表示网格的轨道长度自适应内容最大的那个单元格
        min-content  表示网格的轨道长度自适应内容最小的那个单元格
        auto  作为最大值，等同于 max-content。作为最小值，它代表占据网格轨道的网格项目的最小尺寸的最大值（如同min-width/min-height所指定的)）

    attr()  // 返回元素的属性的属性值
        div:after {
            content: " (" attr(id) ")";
        }

    counter(countername, counterstyle)  // 设置计数器
        countername     必需。 计数器的名称（与 counter-reset 和 counter-increment 属性使用的名称相同）
        counterstyle    可选的。 计数器的样式（可以是 CSS list-style-type 属性值）
        例: body {
            counter-reset: section;           /* 重置计数器成0 */
        }
        h3:before {
            counter-increment: section;      /* 增加计数器值 */
            content: counter(section) ": "; /* 显示计数器 */
        }

    var()  // 用于插入自定义的属性值
        :root {
            --main-bg-color: coral;
        }
        #div1 {
            background-color: var(--main-bg-color, value);
                value  备用值
        }

    cubic-bezier()  // 定义了一个贝塞尔曲线(Cubic Bezier)
        cubic-bezier() 可用于 animation-timing-function 和 transition-timing-function 属性
        cubic-bezier(x1,y1,x2,y2)
            x1,y1,x2,y2  必需。数字值，x1 和 x2 需要是 0 到 1 的数字

    repeat()  // 表示轨道列表的重复片段
        该函数可以用于CSS Grid属性中grid-template-columns和grid-template-rows
        grid-template-columns: repeat(2, 50px 1fr) 100px;
        length  正整数长度
        percentage  非负百分比
        flex  1fr
        max-content	 代表占据网格轨道的网格项目所分配的最大内容区域的最大值
        min-content	 代表占据网格轨道的网格项目所分配的最小内容区域的最小值
        auto  作为最大值，等同于 max-content。作为最小值，它代表占据网格轨道的网格项目的最小尺寸的最大值（如同min-width/min-height所指定的)）
        auto-fill  如果网格容器在相关轴上具有确定的大小或最大大小，则重复次数是最大可能的正整数，不会导致网格溢出其网格容器。如果定义了，将每个轨道视为其最大轨道尺寸大小函数 ( grid-template-rows 或 grid-template-columns用于定义的每个独立值。 否则，作为最小轨道尺寸函数，将网格间隙加入计算。如果重复次数过多，那么重复值是 1 。否则，如果网格容器在相关轴上具有确定的最小尺寸，重复次数是满足该最低要求的可能的最小正整数。否则，指定的轨道列表仅重复一次。
        auto-fit	行为与 auto-fill 相同，除了放置网格项目后，所有空的重复轨道都将折叠。空轨道是指没有流入网格或跨越网格的网格项目。（如果所有轨道都为空，则可能导致所有轨道被折叠。） 折叠的轨道被视为具有单个固定轨道大小函数为 0px，两侧的槽都折叠了。 为了找到自动重复的轨道数，用户代理将轨道大小限制为用户代理指定的值（例如 1px），以避免被零除。

### css单位
    相对长度
        相对长度单位指定了一个长度相对于另一个长度的属性。对于不同的设备相对长度更适用

        em	相对长度单位。一般浏览器字体大小默认为16px，则2em == 32px
        rem  作用于非根元素时，相对于根元素字体大小；作用于根元素字体大小时，相对于其出初始字体大小
        vw	Viewport Width，视窗宽度，1vw=视窗宽度的1%
        vh	Viewport Height，视窗高度，1vh=视窗高度的1%
        vmin  vw和vh中较小的那个
        vmax  vw和vh中较大的那个
        %

        ex	依赖于英文字母小 x 的高度
        ch	数字 0 的宽度

    绝对长度
        绝对长度单位是一个固定的值，它反应一个真实的物理尺寸。绝对长度单位视输出介质而定，不依赖于环境（显示器、分辨率、操作系统等）

        px  像素 (1px = 1/96th of 1in)

        pt	point，大约1/72英寸； (1pt = 1/72in)
        pc	pica，大约 12pt，1/6英寸； (1pc = 12 pt)
        cm	厘米
        mm	毫米
        in	英寸 (1in = 96px = 2.54cm)

### css选择器
    !important
    style=''   1000
    id:  #HOME  100
    class|伪类|属性:  .home||[name=home]  10
    div|伪元素:  div  1
    *

    * {}  // 通配选择器
    p {}  // 元素选择器
    .header {}  // 类选择器
    #HEADER {}  // id选择器
    div,p {}  // 选择所有 <div> 元素和 <p> 元素
    div p {}  // 后代选择器(空格分隔)
    div > p {}  // 子元素选择器(>号分隔)
    div + p {}  // 相邻兄弟选择器(+分隔)紧跟在 <div> 元素之后的第一个 <p> 元素
    div ~ p {}  // 普通兄弟选择器(～分隔)选择div元素之后的每一个p元素

    [name='home']|[name] {}  // 属性选择器
    [title~=flower]  选择标题属性包含单词"flower"的所有元素
    [lang|=en]  选择 lang 属性等于 en，或者以 en- 为开头的所有元素
    [attr^=value]  选择每一个属性的值以"value"开头的元素
    [attr$=value]  选择每一个src属性的值以"value"结尾的元素
    [attr*=value]  选择每一个src属性的值包含子字符串"value"的元素

    :link  选择所有未访问链接
    :visited  选择所有访问过的链接
    :active  选择活动链接
    :hover  选择鼠标在链接上面时


    :before  在元素之前插入内容
    :after  在元素之后插入内容

    
    p:first-child  元素是其父级的第一个子元素(必须是其自身)
    :last-child  元素是其父级的最后一个子元素(必须是其自身)
    :first-of-type  元素是其父级的第一个子元素(同类型第一个)
    :last-of-type  元素是其父级的最后一个子元素(同类型最后一个)
    :nth-child(n)  元素是其父级的第n个子元素
        n:  一个数字: 0, 1, 2
            一个关键字: odd(奇数)even(复数)
            一个公式: 2n+1
    :nth-last-child(n)  元素是其父级的n子元素，倒数
    :nth-of-type(n)  匹配同类型元素中的第n个同级兄弟元素
    :nth-last-of-type(n)  匹配同类型元素中的第n个同级兄弟元素,倒数
    :only-child  元素是其父级的唯一子元素
    :only-of-type  元素是其父级的唯一元素
    div > :not(p)  匹配每个非p元素的元素
    

    :first-letter  选择元素的第一个字母
        font、color、background、margin、padding、border、text-decoration、vertical-align (only if float is 'none')、text-transform、line-height、float、clear、
    :first-line  选择元素的第一行
        font、color、background、word-spacing、letter-spacing、text-decoration、vertical-align、text-transform、line-height、clear
    

    :root	:root	选择文档的根元素
    :lang(it)  选择一个lang属性的起始值="it"的所有元素  lang='item'
    p:empty  匹配该元素没有任何子级的元素（包括文本节点）
    :target  定义跳转至锚连接的样式（包含该锚名称的点击的URL）?
    ::selection  定义元素中被用户选中或处于高亮状态的部分的样式

    input:
        :enabled  定义每一个已启用的输入元素样式
        :disabled  定义每一个禁用的输入元素样式
        :checked  定义每个选中的输入元素样式
        :focus  选择具有焦点的输入元素

        :out-of-range  定义值在指定区间之外的input元素的样式
        :in-range  定义值在指定区间之内的input元素

        :read-write  用于匹配可读及可写的元素(即没有 "readonly" 属性的input)
        :read-only  用于匹配设置 "readonly"（只读） 属性的元素

        :optional  用于匹配可选的输入元素
        :required  用于匹配设置了 "required" 属性的元素(必填)

        :valid  用于匹配输入值为合法的元素
        :invalid  用于匹配输入值为非法的元素

### css2属性
    @charset  属性指定样式文件(.css 后缀)中使用的字符编码，且只能在 CSS 文件中使用。
        @charset "UTF-8";

    @import url|string list-of-mediaqueries;  // 引入外部样式资源
        list-of-mediaqueries  媒体查询条件列表，设置URL引入的CSS规则在什么条件下应用

        @import 'custom.css';
        @import url("chrome://communicator/skin/");

        @import url("fineprint.css") print;
        @import url("bluish.css") projection, tv;
        
        @import "common.css" screen, projection;
        @import url('landscape.css') screen and (orientation:landscape);

    <!-- 常用属性 -->
        width  设置元素的宽度
        max-width  设置元素的最大宽度
        min-width  设置元素的最小宽度
        height  设置元素的高度
        max-height  设置元素的最大高度
        min-height  设置元素的最小高度

        margin  // 外边距
        padding  // 内边距

        z-index: 1;  // 调整显示层级

        opacity: 0.5;  // 透明度

        float: left|right;  // 浮动

        clear: none|left|right|both;  // 清除浮动
            none	默认值。允许浮动元素出现在两侧
            left	在左侧不允许浮动元素
            right	在右侧不允许浮动元素
            both	在左右两侧均不允许浮动元素

        vertical-align: 1px;  // 元素的垂直对齐方式(调整基线)
            baseline  默认。元素放置在父元素的基线上。
            sub  垂直对齐文本的下标
            super  垂直对齐文本的上标
            top  把元素的顶端与行中最高元素的顶端对齐
            text-top  把元素的顶端与父元素字体的顶端对齐
            middle  把此元素放置在父元素的中部
            bottom  使元素及其后代元素的底部与整行的底部对齐
            text-bottom  把元素的底端与父元素字体的底端对齐
            length  将元素升高或降低指定的高度，可以是负数
            %  使用 "line-height" 属性的百分比值来排列此元素。允许使用负值
        
        clip: rect(0, 100px, 100px, 0);  // 裁剪一张绝对定位的图像
            shape  设置元素的形状。唯一合法的形状值是：rect (top, right, bottom, left)

        content: " (" attr(href) ")";  // 插入文本,与 :before 及 :after 伪元素配合使用，来插入内容
            none  空值
            counter  设定计数器
            attr(attribute)  将元素的 attribute 属性以字符串形式返回
            string  设置文本内容
            open-quote  设置前引号
            close-quote  设置后引号
            no-open-quote  移除内容的开始引号
            no-close-quote  移除内容的闭合引号
            url(url)  设置某种媒体（图像，声音，视频等内容）的链接地址

        display: ;  // 设置元素的内部和外部的显示类型
            inline  默认。内联元素
            block  块级元素
            inline-block  行内块元素
            none  此元素不会被显示
            display: contents;

            display: flex;
            display: inline-flex;
            display: grid;
            display: inline-grid;

            list-item  此元素会作为列表显示
            run-in  此元素会根据上下文作为块级元素或内联元素显示
            flow-root  生成一个块级元素盒，其会建立一个新的块级格式化上下文，定义格式化上下文的根元素

            table  此元素会作为块级表格来显示（类似 <table>），表格前后带有换行符
            inline-table  此元素会作为内联表格来显示（类似 <table>），表格前后没有换行符
            table-row-group  此元素会作为一个或多个行的分组来显示（类似 <tbody>）
            table-header-group  此元素会作为一个或多个行的分组来显示（类似 <thead>）
            table-footer-group  此元素会作为一个或多个行的分组来显示（类似 <tfoot>）
            table-row  此元素会作为一个表格行显示（类似 <tr>）
            table-column-group  此元素会作为一个或多个列的分组来显示（类似 <colgroup>）
            table-column  此元素会作为一个单元格列显示（类似 <col>
            table-cell  此元素会作为一个表格单元格显示（类似 <td> 和 <th>）
            table-caption  此元素会作为一个表格标题显示（类似 <caption>）         

            /* 两个值的语法格式 */
            display: block flow;
            display: inline flow;
            display: inline flow-root;
            display: block flex;
            display: inline flex;
            display: block grid;
            display: inline grid;
            display: block flow-root;

    <!-- 输入框 -->
        outline: none;  // 去除聚焦边框
        resize: none;  // 禁止文本框重置大小,文本框（textarea）样式
        
        resize: none|both|horizontal|vertical;  // 属性指定一个元素是否是由用户调整大小的
            none  用户无法调整元素的尺寸
            both  用户可调整元素的高度和宽度
            horizontal  用户可调整元素的宽度
            vertical  用户可调整元素的高度

        输入框图标:
            background-image属性和用于定位的background-position

    <!-- background背景 -->
        简写:
        background: color url('') no-repeat right top;
        background: transparent;  //背景透明
        background-color: pink;  // 背景颜色
        background-repeat: center|no-repeat|repeat-x|repeat-y;  // 平铺方式
        background-position: right top;  // 定位
        background-attachment  // 背景图像是否固定或者随着页面的其余部分滚动

        background-blend-mode: normal|multiply|screen|overlay|darken|lighten|color-dodge|saturation|color|luminosity;
            normal  默认值。设置正常的混合模式
            multiply  正片叠底模式
            screen  滤色模式
            overlay  叠加模式
            darken  变暗模式
            lighten  变亮模式
            color-dodge  颜色减淡模式
            saturation  饱和度模式
            color  颜色模式
            luminosity  亮度模式

        css3:
            background-image: url('');  // 背景图片
            background-size: length|percentage|cover|contain;  //背景图片尺寸,12px 12px、100% 100%、完全覆盖、自适应

            background-origin  // 指定背景图像的定位区域
                padding-box	背景图像填充框的相对位置
                border-box	背景图像边界框的相对位置
                content-box	背景图像的相对位置的内容框
            background-clip  // 指定背景图像的绘画区域
                border-box	默认值。背景绘制在边框方框内（剪切成边框方框）
                padding-box	背景绘制在衬距方框内（剪切成衬距方框）
                content-box	背景绘制在内容方框内（剪切成内容方框）

    <!-- 表格 -->
        border-collapse: collapse;  // 设置表格的边框是否被折叠成一个单一的边框或隔开(table)
        border-spacing: 10px 50px;  // 设置表格的边框间距(水平|垂直)
        caption-side: bottom;  // 指定表格标题的位置
            <caption>Table 1.1 Customers</caption>
            top  默认值。把表格标题定位在表格之上
            bottom  把表格标题定位在表格之下
        empty-cells: hide|show;  // 隐藏表中的空单元格的边框和背景

        table-layout: auto|fixed;  // 属性为设置表格布局算法
            auto  默认。内容设定宽度
            fixed  自定义宽度
                <td width="95%">10000000</td>

    <!-- 边框 -->
        border: 1px solid pink;
            border-color: pink;  // 边框颜色
            border-width: 5px;  // 边框宽度
            border-style: none;  // 边框样式
                dotted  点线边框
                dashed  虚线边框
                solid  实线边框
                double  双层边框
                groove  3D沟槽边框
                ridge  3D脊边框
                inset  3D嵌入边框
                outset  3D突出边框
            border-top|right|bottom|left-width|style|color|radius: dotted;  // 单独设置各边

        css3:
            border-radius：0 0 0 0;  //圆角
                border-top-left-radius	定义了左上角的弧度
                border-top-right-radius	定义了右上角的弧度
                border-bottom-right-radius	定义了右下角的弧度
                border-bottom-left-radius	定义了左下角的弧度
            
            border-image: url(border.png) 30 30 round;  // 边界图片
                border-image: source slice width outset repeat;
                    border-image-source: url();  用于指定要用于绘制边框的图像的位置
                    border-image-slice: 10 10;  图像边界向内偏移
                    border-image-width: 30 30;  图像边界的宽度
                    border-image-outset: 20 20;  用于指定在边框外部绘制 border-image-area  的量
                    border-image-repeat  用于设置图像边界是否应重复（repeat）、拉伸（stretch）或铺满（round）

        <!-- outline轮廓 -->
            outline: color style width;  // 位于边框边缘的外围，可起到突出元素的作用
            outline-color: pink;
            outline-style: none;
                dotted	定义点状的轮廓
                dashed	定义虚线轮廓
                solid	定义实线轮廓
                double	定义双线轮廓
                groove	定义 3D 凹槽轮廓
                ridge	定义 3D 凸槽轮廓
                inset	定义 3D 凹边轮廓
                outset	定义 3D 凸边轮廓
            outline-width: medium;  // 默认，规定中等轮廓
                thin  细轮廓
                thick  粗轮廓
                length  10px
            outline-offset: 15px;  // 轮廓与边框边缘的距离

    <!-- 列 -->
        columns: 100px 3;  // 指定列的宽度和数量
            column-width: 100px;  // 指定每列的宽度
            column-count: 3;  // 划分元素列数
        column-gap: 40px;  // 指定列的间隙
        column-rule: 3px outset #ff00ff;  // 指定列之间的规则：宽度，样式和颜色
        column-span: n|all;  // 指定某个元素应该跨越多少列
            num  指定几列
            all  横跨所有列

    <!-- 文本 -->
        text-indent: 32px;  // 规定文本块中首行文本的缩进

        direction: rtl|ltr;  // 设置文本书写方向

        text-align  // 文本的水平对齐方式
            left  把文本排列到左边。默认值
            right  把文本排列到右边
            center  把文本排列到中间
            justify  实现两端对齐文本效果(对最后一行文本无效)

        text-align-last  // 属性规定如何对齐文本的最后一行
            auto  默认值。最后一行被调整，并向左对齐
            left  最后一行向左对齐
            right  最后一行向右对齐
            center  最后一行居中对齐
            justify  最后一行被调整为两端对齐
            start  最后一行在行开头对齐
            end  最后一行在行末尾对齐

        text-decoration: line color style;  // 添加下划线、上划线、删除线等
            none  默认。定义标准的文本
            underline  下划线
            overline  上划线
            line-through  删除线

            text-decoration-style
                solid	默认值。线条将显示为单线
                double	线条将显示为双线
                dotted	线条将显示为点状线
                dashed	线条将显示为虚线
                wavy	线条将显示为波浪线

        text-overflow: clip|ellipsis|string;  // 溢出文本如何展示
            clip  剪切文本
            ellipsis  显示省略符号 ... 来代表被修剪的文本
            string  使用给定的字符串来代表被修剪的文本

        text-transform: none;  // 英文大小写
            none  默认。定义带有小写字母和大写字母的标准的文本
            capitalize  文本中的每个单词以大写字母开头
            uppercase  定义仅有大写字母
            lowercase  定义无大写字母，仅有小写字母

        writing-mode: horizontal-tb|vertical-rl|vertical-lr|sideways-rl|sideways-lr;  // 文本在水平或垂直方向上如何排布
            horizontal-tb  默认
            vertical-rl  垂直方向自右而左的书写方式
            vertical-lr  垂直方向内内容从上到下，水平方向从左到右
            sideways-rl  内容垂直方向从上到下排列
            sideways-lr  内容垂直方向从下到上排列

        //  两端对齐
            label{
                text-align: justify;
                &::after{
                    width: 100%;
                    content: '';
                    display: inline-block;
                }
            }

        // 单行文本溢出隐藏
            display: block;  // 内联元素不生效
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis、clip;  ...展示、剪切

        // webkit内核浏览器专用方法多行溢出隐藏
            overflow: hidden;
            text-overflow: ellipsis;
            display: -webkit-box;
            -webkit-line-clamp: 2;  //行数
            -webkit-box-orient: vertical;  //对齐模式

    <!-- 字体 -->
        color: pink;  // 设置字体颜色
        letter-spacing: 2px;  // 设置字符间距
        word-spacing: 2px;  // 设置单词间距

        font: font-style font-variant font-weight font-size/line-height font-family;  // 字体
            font-style: normal|italic|oblique;  // 规定字体样式
                normal  默认值。浏览器显示一个标准的字体样式
                italic  浏览器会显示一个斜体的字体样式
                oblique  浏览器会显示一个倾斜的字体样式

            font-variant: normal|small-caps;  // 小型大写字母文本
                normal  默认值。浏览器会显示一个标准的字体
                small-caps  浏览器会显示小型大写字母的字体

            font-weight: normal|bold|bolder|lighter|100~900;  // 属性设置文本的粗细
                normal  默认值。定义标准的字符
                bold  定义粗体字符
                bolder  定义更粗的字符
                lighter  定义更细的字符
                100~900  400 等同于 normal，而 700 等同于 bold

            font-size:  // 字体大小
                xx-small
                x-small
                small
                medium  默认值
                large
                x-large
                xx-large

                smaller  把 font-size 设置为比父元素更小的尺寸
                larger  把 font-size 设置为比父元素更大的尺寸

                16px length  把 font-size 设置为一个固定的值
                %  把 font-size 设置为基于父元素的一个百分比值

            line-height  规定字体行高
                normal  默认。设置合理的行间距
                number  设置数字，此数字会与当前的字体尺寸相乘来设置行间距
                length  设置固定的行间距
                %  基于当前字体尺寸的百分比行间距

            font-family: "Times New Roman", Times, serif;  // 属性指定一个元素的字体
                family-name - 指定的系列名称："times"、"courier"、"arial"
                generic-family - 通常字体系列名称："serif"、"sans-serif"、"cursive"、"fantasy"、"monospace"
                caption  定义被标题控件（比如按钮、下拉列表等）使用的字体
                icon  定义被图标标记使用的字体
                menu  定义被下拉列表使用的字体
                message-box  定义被对话框使用的字体
                small-caption  caption 字体的小型版本
                status-bar  定义被窗口状态栏使用的字体

        <!-- 自定义字体 -->
            @font-face {
                font-family: myFirstFont;  // 定义名字
                src: url('Sansation_Light.ttf');  // 路径
            }
            div {font-family:myFirstFont;}

            font-stretch  // 可选。定义如何拉伸字体
                normal  默认
                condensed
                ultra-condensed
                extra-condensed
                semi-condensed
                expanded
                semi-expanded
                extra-expanded
                ultra-expanded

    <!-- cursor光标 -->
        cursor: pointer;  // 光标呈现为一只手
            url()  指定光标url
            default  默认(箭头)
            auto  默认
            pointer  光标呈现为一只手
            not-allowed  设置一个禁用的图片

            move  此光标指示某对象可被移动
            crosshair  光标呈现为十字线
            text  此光标指示文本
            wait  此光标指示程序正忙（通常是一只表或沙漏）
            help  此光标指示可用的帮助（通常是一个问号或一个气球）
            progress 此光标指示正在加载

            e-resize	此光标指示矩形框的边缘可被向右（东）移动
            ne-resize	此光标指示矩形框的边缘可被向上及向右移动（北/东）
            nw-resize	此光标指示矩形框的边缘可被向上及向左移动（北/西）
            n-resize	此光标指示矩形框的边缘可被向上（北）移动
            se-resize	此光标指示矩形框的边缘可被向下及向右移动（南/东）
            sw-resize	此光标指示矩形框的边缘可被向下及向左移动（南/西）
            s-resize	此光标指示矩形框的边缘可被向下移动（南）
            w-resize	此光标指示矩形框的边缘可被向左移动（西）

    <!-- 定位 -->
        position: absolute;  // 绝对定位(父级)
        position: relative;  // 相对定位(自身)
        position：fixed;   // 广告定位
        position: sticky;  // 粘性定位

        top|right|bottom|left
        
        clip: rect(top, right, bottom, left);  // 剪辑一个绝对定位的元素

        clip-path: none;  // 裁剪元素的可显示区域
            https://blog.csdn.net/cwyp18809/article/details/105097282/
            none  默认,没有剪辑
            clip-source  用 URL 表示剪切元素的路径
            basic-shape  将元素裁剪为基本形状：圆形、椭圆形、多边形或插图
            margin-box  使用外边距框作为引用框
            border-box  使用边框作为引用框
            padding-box  使用内边距框作为引用框
            content-box  使用内容框作为引用框
            fill-box  使用对象边界框作为引用框
            stroke-box  使用笔触边界框（stroke bounding box）作为引用框
            view-box  使用最近的 SVG 视口（viewport）作为引用框
        
    <!-- 显示/隐藏 -->
        overflow: hidden;  // 溢出隐藏
            scroll  滚动条
            auto  自适应滚动条
            visible  默认值,不裁剪内容,可能会显示在内容框之外

        overflow-y  // 指定如何处理顶部/底部边缘的内容溢出元素的内容区域
        overflow-x  // 指定如何处理右边/左边边缘的内容溢出元素的内容区域

        visibility: visible;  // 属性指定一个元素是否是可见的
            visible  默认值。元素是可见的
            hidden  元素是不可见的
            collapse  当在表格元素中使用时，此值可删除一行或一列，但是它不会影响表格的布局。被行或列占据的空间会留给其他内容使用。如果此值被用在其他的元素上，会呈现为 "hidden"

    <!-- 列表样式 -->
        list-style: list-style-type, list-style-position, list-style-image;
            list-style-type: none;  //清除列表默认样式
                none  无标记
                disc  默认。标记是实心圆
                circle  标记是空心圆
                square  标记是实心方块
                decimal  标记是数字
                decimal-leading-zero  0开头的数字标记。(01, 02, 03, 等。)
                cjk-ideographic  简单的表意数字(一、二、三)
                lower-alpha	小写英文字母The marker is lower-alpha (a, b, c, d, e, 等。)
                upper-alpha	大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。)
            list-style-position: 
                inside  列表项目标记放置在文本以内，且环绕文本根据标记对齐
                outside  默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不根据标记对齐
            list-style-image: url('');  // 设置列表样式图片
            
            li::marker{content: '😅';}  // 更改li前面的圆点

    <!-- word单词 -->
        单词换行:
            word-break: normal;  //默认换行
            word-break: break-all;  //拆分换行
            word-break: keep-all;  //不拆分换行

        word-spacing: 10px;  // 定义单词间的间隔

        word-wrap: normal|break-word;  // 属性允许长单词可以自动换行
            normal  只在允许的断字点换行（浏览器保持默认处理）
            break-word  在长单词或 URL 地址内部进行换行

    <!-- 换行 -->
        white-space  属性指定元素内的空白(空格/回车)怎样处理
            normal  默认。空白会被浏览器忽略(换行)
            nowrap  不换行
            pre  保留空白符,不换行
            pre-wrap  保留空白符序列,换行
            pre-line  合并空白符序列,换行
            break-spaces  行尾空格换行

                        换行符      空格和制表符    文字换行	行尾空格
            normal      合并        合并            换行        删除
            nowrap      合并        合并            不换行      删除
            pre         保留        保留            不换行      保留
            pre-wrap    保留        保留            换行        挂起
            pre-line    保留        合并            换行        删除
            break-spaces保留        保留            换行        换行

    <!-- img/video -->
        object-fit: fill|contain|cover|scale-down|none;  // 元素的内容应该如何去适应容器的高宽
            fill  默认，不保证保持原有的比例，内容拉伸填充整个内容容器
            contain  宽度铺满,高度自适应
            cover  高度铺满，宽度等比缩放，超出内容剪切
            none  宽高不变，超出内容剪切
            scale-down  大于容器=contain,小于容器=none

        object-position: x y;  // 属性一般与 object-fit一起使用，用来设置元素的位置

### css3属性
    <!-- 阴影 -->
        text-shadow: h-shadow v-shadow blur color;  // 文本阴影
            h-shadow  必需。水平阴影的位置。允许负值
            v-shadow  必需。垂直阴影的位置。允许负值
            blur  可选。模糊的距离
            color  可选。阴影的颜色。参阅 CSS 颜色值

        box-shadow: 10px 10px 5px #888888;  // 盒阴影
                box-shadow: h-shadow v-shadow blur spread color inset;
                    h-shadow  必需的。水平阴影的位置。允许负值
                    v-shadow  必需的。垂直阴影的位置。允许负值
                    blur  可选。模糊距离
                    spread  可选。阴影的大小
                    color  可选。阴影的颜色
                    inset  内侧阴影

        box-sizing: content-box|border-box;  // 怪异盒模型
            content-box	 默认值
            border-box  怪异盒

    <!-- flex弹性盒子 -->
        排列方向:
        flex-flow: flex-direction flex-wrap;  // 设置或检索弹性盒模型对象的子元素排列方式
            flex-direction: row | row-reverse | column | column-reverse;
                row  横向从左到右，默认的排列方式
                row-reverse  反转横向排列
                column  纵向排列
                column-reverse  反转纵向排列
            flex-wrap: nowrap|wrap|wrap-reverse;  // 换行方式
                nowrap  默认值。规定灵活的项目不拆行或不拆列
                wrap  规定灵活的项目在必要的时候拆行或拆列
                wrap-reverse  规定灵活的项目在必要的时候拆行或拆列，但是以相反的顺序

        横轴(列)的对齐方式
        justify-content: flex-start|flex-end|center|space-between|space-around;
            flex-start  默认值。从行首起始位置开始排列
            flex-end  从行尾位置开始排列
            center  居中排列
            space-between  均匀排列每个元素，首个元素放置于起点，末尾元素放置于终点
            space-evenly  均匀排列每个元素，每个元素之间的间隔相等
            space-around  均匀排列每个元素，每个元素周围分配相同的空间

        纵轴(行)的对齐方式
        align-content: stretch|center|flex-start|flex-end|space-between|space-around;
            stretch  默认值
            center  居中
            flex-start  开头对齐
            flex-end  结尾对齐
            space-between  两边对齐
            space-around  两边对齐(空隙)
            space-evenly  均分

        纵轴(子元素)的对齐方式
        align-items: stretch|center|flex-start|flex-end|baseline;
            stretch  默认值。元素被拉伸以适应容器
            center  元素位于容器的中心
            flex-start  元素位于容器的开头
            flex-end  元素位于容器的结尾
            baseline  元素位于容器的基线上

        
        作用于子元素:
        order: number;  // 设置弹性盒模型子元素順序

        align-self: auto|stretch|center|flex-start|flex-end|baseline;  // 覆盖容器的align-items
            auto  默认值
            stretch  元素被拉伸以适应容器
            center  元素位于容器的中心
            flex-start  元素位于容器的开头
            flex-end  元素位于容器的结尾
            baseline  元素位于容器的基线上

        flex: flex-grow flex-shrink flex-basis|auto;  // 设置或检索弹性盒模型对象的子元素如何分配空间
            注意：如果元素不是弹性盒模型对象的子元素，则 flex 属性不起作用
            flex-grow: number;  // 设置或检索弹性盒子的扩展比率
            flex-shrink: number;  // 指定了 flex 元素的收缩规则
            flex-basis  项目的长度。合法值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字
            auto  与 1 1 auto 相同
            none  与 0 0 auto 相同
            flex-basis: number|auto;  // 设置或检索弹性盒伸缩基准值(宽)
            flex-shrink  定义弹性盒子元素的收缩比率
            flex-basis  定义弹性盒子元素的默认基准值

    <!-- 渐变 -->
        线性渐变linear-gradient(默认从上到下)
            background-image: linear-gradient(90deg|to right, color1 30%, color2);
                repeating-linear-gradient(red, yellow 10%, green 20%);  重复线性渐变

        径向渐变radial-gradient
            background-image: radial-gradient(circle圆形/ellipse椭圆形, [farthest at position],color);
                circle圆形
                ellipse椭圆形  默认
                closest-side at 50% 50%  向最近边渐变
                closest-corner at 50% 50%  向最近角渐变
                farthest-side at 50% 50%  向最远边渐变
                farthest-corner at 50% 50%  向最远角渐变 默认

                repeating-radial-gradient(red, yellow 10%, green 20%);  重复径向渐变

        圆锥渐变
            conic-gradient(from 0deg at 50% 50%, color1, color2)  // 定义了一个圆锥渐变
            repeating-conic-gradient()  // 重复的圆锥渐变

    <!-- 过渡 -->
        transition: property duration timing-function delay;
            transition-property  指定CSS属性的name，transition效果
            transition-duration: time;  完成过渡效果需要花费的时间
            transition-timing-function  指定transition效果的转速曲线
                linear	规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
                ease	规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
                ease-in	规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
                ease-out	规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
                ease-in-out	规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
                cubic-bezier(n,n,n,n)	在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。
            transition-delay: time;  何时开始

    <!-- 动画 -->
        // 使用动画
        animation: name duration timing-function delay iteration-count direction fill-mode play-state;
            animation-name: name;  指定要绑定到选择器的关键帧的名称
            animation-duration: time;  动画需要多少秒或毫秒完成
            animation-timing-function  设置动画将如何完成一个周期
                linear  动画从头到尾的速度是相同的
                ease  默认。动画以低速开始，然后加快，在结束前变慢
                ease-in  动画以低速开始
                ease-out  动画以低速结束
                ease-in-out  动画以低速开始和结束
                steps(int,start|end)  指定函数的间隔数, 第二个参数表示动画是从时间段的开头连续还是末尾连续
                    start：表示直接开始
                    end：默认值，表示戛然而止
                cubic-bezier(n,n,n,n)  贝塞尔曲线
            animation-delay: time;  设置动画在启动前的延迟间隔
            animation-iteration-count: n|infinite;  定义动画的播放次数(num|无限)
            animation-direction: normal|reverse|alternate|alternate-reverse;  是否反向播放动画
                normal  默认值
                reverse  反向播放
                alternate  奇数正向播放，偶数反向播放
                alternate-reverse  奇数反向播放，偶数正向播放
            animation-fill-mode: none|forwards|backwards|both;  规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式
                none  默认值。动画在动画执行之前和之后不会应用任何样式到目标元素
                forwards	在动画结束后（由 animation-iteration-count 决定），动画将应用该属性值。
                backwards	动画将应用在 animation-delay 定义期间启动动画的第一次迭代的关键帧中定义的属性值。这些都是 from 关键帧中的值（当 animation-direction 为 "normal" 或 "alternate" 时）或 to 关键帧中的值（当 animation-direction 为 "reverse" 或 "alternate-reverse" 时）。
                both	动画遵循 forwards 和 backwards 的规则。也就是说，动画会在两个方向上扩展动画属性。
            animation-play-state: paused|running;  指定动画是否正在运行或已暂停(paused暂停|running运行)

        // 创建动画
        @keyframes myMove {
            from|0% { 
                top:0px; 
            }
            to|100% { 
                top:200px; 
            }
        }
    
    <!-- 2D/3D旋转 -->
        transform: none|transform-functions;  // 将元素旋转，缩放，移动，倾斜等
            none  定义不进行转换
            平移: px
                translate(x,y)  转换
                translateX(x)  转换，只是用 X 轴的值
                translateY(y)  转换，只是用 Y 轴的值
                translateZ(z)  3D转换，只是用 Z 轴的值
                translate3d(x,y,z)  3D转换
            缩放: number
                scale(x[,y]?)  2D缩放转换
                scaleX(x)  X轴的缩放转换
                scaleY(y)  Y轴的缩放转换
                scaleZ(z)  Z轴的3D缩放转换
                scale3d(x,y,z)  3D缩放转换

            旋转: deg(顺时针)
                rotate(angle)  2D旋转角度
                rotateX(angle)  X轴的3D旋转(水平)
                rotateY(angle)  Y轴的3D旋转(垂直)
                rotateZ(angle)  Z轴的3D旋转(平面)
                rotate3d(x,y,z,angle)  3D旋转
            倾斜: deg()
                skew(x-angle,y-angle)  2D倾斜
                skewX(angle)  X轴的2D倾斜
                skewY(angle)  Y轴的2D倾斜转换

            matrix(n,n,n,n,n,n)	定义 2D 转换，使用六个值的矩阵
            matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)	定义 3D 转换，使用 16 个值的 4x4 矩阵
            
            perspective(n)	为 3D 转换元素定义透视视图

        transform-origin: x-axis y-axis z-axis;  // 更改转换元素的位置
            x-axis：left|center|right|length|%;  定义视图被置于 X 轴的何处
            y-axis: top|center|bottom|length|%;  定义视图被置于 Y 轴的何处
            z-axis: length;  定义视图被置于 Z 轴的何处

        transform-style: flat|preserve-3d;  // 指定嵌套元素是怎样在三维空间中呈现
            flat  表示所有子元素在2D平面呈现
            preserve-3d  表示所有子元素在3D空间中呈现

        perspective: 10px|none;  // 元素距离视图的距离
        perspective-origin: x-axis y-axis;  // 属性定义3D元素所基于的X轴和Y轴。该属性允许您改变 3D 元素的底部位置
            x-axis: left|center|right|length|%  定义该视图在 x 轴上的位置。默认值：50%。
            y-axis: top|center|bottom|length|%  定义该视图在 y 轴上的位置。默认值：50%。

        backface-visibility: visible|hidden;  // 隐藏旋转 div 元素的背面(3D)
            visible  背面是可见的
            hidden  背面是不可见的

    <!-- 网格布局 -->
        display: grid|inline-grid;  // 设置为网格布局

        grid-template: '九宫格';  // 简写属性
            grid-template-rows
            grid-template-columns
            grid-areas

        grid-template-columns: auto auto auto auto|1fr;  // 定义列的数量及宽度(1fr: 一等份)
        grid-template-rows: auto|100px 300px;  // 每行的高度

        grid-gap: 10px 50px;  行和列的间隙
        grid-column-gap:  ;  // 列间隔
        grid-row-gap:  ;  // 行间隔

        item:
            简写
            grid-area: grid-row-start grid-column-start grid-row-end grid-column-end;
                grid-area: 2 / 1 / span 2 / span 3;  第2行开始和第1列开始，横跨2行3列

                网格元素命名
                    定义名字
                        grid-area: header;
                    使用区域
                        grid-template-areas: 'header header header header header header'

            设置网格元素item列的开始与结束
                grid-column: 1 / 3;
                grid-column-start: 1;
                grid-column-end: 3;

            设置网格元素item行的开始与结束
                grid-row: 1 / 3;
                grid-row-start: 1;
                grid-row-end: 3;

        grid: ;  // 简写属性
            grid-template-rows
            grid-template-columns
            grid-template-areas
            grid-auto-rows
            grid-auto-columns
            grid-auto-flow
            
        grid-auto-columns  列的默认大小
            auto  默认值。 列的大小由容器的大小决定
            fit-content()  相当于公式 min(max-content, max(auto, argument))，类似于auto 的计算(即 minmax(auto, max-content))
            max-content  根据列中最大的网格元素设置每列的大小
            min-content  根据列中的最小的网格元素设置每列的大小
            minmax(min.max)  设置大于等于 min 且小于等于 max
            length  使用自定义的长度值设置列的大小。阅读关于长度单位内容
            %  使用百分比值设置列的大小
        grid-auto-rows  行的默认大小
            auto  默认值。 列的大小由容器的大小决定
            max-content  根据列中最大的网格元素设置每列的大小
            min-content  根据列中的最小的网格元素设置每列的大小
            length  使用自定义的长度值设置列的大小。阅读关于长度单位内容
        grid-auto-flow: row|column|dense|row dense|column dense;  指定自动布局算法怎样运作，精确指定在网格中被自动布局的元素怎样排列
            row  默认值。 通过填充每一行来放置网格元素，在必要时增加新列。
            column  通过填充每一列来放置网格元素，在必要时增加新列。
            dense  该关键字指定自动布局算法使用一种"稠密"堆积算法，如果后面出现了稍小的元素，则会试图去填充网格中前面留下的空白。这样做会填上稍大元素留下的空白，但同时也可能导致原来出现的次序被打乱。
            row dense  按行来填充网格中前面留下的空白
            column dense  按列来填充网格中前面留下的空白
        
    <!-- 媒体查询 -->
        @media screen and (max-width: 300px) {
            body {background-color:lightblue;}
        }

        @media not|only mediatype and (mediafeature and|or|not mediafeature) {
            CSS-Code;
        }
        not: 否定媒体查询，不满足返回true，否则返回false

        only: 整个查询匹配时才用于应用样式

        ,:  将多个媒体查询合并为一个规则,类似or运算符

        and: 当每个查询规则都为真时则该条媒体查询为真，它还用于将媒体功能与媒体类型结合在一起

            mediatype媒体类型:
                all	用于所有设备
                print	用于打印机和打印预览
                screen	用于电脑屏幕，平板电脑，智能手机等。
                speech	应用于屏幕阅读器等发声设备
    
            媒体功能:
                宽度
                width  定义输出设备中的页面可见区域宽度
                max-width  定义输出设备中的页面最大可见区域宽度
                min-width  定义输出设备中的页面最小可见区域宽度

                高度
                height  定义输出设备中的页面可见区域高度
                max-height  定义输出设备中的页面最大可见区域高度
                min-height  定义输出设备中的页面最小可见区域高度

                宽高比例
                aspect-ratio  定义输出设备中的页面可见区域宽度与高度的比率
                max-aspect-ratio  定义输出设备的屏幕可见宽度与高度的最大比率
                min-aspect-ratio  定义输出设备中的页面可见区域宽度与高度的最小比率

                device-aspect-ratio  定义输出设备的屏幕可见宽度与高度的比率
                device-width  定义输出设备的屏幕可见宽度
                device-height  定义输出设备的屏幕可见高度
                max-device-aspect-ratio  定义输出设备的屏幕可见宽度与高度的最大比率
                max-device-width  定义输出设备的屏幕最大可见宽度
                max-device-height  定义输出设备的屏幕可见的最大高度
                min-device-aspect-ratio  定义输出设备的屏幕可见宽度与高度的最小比率
                min-device-height  定义输出设备的屏幕的最小可见高度
                min-device-width  定义输出设备的屏幕最小可见宽度
                
                颜色
                color  定义输出设备每一组彩色原件的个数。如果不是彩色设备，则值等于0
                max-color  定义输出设备每一组彩色原件的最大个数
                min-color  定义输出设备每一组彩色原件的最小个数
                color-index  定义在输出设备的彩色查询表中的条目数。如果没有使用彩色查询表，则值等于0
                max-color-index  定义在输出设备的彩色查询表中的最大条目数
                min-color-index  定义在输出设备的彩色查询表中的最小条目数
                monochrome  定义在一个单色框架缓冲区中每像素包含的单色原件个数。如果不是单色设备，则值等于0
                max-monochrome  定义在一个单色框架缓冲区中每像素包含的最大单色原件个数
                min-monochrome  定义在一个单色框架缓冲区中每像素包含的最小单色原件个数

                分辨率
                max-resolution  定义设备的最大分辨率
                min-resolution  定义设备的最小分辨率

                竖屏/横屏
                orientation：portrait | landscape
                    portrait  竖屏(高度大于或等于宽度)
                    landscape  横屏
                    
                resolution  定义设备的分辨率。如：96dpi, 300dpi, 118dpcm

                grid  用来查询输出设备是否使用栅格或点阵
                scan  定义电视类设备的扫描工序

        <!-- 宽度大于 900px 的屏幕使用该样式 -->
            <link rel="stylesheet" media="screen and (min-width: 900px)" href="widescreen.css">
        <!-- 宽度小于或等于 600px 的屏幕使用该样式 -->
            <link rel="stylesheet" media="screen and (max-width: 600px)" href="smallscreen.css">

    <!-- 滤镜 -->
        filter: none;  // 定义了元素(通常是<img>)的可视效果(如：模糊与饱和度)
            none  默认值，没有效果
            blur(1px)  设置高斯模糊效果
            brightness(100%)  设置亮度
                0%(暗)--100%(默认)--(亮)
            contrast(100%)  设置对比度
                0%(暗)--100%(默认)--(亮)
            drop-shadow(x y blur color)  设置阴影效果
            grayscale(0%)  设置灰度图像
                0%(默认)--100%(灰)
            hue-rotate(0deg)  设置色相旋转
                0deg(默认)--360deg
            invert(0%)  反转输入图像
                0%(默认)--100%(反转)
            opacity(0%)  设置透明度
                0%(透明)--100%(默认)
            saturate(100%)  设置饱和度
                0%(不饱和)--100%(默认)--(饱和)
            sepia(0%)  设置为深褐色
                0%(默认)--100%(深褐色)
            
            url()  接受XML文件，设置SVG滤镜，包含一个锚点来指定一个具体的滤镜元素
                url(svg-url#element-id)

        backdrop-filter: none;  // 元素后面区域添加图形效果（如模糊或颜色偏移:滤镜）
            none;
            blur(2px);
            brightness(60%);
            contrast(40%);
            drop-shadow(4px 4px 10px blue);
            grayscale(30%);
            hue-rotate(120deg);
            invert(70%);
            opacity(20%);
            sepia(90%);
            saturate(80%);

            url()
                url(commonfilters.svg#filter);

        mix-blend-mode: normal;  // 元素(img)与父元素的内容和元素的背景如何混合
            normal;
            multiply;
            screen;
            overlay;
            darken;
            lighten;
            color-dodge
            color-burn;
            hard-light;
            soft-light;
            difference;
            exclusion;
            hue;
            saturation;
            color;
            luminosity;

### 不常用属性
    direction: rtl|ltr;  // 设置文本书写方向
    unicode-bidi: normal|embed|bidi-override;  // 与 direction 属性一起使用，来设置或返回文本是否被重写
        normal	默认。不使用附加的嵌入层面
        embed	创建一个附加的嵌入层面
        bidi-override	创建一个附加的嵌入层面。重新排序取决于 direction 属性

    <!-- 分页符 -->
        page-break-inside
            auto	默认。如果必要则在元素内部插入分页符
            avoid	避免在元素内部插入分页符
        page-break-after  属性用于设置在指定元素后面插入分页符
        注意： 请尽可能少地使用分页属性，并且避免在表格、浮动元素、带有边框的块元素中使用分页属性。
            auto	默认值。如果必要则在元素前插入分页符。
            always	在元素前插入分页符。
            avoid	避免在元素前插入分页符。
            left	在元素之前足够的分页符，一直到一张空白的左页为止。
            right	在元素之前足够的分页符，一直到一张空白的右页为止。
            inherit	规定应该从父元素继承 page-break-before 属性的设置。
        page-break-before  元素在指定元素前添加分页符

    counter-increment  // 计数器
    counter-reset  // 计数器

    all: initial|inherit|unset;
        all 属性用于重置所有属性，除了 unicode-bidi 和 direction

    quotes  属性设置嵌套引用的引号类型
        none	规定 "content" 属性的 "open-quote" 和 "close-quote" 的值不会产生任何引号。
        string string string string  定义要使用的引号,前两个值规定第一级引用嵌套，后两个值规定下一级引号嵌套

    pointer-events: auto;  // 属性用于设置元素是否对鼠标事件做出反应
        auto  默认值，设置该属性链接可以正常点击访问
        none	元素不能对鼠标事件做出反应

        /* 属性值 */
        pointer-events: visiblePainted; /* 只适用于 SVG */
        pointer-events: visibleFill;    /* 只适用于 SVG */
        pointer-events: visibleStroke;  /* 只适用于 SVG */
        pointer-events: visible;        /* 只适用于 SVG */
        pointer-events: painted;        /* 只适用于 SVG */
        pointer-events: fill;           /* 只适用于 SVG */
        pointer-events: stroke;         /* 只适用于 SVG */
        pointer-events: all;            /* 只适用于 SVG */


        visiblePainted  元素只有在以下情况才会成为鼠标事件的目标：
            visibility属性值为visible，且鼠标指针在元素内部，且fill属性指定了none之外的值
            visibility属性值为visible，鼠标指针在元素边界上，且stroke属性指定了none之外的值

        visibleFill  只有在元素visibility属性值为 visible，且鼠标指针在元素内部时，元素才会成为鼠标事件的目标，fill属性的值不影响事件处理

        visibleStroke  只有在元素 visibility 属性值为 visible，且鼠标指针在元素边界时，元素才会成为鼠标事件的目标，stroke 属性的值不影响事件处理

        visible  只有在元素 visibility 属性值为 visible，且鼠标指针在元素内部或边界时，元素才会成为鼠标事件的目标，fill 和 stroke 属性的值不影响事件处理

        painted  元素只有在以下情况才会成为鼠标事件的目标：
            鼠标指针在元素内部，且 fill 属性指定了 none 之外的值
            鼠标指针在元素边界上，且 stroke 属性指定了 none 之外的值
            visibility 属性的值不影响事件处理

        fill  只有鼠标指针在元素内部时，元素才会成为鼠标事件的目标，fill 和 visibility 属性的值不影响事件处理

        stroke  只有鼠标指针在元素边界上时，元素才会成为鼠标事件的目标，stroke和 visibility属性的值不影响事件处理

        all  只有鼠标指针在元素内部或边界时，元素才会成为鼠标事件的目标，fill、stroke 和 visibility 属性的值不影响事件处理

###  <!-- 垂直居中对齐方式 -->
    1、
        {
            padding: 50px 0;
            text-align: center;
        }
    2、
        {
            line-height: 100px;
            text-align: center;
        }
    3、
        {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    4、
        {
            display: flex;
            margin: auto;
        }

### 响应式设计Viewport(视区)
    平板响应式:
        <meta name="viewport" content="width=device-width, initial-scale=1.0">  // 移动端适配
            width：控制 viewport 的大小，可以指定的一个值，如 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）
            height：和 width 相对应，指定高度
            initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例
            maximum-scale：允许用户缩放到的最大比例
            minimum-scale：允许用户缩放到的最小比例
            user-scalable：用户是否可以手动缩放

        * {
            box-sizing: border-box;
        }

        @media only screen and (orientation: landscape) {
            body {
                background-color: lightblue;
            }
        }
            orientation：portrait | landscape
                portrait  竖屏(高度大于或等于宽度)
                landscape  横屏

## Less
    @name: bule;
    div{
        color: @name;
    }

    # 变量
        声明变量
            属性值：@xxx：xxx；
            选择器：#@{xxxxx}
            url：@{url}

    # 混合
        div(@color){
            width: 100px;
            height: 100px;
            color: @color;
        }

        #ID{
            .class(red)
        }

    # 继承
        div{
            color: red;
        }
        div2:extend(div){
            width: 100px;
        }

## Sass
    https://www.sass.hk/
    Live Sass Compiler扩展
        配置
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

    语法扩展
        font-size: 16px;
        font-family: sans-serif;

        font: {
            size: 16px;
            family: sans-serif;
        }

    定义变量
        $color: red;

        div {
            color: $color;
            $width: 50px !global;  //全局变量
        }

    导入
        _pubilc.scss
        @import 'url';

    混合
        @mixin name{

        }
        @mixin name($a, $b, $c:10px){
            width: $a;
            height: $b;
            font-size: $c;
        }

        div{
            @include name;
        }
        div{
            @include name(10px, 20px);
        }

    继承
        @extend %class

    占位符
        必须配合继承使用
        %class

    运算
        and与、or或、not非
        @if 条件 {

        }
        @else {

        }
        三元表达式
            color: if(条件, true, false)

    插值语法
        #{$width}

    函数
        @function name(){
            @return
        }
        name();

    @for
        to 包含start不包含end
        through 包含start与end的值
        @for $i from 1 to 4{
            .p#{$1} {

            }
        }

## Stylus
