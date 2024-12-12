## CSS√
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

<!-- 
    引入外部资源
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
 -->

### css函数√
    https://www.runoob.com/cssref/css-functions.html

    calc()  // 函数用于动态计算长度值
        width: calc(100% - 100px);

    rgb()  // 使用红(R)、绿(G)、蓝(B)三个颜色的叠加来生成各式各样的颜色
        background-color: rgba(255, 0, 0,);
    rgba()  // 使用红(R)、绿(G)、蓝(B)、透明度(A)的叠加来生成各式各样的颜色
        background-color:rgba(255, 0, 0, 0.3);

    max()  // 从一个逗号分隔的表达式列表中选择最大的值作为属性的值
        width: max(50%, 300px);
    min()  // 从一个逗号分隔的表达式列表中选择最小的值作为属性的值
        width: min(50%, 300px);

### css单位√
    相对长度
        em	相对长度单位。一般浏览器字体大小默认为16px，则2em == 32px
        rem  作用于非根元素时，相对于根元素字体大小；作用于根元素字体大小时，相对于其出初始字体大小
        vw	视窗宽度，1vw=视窗宽度的1%
        vh	视窗高度，1vh=视窗高度的1%
        vmin  vw和vh中较小的那个
        vmax  vw和vh中较大的那个
        %

    绝对长度
        px  像素 (1px = 1/96th of 1in)

### css选择器√
    !important
    style=''   1000
    id:  #HOME  100
    class|伪类|属性:  .home/[name=home]  10
    div|伪元素:  div  1
    *

    #HEADER {}  // id选择器
    .header {}  // 类选择器
    [name] {}  // 属性选择器
    p {}  // 元素选择器
    * {}  // 通配选择器
    
    
    div,p {}  // 选择所有 <div> 元素和 <p> 元素
    div p {}  // 后代选择器(空格分隔)
    div > p {}  // 子元素选择器(>号分隔)
    div + p {}  // 相邻兄弟选择器(+分隔)紧跟在 <div> 元素之后的第一个 <p> 元素
    div ~ p {}  // 普通兄弟选择器(～分隔)选择div元素之后的每一个p元素


    :link  // 选择所有未访问链接
    :visited  // 选择所有访问过的链接
    :active  // 选择活动链接
    :hover  // 选择鼠标在链接上面时

    :before  // 在元素之前插入内容
    :after  // 在元素之后插入内容


    :first-child  // 匹配第一个子元素
    :last-child  // 匹配最后一个子元素
    :nth-child(n)  // 匹配第n个子元素,odd(奇数)even(复数)
    :nth-last-child(n)  // 元素是其父级的n子元素，倒数

    :only-child  // 元素是其父级的唯一子元素（筛选）
    :empty  // 匹配该元素没有任何子级的元素（包括文本节点）
    :not(p)  // 匹配每个非p元素的元素
    
    :root  // 选择文档的根元素

<!-- 
    input:
        :enabled  定义每一个已启用的输入元素样式
        :disabled  定义每一个禁用的输入元素样式
        :checked  定义每个选中的输入元素样式
        :focus  选择具有焦点的输入元素

        :out-of-range  定义值在指定区间之外的input元素的样式
        :in-range  定义值在指定区间之内的input元素

        :read-write  用于匹配可读及可写的元素(即没有 "readonly" 属性的input)
        :read-only  用于匹配设置 "readonly"（只读） 属性的元素
        :required  用于匹配设置了 "required" 属性的元素(必填)
        :optional  用于匹配可选的输入元素

        :valid  用于匹配输入值为合法的元素
        :invalid  用于匹配输入值为非法的元素
 -->

## css2属性

