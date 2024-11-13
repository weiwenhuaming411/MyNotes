## 书写规范
    const定义常量、let定义变量
        let mySchool = "我的学校"

    class,使用小写字母和中划线
        class="my-school"

    ID,大写字母和下划线
        <view id="MY_SCHOOL"></view>

    组件命名,首字母大写,及驼峰命名规则
        例: MyPay.vue

    函数命名命名规范
        驼峰式命名，统一使用动词或者动词+名词形式
        请求数据方法，以data结尾
        methods: {
            jumpPage(){},
            openCarInfoDialog(){},
            getListData(){},
            postFormData(){}
        }
        has: 判断是否含有某个值
        is: 判断是否为某个值
        get: 获取某个值
        set: 设置某个值
        update: 更新某个值
        on: 触发事件（click/change 等 dom 事件或者emit派发事件）
        render: 渲染页面
        handle: 执行某一个事件（如果不清楚用什么动词前缀，可以使用 handle）
        还有很多类似的动作，例如：add/delete/put/select/change/move/remove/to等

        例外情况:
            作用域不大临时变量可以简写，比如：str，num，bol，obj，fun，arr
            循环变量可以简写，比如：i，j，k 等

## javaScript API√
    "use strict";  严格模式
    debugger;  断点、调试代码
    //#region  // 注释折叠

    <!-- 数据类型 -->
        值类型: Number/String/Boolean/Null/Undefined/Symblo
        引用类型: Object/Array/Function/RegExp/Date
        
        new Boolean():
            值为0、-0、null、""、false、undefined、NaN时为false

    <!-- Error错误处理 -->
        try(){}catch(err){}

        异常处理：
            ReferencError  非法引用
            TypeError  类型错误
            SyntaxError  语法错误
            URIError  encodeURI() 函数产生的错误
            RangeError  数值超出规定的范围
            SyntaxError  eval()函数产生的错误

            err.name  错误类型
            err.message  错误信息

    <!-- this指向 -->
        myFun.call(obj, 'xx', 'xx')
        myFun.apply(obj, ['xx', 'xx'])
        myFun.bind(obj, 'xx', 'xx')()  //有返回值且是个函数

    <!-- 条件语句 -->
        if(){}else{}

        不同的结果执行不同的代码
            switch(item){
                case 1: xxx;
                break;
                case 2: sss;
                default: ccc;
            }

    <!-- 循环 -->
        for(let i=0; i<number; i++){}
        for(item in obj){}

        while(){}
        do{}while()

        break  // 跳出循环
        continue  // 跳过本次循环

    <!-- 定时器 -->
        const T = setTimeout(() => {}，1000)  执行一次
        const T = setInterval(() => {}, 1000)  循环执行
        
        关闭定时器/重启
            clearInterval(T);
            clearTimeout(T);

    <!-- JSON -->
        JSON.parse(data)  // 将JSON转换成字符串
        JSON.stringify()  // 将字符串转换成JSON

#### 全局属性√
        属性:
            constructor  // 返回创建该属性的构造函数
            prototype  // 允许您向对象添加属性和方法
            length  // 对象长度
            data-name='value'
                element.dataset  // 获取自定义属性合集
                element.dataset.name  // 读取自定义属性
        方法:
            instanceof  // 判断一个属性是否存在一个对象身上(引用类型)
            typeof()  // 检测类型(值类型)
            parseFloat()  // 将字符串转换成浮点数
            parseInt()  // 将字符串转换成整型数字

            encodeURI()  把字符串编码为 URI
            decodeURI()  解码某个编码的 URI

            eval()  计算 JavaScript 字符串，并把它作为脚本代码来执行
            
