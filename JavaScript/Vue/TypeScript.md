## TypeScript
    npm i typescript -g

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

<!-- interface定义接口 -->
    interface PersonInter{
        id: string,
        name: string
    }  // 定义

<!-- <>泛型 -->
    let person:Array<PersonInter> = []

<!-- 类型断言 -->
        value as string  // 
        变量<类型>
        
<!-- 类型 -->
    number
    string
    boolean
    object  //{}、let b :{name: string, [name: string]: any}
    function  //(形参：类型, ...) => 返回值类型
    array  //数值类型[]、Array<类型>
    any  //任意类型
    
    类型别名  type 属性名 = 类型;



    
 
    面向对象
        类
            public  //公用属性（默认）
            private  //私有属性
            protected  //包含属性，当前类和子类中访问
            readonly name;  //只读属性

        抽象类
            abstract class Promise  //抽象类，不能用来被创建实例
            abstract demo();  //抽象方法，没有方法体，子类必须重写

        <!-- interface定义接口 -->
            interface PersonInter{}  // 定义

            class myClass implements PersonInter{} //实现接口

## tsconfig.json
    编译 tsc -w
        tsconfig.json
            {
                "include": ["./src/**任意目录/*任意文件"],  // 编译指定文件
                "exclude": [ "./src/**任意目录/*任意文件"],  // 指定不编译文件
                "extends": "url",  // 继承指定配置文件
                "files": ["文件名","文件名"],  // 指定编译文件列表
                // 编译器选项
                complierOptions: {
                    "target": "ES3",  //指定编译版本
                    "mudule": "es6",  //指定模块化规范，conmmonjs
                    "lib": [],  //指定项目中要使用的库 
                    "outDir": "url",  //指定编译后的文件路径目录
                    "outFile": "url",  //将代码合成为一个文件
                    "allowJs": false,  //是否编译js文件
                    "checkJs": false,  //是否检查js代码
                    "removeComments": false,  //是否移除注释
                    "noEmit": false,  //是否不生成编译文件
                    "noEmitOnError": false,  //产生错误时是否编译文件
                    "alwaysStrict": false,  //是否开启严格模式
                    "noImplicitAny": false,  //是否不允许隐式的any
                    "noImplicitThis": flase,  //是否不允许不明确类型的this
                    "strictNullChecks": false,  //是否严格的检查空值
                    "strict": false,  //所有严格检查总开关
                }
            }
           