#### <!-- 常用属性 -->√
        width  // 设置元素的宽度  => max-width/min-width
        height  // 设置元素的高度  => max-height/min-height

        border: 1px solid pink;  // 边框样式,dotted点线边框|dashed虚线边框|double双层边框
        border-radius: 左上 右上 左下 右下;  //圆角

        margin  // 外边距
        padding  // 内边距

        z-index: 1;  // 调整显示层级
        opacity: 0.5;  // 透明度

        position: absolute;  // 绝对定位(父级)
            relative  // 相对定位(自身)
            fixed  // 广告定位
            sticky  // 粘性定位

        float: left|right;  // 浮动
        clear: none|left|right|both;  // 清除浮动
            none  // 默认值。允许浮动元素出现在两侧
            left  // 在左侧不允许浮动元素
            right  // 在右侧不允许浮动元素
            both  // 在左右两侧均不允许浮动元素

        box-sizing: content-box|border-box;  // 怪异盒模型
            content-box  // 默认值
            border-box  // 怪异盒
        
        display: inline;  // 默认。内联元素，设置元素的内部和外部的显示类型
            block  // 块级元素
            inline-block  // 行内块元素
            none  // 此元素不会被显示

        outline: none;  // 去除聚焦边框(input输入框)
        resize: none;  // 禁止文本框重置大小(textarea文本框)

        overflow: visible;  // 默认值。(overflow-y/overflow-x)
            hidden  // 溢出隐藏
            scroll  // 滚动条
            auto  // 自适应滚动条
            
        visibility: visible;  // 默认值。元素是可见的
            hidden  // 元素是不可见的
            collapse  // 删除一行或一列，并且不影响表格的布局(表格元素)

        list-style-type: none;  // 清除列表默认样式
            disc  // 默认。标记是实心圆
            circle  // 标记是空心圆
            square  // 标记是实心方块
            decimal  // 标记是数字
            decimal-leading-zero  // 0开头的数字标记。(01, 02, 03, 等。)
            cjk-ideographic  // 简单的表意数字(一、二、三)
            lower-alpha  // 小写英文字母(a, b, c, d, e, 等。)
            upper-alpha  // 大写英文字母(A, B, C, D, E, 等。)

        list-style-position: outside;  // 默认值。列表项目标记放置在文本以外
            inside  // 列表项目标记放置在文本以内

        list-style-image: url('');  // 设置列表样式图片

<!-- 
        li::marker{content: '😅';}  // 更改li前面的圆点

        clip: rect(top, right, bottom, left);  // 剪辑一个绝对定位的元素

        vertical-align: 1px;  // 元素的垂直对齐方式(调整基线)
            baseline  默认。元素放置在父元素的基线上。
            sub  垂直对齐文本的下标
            super  垂直对齐文本的上标
            top  把元素的顶端与行中最高元素的顶端对齐
            middle  把此元素放置在父元素的中部
            bottom  使元素及其后代元素的底部与整行的底部对齐
            text-top  把元素的顶端与父元素字体的顶端对齐
            text-bottom  把元素的底端与父元素字体的底端对齐
            length  将元素升高或降低指定的高度，可以是负数
            %  使用 "line-height" 属性的百分比值来排列此元素。允许使用负值

        direction: rtl|ltr;  // 设置文本书写方向

        clip: rect(0, 100px, 100px, 0);  // 裁剪一张绝对定位的图像
            shape  设置元素的形状。唯一合法的形状值是：rect (top, right, bottom, left)

        content: " (" attr(href) ")";  // 插入文本,与 :before 及 :after 伪元素配合使用，来插入内容
            none  空值
            string  设置文本内容
            url(url)  设置某种媒体（图像，声音，视频等内容）的链接地址

        列：
        columns: 100px 3;  // 指定元素的列的宽度和数量
            column-width: 100px;  // 指定每列的宽度
            column-count: 3;  // 划分元素列数
        column-gap: 40px;  // 指定列的间隙
        column-rule: 3px outset #ff00ff;  // 指定列之间的规则：宽度，样式和颜色
        column-span: n|all;  // 指定某个元素应该跨越多少列
            num  指定几列
            all  横跨所有列
 -->

#### <!-- background背景 -->√
        background: color url('') no-repeat right top;  // 简写
        background-color: pink;  // 背景颜色
        background-repeat: center|no-repeat|repeat-x|repeat-y;  // 平铺方式
        background-position: right top;  // 定位

        background-image: url('');  // 背景图片
        background-size: length|percentage|cover|contain;  //背景图片尺寸,12px 12px、100% 100%、完全覆盖、自适应

        background-attachment: scroll;  // 默认值。背景图片随着页面的滚动而滚动
            fixed  // 背景图片不会随着页面的滚动而滚动(永远显示在当前)
            local  // 背景图片会随着元素内容的滚动而滚动
<!-- 
    background-origin  // 指定背景图像的定位区域
                padding-box	背景图像填充框的相对位置
                border-box	背景图像边界框的相对位置
                content-box	背景图像的相对位置的内容框
    background-clip  // 指定背景图像的绘画区域
        border-box	默认值。背景绘制在边框方框内（剪切成边框方框）
        padding-box	背景绘制在衬距方框内（剪切成衬距方框）
        content-box	背景绘制在内容方框内（剪切成内容方框）
 -->