#### Array数组√
        <!-- 添加 -->
        array.unshift(1)  // 向数组开头添加元素，并返回新的长度(修改原数组)
        array.push(1)  // 向数组末尾添加元素，并返回新的长度(改变原数组)

        <!-- 删除 -->
        array.shift()  // 删除并返回数组的第一个元素(改变原数组)
        array.pop()  // 删除并返回数组的最后一个元素(改变原数组)

        <!-- 读取 -->
        array.slice(start, end)  // 选取数组的一部分，并返回(不改变原数组)
        array.at(index)  // 返回索引值的值(负数倒数)

        <!-- 修改 -->
        array.reverse()  // 反转数组的元素顺序(改变原数组)
        array.sort((a, b) => {return a-b;})	 // 对原数组的元素进行排序。默认升序
        array.fill('', start, end)  // 使用一个值来替换数组(改变原数组)
        array.splice(index, number, newItem)  // 删除并返回删除元素后添加新元素(改变原数组)
        array.flat(2)  // 数组降维并返回，参数为深度(使用Infinity，可展开任意深度的嵌套数组)
        array.flatMap(item => {})  将多维数组降维并遍历数组
        
        <!-- 检索 -->
        array.indexOf()  // 搜索数组中的元素，并返回它的索引值,没找到则返回-1
        array.lastIndexOf()  // 从后面搜索数组中的元素，并返回它的索引值,没找到则返回-1
        array.includes()  // 判断一个数组是否包含一个指定的值true/false

        <!-- 拼接 -->
        array.join('')  // 使用字符串拼接数组，并返回拼接字符串
        array.concat(arr)  // 连接两个或更多的数组/字符串，并返回结果
        
        <!-- 遍历 -->
        array.forEach((item, index) => {})  // 遍历数组
        array.map((item) => {return})  // 遍历数组,并返回新数组

        <!-- 过滤 -->
        array.filter((item) => {})  // 过滤器,返回所有匹配的值，并生成新的数组

        <!-- 判断 -->
        array.every((item) => {})  // 遍历数组是否符合条件，全符合为true,否则false
        array.some((item) => {})  // 遍历数组是否含有符合条件，只要有一项满足条件，就会返回true
        array.find((item) => {})  // 返回第一个所匹配的值
        array.findIndex(item => {})  // 返回第一个所匹配的值的索引

        <!-- 累加器 -->
        array.reduce((total, item, index, arr)=>{}, value)  累加器（从左到右）
            total  必需。初始值, 或者计算结束后的返回值。
            item  必需。当前元素
            index  可选。当前元素的索引
            arr  可选。当前元素所属的数组对象
            value  可选。传递给函数的初始值
        
        <!-- Array -->
        Array.isArray()  // 判断是否为数组
        Array.from(arr, callback)  // 通过给定的对象中(伪数组)创建一个数组(必须要有length属性)
        Array.of(item, item2...)  // 将一组值转换为数组

<!-- 
    array.copyWithin(index, start, end)  // 从指定位置拷贝元素到数组的另一个指定位置中(覆盖原数组)
        index  必需。复制到指定目标索引位置。
        start  可选。元素复制的起始位置。
        end  可选。停止复制的索引位置 (默认为 array.length)。如果为负值，表示倒数。

    array.entries()  // 返回数组的可遍历对象
        let E = array.entries()
        console.log(E.next().value)  // [index, item]
    array.keys()  // 返回数组的可迭代对象，包含原始数组的键(key)
        let K = array.keys()
        console.log(K.next().value)  // 0(索引值)
 -->

#### Number数字√
        Number()  // 将字符串转换为数字
        Number.isFinite()  // 判断传递的参数是否为有限数字
        Number.isInteger()  // 判断传递的参数是否为整数
        Number.isNaN()  // 判断传递的参数是否为NaN
        
        number.toFixed(x)  // 保留几位小数(四舍五入)
        number.toPrecision(x)  // 返回一个指定长度的数字(四舍五入)

