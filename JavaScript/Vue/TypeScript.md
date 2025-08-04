## TypeScript
    npm i typescript -g

<!-- interface接口定义 -->
    interface User{
        id: number,
        name: string
    }

    let user: User = {}

    <!-- 拓展接口 -->
    interface Item extends User {
        sex: number
    }

<!-- 类型别名 -->
    type User = string;

    let user: User = ''
    
    <!-- 扩展类型 -->
    type Item = User & {
        sex: number
    }

<!-- 类型断言 -->
    let str = 'str' as string
    or
    let str = <string>'str'

<!-- 枚举 -->

<!-- 类型 -->
    number
    string
    boolean
    object  // let user :User = {}  // interface User {}
    function  // (data：any) => 返回值类型
    array  // 数值类型[]、Array<类型>
    any  // 任意类型

    unknown  // 确保使用此类型的人声明类型是什么???
    never  // 这种类型不可能发生
    void  // 返回 undefined 或没有返回值的函数

<!-- 面向对象 -->
    <!-- 类 -->
        public  //公用属性（默认）
        private  //私有属性
        protected  //包含属性，当前类和子类中访问
        readonly name;  //只读属性

    <!-- 抽象类 -->
        abstract class Promise  //抽象类，不能用来被创建实例
        abstract demo();  //抽象方法，没有方法体，子类必须重写

<!-- 
    interface User {
        name: string;
        id: number;
    }
 
    class UserAccount {
        name: string;
        id: number;
    
        constructor(name: string, id: number) {
            this.name = name;
            this.id = id;
        }
    }
    
    const user: User = new UserAccount("Murphy", 1);
 -->

 <!-- 
    vue3:
        interface接口
            src/types/PersonInter.ts:
                export interface PersonInter{
                    id: string
                    name: string,
                    age?: number  // ?可选选项
                }

        引入:
            import {type PersonInter} from 'path'
            let person:PersonInter = {id:'0',name:'杨超越',age:18}
 -->

## tsconfig.json 文件 说明
    https://juejin.cn/post/7077102548640858125

<!-- tsconfig.json -->
    {
        "extends": "url",  // 继承指定配置文件
        "include": [ "src/**/*" ],  // 编译指定文件
        "exclude": [ "src/**/*" ],  // 指定不编译文件
        "files": [ "文件名","文件名" ],  // 指定编译文件列表(一般直接用include指定文件夹)
        // 编译器配置
        complierOptions: {
            "target": "ES3",  // 编译成指定的es版本的js *
            "mudule": "es6",  // 指定模块化规范  conmmonjs/es6
            "noEmit": true,  // 是否不生成编译文件 *
            "noImplicitAny": true,  // 是否不允许隐式的any *
            "strictNullChecks": true,  // 是否严格的检查空值 null/undefined *
            "removeComments": false,  // 是否移除注释 *
            "strict": true,  // 所有严格检查总开关 开启/关闭 *
            "tsBuildInfoFile": "./buildFile",  // 增量编译文件的存储位置 *
            "moduleResolution": "Bundler",  // 指定模块解析策略 *

            "noEmitOnError": false,  // 当有错误时候不生成编译后的文件

            "lib": [],  // 指定项目中要使用的库
            "outDir": "url",  // 指定编译后文件的所在目录
            "outFile": "url",  // 将代码合成为一个文件
            "allowJs": false,  // 是否对js进行编译，默认为false
            "checkJs": false,  // 是否检查js是否符合语法规范，默认为false
            "alwaysStrict": false,  // 编译后的文件是否使用严格模式
            "noImplicitThis": flase,  // 是否允许不明确类型的this

            // 用于设置模块名到基于baseUrl的路径映射
            "paths": {
                "@/*": [
                    "src/*"
                ]
            },
        }
    }
        