#### <!-- 文本 -->√
        text-indent: 32px;  // 首行缩进
        text-align: left;  // 默认值,文本向左对齐
            center  // 居中
            right  // 右对齐
            justify  // 实现两端对齐文本效果(对最后一行文本无效)

        text-overflow: clip|ellipsis|string;  // 溢出文本如何展示
            clip  // 剪切文本
            ellipsis  // 显示省略符号 ... 来代表被修剪的文本
            string  // 使用给定的字符串来代表被修剪的文本

        text-decoration: line color style;  // 添加下划线、上划线、删除线等
            none  // 默认。定义标准的文本
            underline  // 下划线
            overline  // 上划线
            line-through  // 删除线

            text-decoration-style: solid;  // 默认值。线条将显示为单线
                double  // 线条将显示为双线
                dotted  // 线条将显示为点状线
                dashed  // 线条将显示为虚线
                wavy  // 线条将显示为波浪线

    <!-- font字体 -->
        color: pink;  // 设置字体颜色
        line-height: 16px;  // 设置行高
        letter-spacing: 2px;  // 设置字符间距
        word-spacing: 2px;  // 设置单词间距

        font-style: normal;  // 规定字体样式
            normal  默认值。浏览器显示一个标准的字体样式
            italic  浏览器会显示一个斜体的字体样式
            oblique  浏览器会显示一个倾斜的字体样式

        font-weight: normal|bold|bolder|lighter|100~900;  // 属性设置文本的粗细
            normal  默认值。定义标准的字符
            100~900  400 等同于 normal,而 700 等同于 bold

        font-size: medium;  // 默认值,字体大小
            16px  // 设置字体大小
            %  // 基于父元素的一个百分比值

    <!-- word单词 -->
            word-break: normal;  // 默认换行
                break-all;  // 拆分换行
                keep-all;  // 不拆分换行

            word-wrap: normal|break-word;  // 属性允许长单词可以自动换行
                normal  // 只在允许的断字点换行（浏览器保持默认处理）
                break-word  // 在长单词或 URL 地址内部进行换行

    <!-- 换行 -->
        white-space: ;  // 属性指定元素内的空白(空格/回车)怎样处理
            normal  // 默认。空白会被浏览器忽略(换行)
            nowrap  // 不换行
            pre  // 保留空白符,不换行
            pre-wrap  // 保留空白符序列,换行
            pre-line  // 合并空白符序列,换行
            break-spaces  // 行尾空格换行

                        换行符      空格和制表符    文字换行	行尾空格
            normal      合并        合并            换行        删除
            nowrap      合并        合并            不换行      删除
            pre         保留        保留            不换行      保留
            pre-wrap    保留        保留            换行        挂起
            pre-line    保留        合并            换行        删除
            break-spaces保留        保留            换行        换行

<!-- 
        text-align-last: auto;  // 属性规定如何对齐文本的最后一行
                    auto  默认值。最后一行被调整，并向左对齐
                    left  最后一行向左对齐
                    right  最后一行向右对齐
                    center  最后一行居中对齐
                    justify  最后一行被调整为两端对齐
                    start  最后一行在行开头对齐
                    end  最后一行在行末尾对齐

        text-transform: none;  // 英文大小写
            none  默认。定义带有小写字母和大写字母的标准的文本
            capitalize  文本中的每个单词以大写字母开头
            uppercase  定义仅有大写字母
            lowercase  定义无大写字母，仅有小写字母

        writing-mode: horizontal-tb;  // 文本在水平或垂直方向上如何排布
            horizontal-tb  默认
            vertical-rl  垂直方向自右而左的书写方式
            vertical-lr  垂直方向内内容从上到下，水平方向从左到右
            sideways-rl  内容垂直方向从上到下排列
            sideways-lr  内容垂直方向从下到上排列
 -->

#### <!-- 表格Table -->√
        border-collapse: collapse;  // 折叠表格的边框
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

#### <!-- cursor光标 -->√
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

## css3√

#### <!-- 阴影 -->√
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