#### Math数学√
        Math.random()  // 1~0之间的随机数
        Math.abs(x)  // 返回 x 的绝对值
        Math.round()  // 四舍五入
        Math.ceil()  // 对数进行上舍入(5.12=6)
        Math.floor()  // 对数进行下舍入(1.59=1)
        Math.max(...arr)  // 返回最高值
        Math.min(...arr)  // 返回最低值
        Math.pow(x, y)  // 返回x的y次幂
        Math.trunc()  // 去掉小数部分
        Math.sign()  // 判断为正数1 负数-1 还是零0
        Math.sqrt(x)  // 返回数的平方根

        Math.PI  // 圆周率3.141592653589793

#### String字符串√
        string.split('')  把字符串分割为字符串数组
        .toString()	// 转换为字符串(或转换16、8、2进制)
        .trim()  // 去除首尾空白
        .charAt(index)  // 返回在指定索引的字符
        .toUpperCase()  // 把字符串转换为大写
        .toLowerCase()  // 把字符串转换为小写
        .search('')  // 查找相匹配的值,并返回索引值,没找到则返回-1(or正则)
        .charCodeAt(index)  // 返回在指定索引值的字符的 Unicode 编码

        String.fromCharCode()  // 将 Unicode 编码转为字符

<!-- 
        string.trimStart()  // 去除开头空白
        string.trimEnd()  // 去除结尾空白
        .repeat(num)  // 复制字符串指定次数，并将它们连接在一起返回
        .replace('oldStr', 'newStr')  // 匹配字符串并替换(单个)
        .replaceAll('oldStr', 'newStr')	// 匹配字符串并替换(所有)
        .startsWith('')  // 查看字符串是否以指定的字符串开头
        .endsWith('')  // 判断当前字符串是否是以指定的子字符串结尾的
        .localeCompare()  用本地特定的顺序来比较两个字符串,完全匹配0 匹配1 不匹配-1

        .substring(index, index)  // 提取字符串中两个指定的索引号之间的字符
        match(reg)  正则表达式的匹配,返回匹配值
        matchAll(reg)  批量匹配
 -->

#### Object对象√
        Object.is(a, b)  // 判断两个值是否相等,返回ture/false
        Object.assign(obj, objItem)  // 合并对象(同属性会覆盖)
        Object.setPrototypeOf(obj1, obj2)  // 给对象添加原型对象
        Object.getPrototypeOf(obj1)  // 读取对象的原型对象

<!-- 
        Object.entries(obj)  // 返回对象可遍历属性[key, value]的数组
        Object.fromEntries()  // 把[key, value]的数组转换成对象
        Object.getOwnPropertyDescriptors(obj)  // 获取对象属性的描述对象
 -->

## ES6
    <!-- 属性名表达式 -->
        const obj = {
            ["he"+"llo"](){
                return "Hi";
            }
        }
        obj.hello();  //"Hi"

    <!-- rest参数整合 -->
        let data = function(...rest){
            console.log(rest)  // [1, 2, 3]
        }
        data(1, 2, 3)

    <!-- Set集合(数组去重) -->
        let s = new Set(array);

    <!-- Map集合(扩展键的范围) -->
        let m = new Map();
        let school = {name: '学校'}
        m.set(school, 'xxx')  // 添加一个key为{name: '学校'},值为'xxx'的键值对

    # import按需加载:
        import("./js/count")
        .then((res)=>{
            console.log('模块加载成功', res)
        })
        .catch((err)=>{
            console.log('模块加载失败', err)
        })

    # Symblo类型
        let sym = Symblo();  //函数
        let sym = Symblo.for();  //函数对象
        独一无二
        不能运算
        不能for...in循环,但是可以使用reflect.ownKeys来获取对象的所有键名
        防止创建方法和对象本身的方法冲突
            const game = {}
            let sym = Symblo();
            game[sym] = functiom(){}
            game[sym]();
        
        Symbol.prototype.description  获取symblo字符串描述

    # calss 类
        calss Promise{
            name;  //公有属性
            #age  //私有属性，只能出现在类的内部
            static resolve(){}  //<!-- 静态属性 -->  //属于类，不属于构造对象
            
            <!-- 构造函数 -->
            constructor(){
                this.xxx = xxx;
            };
            
            get name(){}  //属性被读取时触发、访问私有属性
            set name(){}  //属性被调用时触发
        }

        extends继承一个类
            class Pro extends Promise{
                constructor(xxx){
                    super(xxx)  调用父类的构造方法
                }
            }

### 模块化
    # CommonJS
        暴露模块
            module.exports = {value}
            exports.name = value
        
        引入模块
            require(xxx)
                第三方模块(模块名字)
                自定义模块(文件路径)

    # ES6
        暴露模块
            分别暴露
                export function name(){}
            
            默认暴露
                export default ()=>{}, {}, []
                
            统一暴露
                export {}

        引入模块
            常规暴露
                import {name} from 'url'
            
            默认暴露
                import name from 'url'

            统一引入
                import * as API from 'url';

### Promise
    const p = new Promise((resolve, reject) => {xxx? resolve() : reject();})
        p.then((value) => {}, (reason) => {})

        // 只能做失败回调
        p.catch(() => {})

        异常穿透
            promise链式最后调用.catch()

        中断promise链
            返回一个peding状态的promise

    promise方法
        Promise.resolve()
            传入非promise对象，返回一个成功的promise对象
            传入promise对象，由参数结果决定resolve结果

        Promise.reject()
            返回一个失败的promise对象

        Promise.all()
            传入promise数组
            返回一个新的promise，只有所有的promise都成功才成功，只要有一个失败就直接失败

        Promise.allSettled()
            传入promise数组
            返回一个promise数组，值为每一个promise的状态和值

        Promise.race()
            传入promise数组
            返回一个新的promise，最先完成promise状态改变的结果

## Dom对象√

#### Document 对象√
    <!-- DOM属性 -->
        document.documentElement  返回文档的根节点  // <html lang="en"></html>
        document.cookie  设置或返回与当前文档有关的所有cookie
        document.title  返回当前文档的标题  // Document
        document.body  返回文档的body元素
        document.URL  返回文档完整的URL  // http://127.0.0.1:5501/html-demo/HTML/index.html

    <!-- DOM方法 -->
        创建node节点
        document.createElement('button')  // 创建元素节点
        document.createAttribute('class')  // 创建属性节点  // attr.value='demo'
        document.createTextNode('按钮')  // 创建文本节点

        获取元素节点
        document.getElementById('ID')  // 返回指定 ID 的元素
        document.getElementsByName('name')  // 返回带有指定名称的对象的集合
        document.getElementsByTagName('div')  // 返回指定标签名的所有子元素集合
        document.getElementsByClassName('class')  // 返回所有指定类名的元素集合
        document.querySelector('div'|'#ID'|'.class'|'attr'|'value')  // 返回指定元素的第一个子元素
        document.querySelectorAll()  // 返回指定元素的所有子元素节点列表

<!-- 
        document.doctype  返回与文档相关的文档类型声明 (DTD)  // <!DOCTYPE html>
        document.inputEncoding  返回用于文档的编码方式（在解析时）  // UTF-8
        document.activeElement  返回当前获取焦点的元素

        document.createComment('注释')  创建注释节点
        document.hasFocus()  // 方法来查看当前整个文档是否获取焦点

        添加事件
        document.addEventListener('click', ()=>{}, true/false)  // 添加事件
        document.removeEventListener()  // 移除事件
 -->       