#### <!-- flex弹性盒子 --> √
        display: flex/inline-flex;  // 弹性排列

        排列方向:
        flex-flow: flex-direction flex-wrap;  // 设置或检索弹性盒模型对象的子元素排列方式
            flex-direction: row | row-reverse | column | column-reverse;
                row  横向从左到右，默认的排列方式
                row-reverse  反转横向排列,右→左
                column  纵向排列，从上到下
                column-reverse  反转纵向排列，从下到上
            flex-wrap: nowrap|wrap|wrap-reverse;  // 换行方式
                nowrap  默认值。不换行
                wrap  换行
                wrap-reverse  换行，但是以相反的顺序（横轴）

        横轴的对齐方式:
        justify-content: flex-start|flex-end|center|space-between|space-around;
            flex-start  默认值。左对齐
            flex-end  右对齐
            center  居中
            space-between  均匀排列每个元素，首个元素放置于起点，末尾元素放置于终点
            space-around  均匀排列每个元素，每个元素周围分配相同的空间
            space-evenly  均匀排列每个元素，每个元素之间的间隔相等

        纵轴的对齐方式:
        align-content: stretch|center|flex-start|flex-end|space-between|space-around;
            stretch  默认值。元素被拉伸以适应容器(没有定义长度时)
            center  居中
            flex-start  开头对齐
            flex-end  结尾对齐
            space-between  均匀排列每个元素，首个元素放置于起点，末尾元素放置于终点
            space-around  均匀排列每个元素，每个元素周围分配相同的空间
            space-evenly  均匀排列每个元素，每个元素之间的间隔相等

        纵轴(子元素)的基线的对齐方式:
            align-items: stretch|center|flex-start|flex-end|baseline;
                stretch  默认值。元素被拉伸以适应容器(没有定义长度时)
                center  元素位于容器的中心
                flex-start  元素位于容器的开头
                flex-end  元素位于容器的结尾
                baseline  元素位于容器的基线上

        **作用于子元素:
            order: -1;  // 设置弹性盒模型子元素順序，数值小排名靠前

            align-self: auto|stretch|center|flex-start|flex-end|baseline;  // 覆盖容器的align-items
                auto  默认值
                stretch  元素被拉伸以适应容器(没有定义长度时)
                center  元素位于容器的中心
                flex-start  元素位于容器的开头
                flex-end  元素位于容器的结尾
                baseline  元素位于容器的基线上

            flex: 1;  // 弹性盒模型对象的子元素分配空间

#### <!-- 渐变 -->√
        线性渐变linear-gradient(默认从上到下)
            background-image: linear-gradient(90deg|to right, color1 30%, color2);
                repeating-linear-gradient  // 重复线性渐变

        径向渐变radial-gradient
            background-image: radial-gradient(circle圆形/ellipse椭圆形, [farthest at position],color);
                farthest-corner at 50% 50%  向最远角渐变 默认
                closest-side at 50% 50%  向最近边渐变
                closest-corner at 50% 50%  向最近角渐变
                farthest-side at 50% 50%  向最远边渐变
            
                repeating-radial-gradient  // 重复径向渐变

        圆锥渐变
            conic-gradient(from 0deg at 50% 50%, color1, color2)  // 定义了一个圆锥渐变
            repeating-conic-gradient()  // 重复的圆锥渐变

#### <!-- 过渡 -->√
        transition: property duration timing-function delay;
            transition-property  // all所有属性or指定某个CSS属性(以逗号隔开)
            transition-duration: time;  需要花费的时间
            transition-timing-function  指定转速曲线
                ease  // 默认,慢速开始,然后变快,然后慢速结束
                linear  // 匀速
                ease-in  // 慢速开始
                ease-out  // 慢速结束
                ease-in-out  // 慢速开始和慢速结束
                cubic-bezier(n,n,n,n)  // 贝塞尔曲线函数
            transition-delay: time;  何时开始

#### <!-- 动画 -->√
        // 创建动画
        @keyframes myAnimation {
            from|0% { 
                top:0px; 
            }
            to|100% { 
                top:200px; 
            }
        }

        // 使用动画
        animation: name duration timing-function delay iteration-count direction fill-mode play-state;
            animation-name: myAnimation;  // 绑定哪个动画
            animation-duration: time;  // 所需时间
            animation-timing-function: ease;  // 完成周期
                ease  // 默认。低速开始，然后加快，在结束前变慢
                linear  // 匀速
                ease-in  // 低速开始
                ease-out  // 低速结束
                ease-in-out  // 低速开始和结束
                cubic-bezier(n,n,n,n)  // 贝塞尔曲线
            animation-delay: time;  // 设置动画在启动前的延迟间隔
            animation-iteration-count: number|infinite;  // 播放次数(infinite无限)
            animation-direction: normal;  // 是否反向播放动画
                normal  // 默认值
                reverse  // 反向播放
                alternate  // 奇数正向播放，偶数反向播放
                alternate-reverse  // 奇数反向播放，偶数正向播放
            animation-fill-mode: none;  // 动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式
                none  // 默认值。动画在动画执行之前和之后不会应用任何样式到目标元素
                forwards  // 应用动画结束后的样式
                backwards  // ???
                both  // 动画遵循 forwards 和 backwards 的规则。动画会在两个方向上扩展动画属性。
            animation-play-state: paused|running;  // 指定动画是否正在运行或已暂停(paused暂停|running运行)
        