#### element 对象√
    input.checked  // 返回选择框的状态(checkbox)
    element.focus()  // 为元素设置焦点(input/)
    element.blur()  // 移除元素焦点(input/)

    <!-- 事件 -->
    element.addEventListener('', ()=>{}, true捕获/false冒泡默认)  // 添加事件
    element.removeEventListener()  // 移除事件

    <!-- 父/兄弟/子元素 -->
    element.parentNode  // 返回元素的父节点
    element.previousElementSibling  // 返回元素的前一个兄弟元素(忽略文本和注释节点)
    element.nextElementSibling  // 返回元素之后的下一个兄弟元素(忽略文本和注释节点)
    element.children  // 返回元素的所有子元素集合
    element.firstElementChild  // 返回元素的第一个子元素(忽略文本和注释节点)  // .tagName获取标签名、.textContent获取文本    
    element.lastElementChild  // 返回指定元素的最后一个子元素(忽略文本和注释节点)  // .tagName获取标签名、.textContent获取文本

<!-- 基础属性 -->
        <!-- 增加/修改 -->
        element.id  // 设置或者返回元素的id
        element.className  // 设置或返回元素的class属性
        element.classList  // 返回元素的类名集合(.add('')添加类/.remove('')移除)
        element.title  // 设置或返回元素的title属性
        element.style  // 设置或返回元素的样式
        element.innerHTML  // 设置或返回元素的文本内容(包含元素节点)
        element.textContent  // 设置或返回元素的文本内容(仅限文本,会覆盖元素节点)

        <!-- 查询 -->
        element.ownerDocument  // 返回元素的根元素(document)
        element.tagName  // 返回元素的标签名(大写)
        element.attributes  // 返回一个元素的属性数组
        element.isContentEditable  // 返回元素内容是否可编辑(true/false)
        element.nodeType  // 返回元素的节点类型
        element.nodeValue  // 返回元素的节点值
        
<!-- node节点 -->
        <!-- 添加node -->
        element.appendChild(node)  // 为元素添加一个新的子节点(如元素已存在则会移除)
        element.insertBefore(newNode, node)  // 在元素的指定子元素之前添加新元素(如元素已存在则会移除)

        element.insertAdjacentHTML('position', html)  // 添加一段HTML
        element.insertAdjacentElement('position', eleNode)  // 添加元素
        element.insertAdjacentText('position', text)  // 添加文本
            afterbegin  // 插入到元素第一个子节点之前
            beforeend  // 元素最后一个子节点之后
            beforbegin  // 插入自身元素前面
            afterend  // 元素自身的后面

        <!-- 删除node -->
        element.removeChild(node)  // 删除元素的子节点
        
        <!-- 更改node -->
        element.replaceChild(newNode, oldNode)  // 替换元素的子节点(如元素已存在则会移除)

<!-- 标签属性 -->
        <!-- 添加/修改属性 -->
            element.setAttribute('attrName', 'attrValue')  // 添加属性
            element.setAttributeNode()  // 设置或者改变指定属性节点

        <!-- 删除属性 -->
            element.removeAttribute('attr')  // 删除属性  
            element.removeAttributeNode()  // 删除指定属性节点并返回移除后的节点

        <!-- 查询属性 -->
            element.getAttribute('name')  // 读取属性值
            element.getAttributeNode()  // 返回指定属性节点
            
        <!-- 检索元素 -->
            element.hasAttribute('attrName')  // 检测元素是否存在指定属性(true/false)
            element.hasAttributes()  // 检测元素是否存在任何属性(true/false)
            element.matches('.class')  检索元素是否存在指定的CSS选择器(true/false)

<!-- 文档/元素宽高 -->
        <!-- offset包含边框 -->
        element.offsetWidth  // 返回元素的宽度
        element.offsetHeight  // 返回元素的高度
        element.offsetLeft  // 返回当前元素X轴偏移文档左边缘的距离
        element.offsetTop  // 返回当前元素的Y轴偏移文档顶部边缘的距离
        element.offsetParent  // 返回元素的偏移父元素  // <body></body>

        <!-- client不含边框(不含滚动条) -->
        element.clientWidth  // 返回元素的可视宽度
        element.clientHeight  // 返回元素的可视高度
        element.clientLeft  // 返回元素左边框宽度
        element.clientTop  // 返回元素上边框宽度

        <!-- scroll不含边框(不含滚动条样式) -->
        element.scrollWidth  // 返回元素的整个宽度(包括带滚动条的隐蔽的宽度)
        element.scrollHeight  // 返回元素的整个高度(包括带滚动条的隐蔽的宽度)
        element.scrollLeft  // 返回元素滚动后的左边缘和视图左边缘之间的距离
        element.scrollTop  // 返回元素滚动后的顶部边缘和视图顶部边缘之间的距离

<!-- 
        element.dir  设置或返回一个元素中的文本方向  // ltl左、rtl右
        element.contentEditable  // 设置或返回元素的内容是否可编辑(inherit继承/true可编辑/false不可编辑)

        element.cloneNode(true/false)  // 克隆元素(true克隆子节点/false克隆当前节点(默认))
        element.hasChildNodes()  // 检测元素是否具有任何子节点(包含元素、文本、注释)

        const height = document.documentElement.scrollTop || document.body.scrollTop  // 获取文档滚动条滚动后的高度(兼容性)
 -->

#### 属性对象√
    element.attributes.item(index)  // 返回指定索引的属性节点
    element.attributes.length  返回属性列表的属性数目

    attr.isId  // 判断该属性是否是id(true/false)
    attr.specified  // 判断是否存在该属性(true/false)

    element.attributes.setNamedItem(attr)  // 从属性列表中设置指定属性节点(通过名称)
    element.attributes.getNamedItem("onclick")  // 从属性列表中返回的指定属性节点
    element.attributes.removeNamedItem('attrName')  // 从属性列表中删除指定属性节点
    
#### 事件对象√
    scroll  // 滚动条事件

    <!-- 事件属性 -->
        event.type  // 触发事件的类型
        target  // 触发事件的元素
        event.currentTarget  // 绑定事件的元素

    <!-- 鼠标事件对象属性 -->
        event.button  // 返回当事件被触发时，哪个鼠标按钮被点击  // 0左键|1中间|2右键

        event.clientX  // 鼠标指针相对于浏览器页面的水平坐标
        event.clientY  // 鼠标指针相对于浏览器页面的垂直坐标

    <!-- 鼠标事件 -->
    click  // 单击
    mouseenter  // 鼠标移至元素时(非冒泡)
    mouseleave  // 鼠标移出元素时(非冒泡)
    mousemove  // 鼠标移动时

    <!-- input输入框事件 -->
    focus  // 元素获取焦点时触发
    blur  // 元素失去焦点时触发
    input  // 元素获取用户输入时触发(立即触发)
    change  // 该事件在表单元素的内容改变时触发(失焦后触发)
    select  // 用户选取文本时触发

<!-- 
    form表单事件
        submit  // 表单提交时触发(<form></form>)
        invalid  // 当元素无效时运行脚本
        contextmenu  // 当触发上下文菜单时运行脚本
        formchange  // 当表单改变时运行脚本
        forminput  // 当表单获得用户输入时运行脚本

    鼠标事件
        dblclick  // 双击
        contextmenu  // 鼠标右键
        mousedown  // 鼠标按钮被按下
        mouseup  // 鼠标按键被松开
        mouseover  // 鼠标移至元素时(冒泡)
        mouseout  // 鼠标移出元素时(冒泡)
        mousewheel  // 鼠标滚轮转动时
        event.relatedTarget  // 返回触发事件的节点(mouseover,离开了哪个节点/mouseout,进入到哪个节点)

    键盘事件
        keydown  按下按键时
        keypress  按下并松开按键时
        keyup  松开按键时

    onresize  // 在窗口或框架被调整大小时发生<body></body>
    onpageshow  // 该事件在用户访问页面时触发<body></body>
    onload  // 在页面第一次加载时触发(只触发一次)<body></body>
    onbeforeunload  // 即将离开页面（刷新或关闭）时触发<body></body>
    onpagehide	// 在用户离开网页时触发<body></body>
    onunload  // 用户退出页面<body></body>

    剪贴板事件
        oncopy  该事件在用户拷贝元素内容时触发
        onpaste  该事件在用户粘贴元素内容时触发
        oncut  该事件在用户剪切元素内容时触发

    # 拖动事件
        ondrag  该事件在元素正在拖动时触发
        ondragend  该事件在用户完成元素的拖动时触发
        ondragenter  该事件在拖动的元素进入放置目标时触发
        ondragleave  该事件在拖动元素离开放置目标时触发
        ondragover  该事件在拖动元素在放置目标上时触发
        ondragstart  该事件在用户开始拖动元素时触发
        ondrop  该事件在拖动元素放置在目标区域时触发

    # CSS事件
        animationend  CSS 动画结束播放时
        animationiteration  CSS 动画重复播放时
        animationstart  CSS 动画开始播放时
        transitionend  CSS 完成过渡后触发

    #事件属性
        event.screenX  // 鼠标指针相对于屏幕的水平坐标
        event.screenY  // 鼠标指针相对于屏幕的垂直坐标
  -->