#### <!-- 2D/3D旋转 -->√
        transform: none|transform-functions;  // 将元素旋转，缩放，移动，倾斜等
            none  定义不进行转换
            平移: px
                translate(x,y)  // 平移
                translateX(x)  平移X 轴的值
                translateY(y)  平移Y 轴的值
                translateZ(z)  3D平移Z 轴的值
                translate3d(x,y,z)  3D转换
            缩放: number倍数
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

        backface-visibility: visible|hidden;  // 隐藏旋转 div 元素的背面(3D)
            visible  // 背面是可见的
            hidden  // 背面是不可见的

<!--    
        transform-origin: x-axis % y-axis % z-axis px;  // 指定从哪个位置转换元素
        transform-style: flat|preserve-3d;  // 指定嵌套元素是怎样在三维空间中呈现
            flat  所有子元素在2D平面呈现
            preserve-3d  所有子元素在3D空间中呈现

        perspective: 10px|none;  // 元素距离视图的距离
        perspective-origin: x-axis y-axis;  // 属性定义3D元素所基于的X轴和Y轴。该属性允许您改变 3D 元素的底部位置
            x-axis: %  定义该视图在 x 轴上的位置。默认值：50%。
            y-axis: %  定义该视图在 y 轴上的位置。默认值：50%。
-->

#### <!-- 网格布局 -->√
        父元素:
        display: grid|inline-grid;  // 设置为网格布局

        grid-template: auto / auto auto auto;  // 简写属性
        grid-template-rows: auto;  // 每行的高度
        grid-template-columns: auto auto auto|1fr;  // 定义列的数量及宽度(1fr: 一等份)
        
        grid-gap: 10px 50px;  // 简写属性:行和列的间隙
        grid-row-gap:  ;  // 行间隔
        grid-column-gap:  ;  // 列间隔

        子元素:
        grid-area: grid-row-start grid-column-start grid-row-end grid-column-end;
            grid-area: 2 / 1 / span 2 / span 3;  第2行开始和第1列开始，横跨2行3列

        设置某个网格元素item列的开始与结束
            grid-column: 1 / 3;
            grid-column-start: 1;
            grid-column-end: 3;

        设置某个网格元素item行的开始与结束
            grid-row: 1 / 3;
            grid-row-start: 1;
            grid-row-end: 3;

<!-- 
    grid-auto-columns  列的默认大小
            auto  默认值。 列的大小由容器的大小决定
            length  使用自定义的长度值设置列的大小。阅读关于长度单位内容
    grid-auto-rows  行的默认大小
        auto  默认值。 列的大小由容器的大小决定
        length  使用自定义的长度值设置列的大小。阅读关于长度单位内容
    grid-auto-flow: row|column|dense|row dense|column dense;  指定自动布局算法怎样运作，精确指定在网格中被自动布局的元素怎样排列
        row  默认值。 通过填充每一行来放置网格元素，在必要时增加新列
        column  通过填充每一列来放置网格元素，在必要时增加新列
 -->
        
#### <!-- 媒体查询 -->√
        @media not|only mediatype and (mediafeature and|or|not mediafeature) {
            CSS-Code;
        }
            not  // 否定媒体查询,不满足返回true,否则返回false
            only  // 整个查询匹配时才用于应用样式
            ,  // 将多个媒体查询合并为一个规则,类似or运算符
            and  // 当每个查询规则都为真时则该条媒体查询为真，它还用于将媒体功能与媒体类型结合在一起

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

                分辨率
                max-resolution  定义设备的最大分辨率
                min-resolution  定义设备的最小分辨率

                竖屏/横屏
                orientation：portrait | landscape
                    portrait  竖屏(高度大于或等于宽度)
                    landscape  横屏
                    
                resolution  定义设备的分辨率。如：96dpi, 300dpi, 118dpcm

        例:
            @media screen and (max-width: 300px) {
                body {background-color:lightblue;}
            }

        <!-- 宽度大于 900px 的屏幕使用该样式 -->
            <link rel="stylesheet" media="screen and (min-width: 900px)" href="widescreen.css">
        <!-- 宽度小于或等于 600px 的屏幕使用该样式 -->
            <link rel="stylesheet" media="screen and (max-width: 600px)" href="smallscreen.css">

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
    4、√
        {
            display: flex;
            margin: auto;
        }

<!-- 常用技巧 -->
        //  单行文本两端对齐
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