## BOM对象√
    <!-- 弹窗 -->
        alert() // 显示带有一段消息和一个确认按钮的警告框
        confirm()  // 显示带有一段消息以及确认按钮和取消按钮的对话框 ??? 如何获取用户点击
        prompt()  // 显示可提示用户输入的对话框  ??? 如何获取用户输入

    <!-- screen对象 -->
        screen.width  // 返回屏幕的总宽度
        screen.height  // 返回屏幕的总高度

    <!-- 本地存储 -->
        localStorage.setItem("key", "value")  // 添加键和值
        localStorage.getItem("key")  // 返回指定键的值
        localStorage.removeItem("key")  // 移除键
        localStorage.clear()  // 清除存储对象中所有的键

        sessinStorage.setItem("key", "value")  // 添加键和值
        sessinStorage.getItem("key")  // 返回指定键的值
        sessinStorage.removeItem("key")  // 移除键
        sessinStorage.clear()  // 清除存储对象中所有的键

    <!-- location对象 -->
        location.href  // 返回完整的URL  // http://127.0.0.1:5501/html-demo/HTML/index.html
        location.protocol  // 返回URL协议  // http:
        location.host  // 返回URL的主机名和端口  // 127.0.0.1:5501
        location.hostname  // 返回URL的主机名  // 127.0.0.1
        location.port  // 返回URL端口号  // 5501
        location.pathname  // 返回的URL路径名  // /html-demo/HTML/index.html
        location.search  // 返回一个URL的查询部分  // ?
        location.hash  // 返回一个URL的锚部分  // #
        location.origin  // 起源  // http://127.0.0.1:5501

        location.reload()  // 刷新当前页面

    <!-- history对象 -->
        history.back()  // 回退
        history.forward()  // 前进
        history.go(number|URL)  // 指定步数

<!-- 
    screen.availWidth  // 返回屏幕的宽度(不包括Windows任务栏)
    screen.availHeight  // 返回屏幕的高度(不包括Windows任务栏)
    window.screenLeft || window.screenX  // 返回窗口相对于屏幕的x坐标(不兼容火狐||不兼容IE)
    window.screenTop || window.screenY  // 返回窗口相对于屏幕的y坐标(不兼容火狐||不兼容IE)
 -->

 <!-- 
    scrollBy(x, y)	// 按照指定的像素值来滚动内容
    scrollTo(x, y)	// 把内容滚动到指定的坐标

    window.scrollX  // 获取滚动条滚动后的左边缘和视图左边缘之间的距离  // 滚动后
    window.scrollY  // 获取滚动条滚动后的顶部边缘和视图顶部边缘之间的距离  // 滚动后
    window.innerWidth  // 返回当前窗口可视的宽度(可调节)(内容区)
    window.innerHeight  // 返回当前窗口可视的高度(可调节)(内容区)
    window.outerWidth  // 返回当前窗口调节宽度，包含工具条与滚动条(可调节)(整个页面大小)
    window.outerHeight  // 返回当前窗口调节高度，包含工具条与滚动条(可调节)(整个页面大小)

    window.open(url[,opution(宽高)])  打开一个新的浏览器窗口
    window.close()  关闭浏览器窗口
    window.moveBy(x, y)  可相对窗口的当前坐标把它移动指定的像素
    window.moveTo(x, y)  把窗口的左上角移动到一个指定的坐标
    window.resizeTo(x, y)	把窗口的大小调整到指定的宽度和高度
    window.resizeBy(x, y)	按照指定的像素调整窗口的大小
    btoa()	创建一个 base-64 编码的字符串
    atob()	解码一个 base-64 编码的字符串
 -->

## RegExp正则
    https://www.runoob.com/jsref/jsref-obj-regexp.html
    const phone = /^1\d{10}$/

    let iphone = /^1[0-9]{10}$/
    let password = /^[a-z][a-z0-9]{5}$/
        ^ 开始标记
        $ 结束标记

## Date日期
    get/set/getUTC/setUTC
    getTime()	返回 1970 年 1 月 1 日至今的毫秒数。
    getFullYear()   返回年份
    getMonth()      返回月份(0-11)
    getDate()       返回当日
    getHours()      返回小时
    getMinutes()    返回分钟
    getSeconds()	返回秒数
    getMilliseconds()   返回毫秒

    parse()	返回1970年1月1日午夜到指定日期（字符串）的毫秒数。
    getDay()        一周中的某一天
    UTC()	根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。
    getUTCDay()	根据世界时从 Date 对象返回周中的一天 (0 ~ 6)。

    toJSON()	以 JSON 数据格式返回日期字符串。
    toISOString()	使用 ISO 标准返回字符串的日期格式。
    toDateString()	把 Date 对象的日期部分转换为字符串。
    toLocaleString()	根据本地时间格式，把 Date 对象转换为字符串。2023/5/31 14:11:53
    toLocaleDateString()	根据本地时间格式，把 Date 对象的日期部分转换为字符串。2023/5/31
    toLocaleTimeString()	根据本地时间格式，把 Date 对象的时间部分转换为字符串。14:12:12
    
    toString()	转换为字符串。Wed May 31 2023 14:12:31 GMT+0800 (中国标准时间)
    toTimeString()	把 Date 对象的时间部分转换为字符串。14:12:57 GMT+0800 (中国标准时间)
    toUTCString()	根据世界时，把 Date 对象转换为字符串。  
        
## 
<!-- 
    ## 各浏览器兼容性
    # 窗口尺寸
        有三种方法能够确定浏览器窗口的尺寸:
            对于Internet Explorer、Chrome、Firefox、Opera 以及 Safari：
                window.innerHeight - 浏览器窗口的内部高度(包括滚动条)
                window.innerWidth - 浏览器窗口的内部宽度(包括滚动条)
            对于 Internet Explorer 8、7、6、5：
                document.documentElement.clientHeight
                document.documentElement.clientWidth
            或者
                document.body.clientHeight
                document.body.clientWidth

            例: 实用的 JavaScript 方案（涵盖所有浏览器，包含 IE8 及以下版本的浏览器）：
                var w=window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
                var h=window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight;

## JavaScript 原理
    运行原理：编译一行，执行一行。
        编译    声明变量
        执行   赋值
        赋值变量LHS查询
        引用变量RHS查询

    堆与栈: 

    作用域：能够储存变量中的值，并且能对其进行访问或修改的区域。

    闭包: 形成一个不销毁的栈环境。

    with()/eval()：
        把字符串当作js代码执行（非"use strict"；模式下）
        注意️：影响性能，引擎无法在编译时对其作用域查找进行优化

    this指向: