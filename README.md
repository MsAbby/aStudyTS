# 基础

## typescript?
01 定义1： 添加了类型系统的javascript<br>
01 定义2： 属于静态类型，弱类型的语言<br>
01 定义3： 是完全兼容 JavaScript 的，它不会修改 JavaScript 运行时的特性<br>
02 核心： 类型<br>
03 属性： 静态类型<br>

## 动态类型和静态类型区别？
01 动态类型： 在运行时才会进行类型检查，类型错误往往导致运行时报错<br>
02 js: 解释型语言，没有编译阶段，所以他是动态类型<br>
03 静态类型： 编译阶段检查每个变量的类型，类型报错会导致语法报错<br>
04 ts: 运行前需要编译成js, 编译阶段就会进行类型检查，所以是静态类型<br>

## 弱类型和强类型？
01 依据： 系统根据是否允许隐式转换来区分 <br>
02 归属： js && ts 属于弱类型（python是强类型） <br>

## 为什么要用typescript?
01 适合大型项目： 更高的维护性，增强了编辑器的功能，包括代码补全、接口提示、跳转到定义、代码重构等<br>
02 更严谨，更不容易出错<br>

## 安装
01 全局安装typecript: npm install -g typescript<br>
02 全局安装ts-node： npm install -g ts-node<br>


# 知识

## 数据类型(js)
01 js 分为两种： 基本数据类型和对象数据类型（引用数据类型）<br>
02 基本数据类型（6）： number, string, boolean, null, undefined, symbol(3+2+1)<br>
03 引用数据类型： object, array<br>

## 数据类型(ts)
01 ts 分为两种： 基础静态类型（定义了不可以改变）和对象静态类型<br>
01 基本数据类型：number, string, boolean, null, null, undefined, void, never<br> 
01 任意类型：any<br> 

## 类型注解 和 类型判断？
01 类型注解: Type Inference - 人为为一个变量指定类型<br>
02 类型判断：Type Inference - TS可以通过变量值倒推变量类型<br>

## "基础" 静态类型-注解
01 冒号后面跟类型
````
const aa: number = 1;
const bb: string = '11';

````

## " 对象" 静态类型
````
type Hello = {
    name: string
    age: number
}
const add: Hello = {
    name: '你好',
    age: 18
}
````

## "数组" 静态类型注解
````
const arr1: string[]=['1', '2', '3']
const arr2: number[]=[1, 2, 3, 4]
const undefinedarr3: undefined[]=[undefined, undefined]
const arr3: (number | string)[] = [2, '3', 5]
const arr4: {name: string, age: number} [] = [{name: 'ee', age: 18}]

别名： type
type tager = {name: string, age: number}
const arr4: tager[] = [{name: 'ee', age: 18}]
````

## 元组
01 数组的加强版
02 数组赋值类型必须和定义的类型顺序一样

## 函数返回类型：never 和 void 的区别？
01 never: 函数无法正常返回, 无法终止，或会抛出异常； 表示永远不会有值的一种类型。
02 void: 函数能正常运行; 没有返回值的函数，其返回值类型为void
````
声明 void 类型的变量，只能赋予 undefined 和 null
let unusable: void = undefined;

function({name: string, age: number}): any {
    return null
}

````

## 定义对象的类型 -  接口interface 
01 接口一般首字母大写
02 可以继承
03 只是在开发过程中进行了约束
04 接口可以继承接口
05 接口可以继承类

````
interface Demo {
    name: string,
    age: number,
    sex?: number,
    [propsname: string]: string
}
<!-- 基本使用 -->
let tom:Demo = {
    name: 'sds',
    age: 12
}
<!-- 可选属性 -->
sex?: number

<!-- 任意属性 -->
[propsname: string]: string

<!-- 只读属性 -->
readonly id: number;
````


## 类
01 定义： 定义类一件事物的抽象属性，包含他的属性和方法 （es6之前是构造函数实现类的概念）<br>
02 对象： 类的实例， 通过new 生成<br>
03 es6中： 使用class 定义类， constructor定义构造函数<br>
04 继承： extends关键字实现继承， super关键字调用父类构造函数和方法<br>
05 存储器： setter 和 getter 可以改变属性的赋值和读取行为<br>

+ ts 可以使用三种修饰符public, private, protected<br>
+ + public： 类的内部和类的外部都可以被调用<br>
+ + private: 只能在类的内部使用（该类不允许被继承或者实例化：）<br>
+ + protected: 只能在类的内部使用， 特殊点： 继承时可以使用（该类只允许被继承：）<br>

+ 抽象类是不允许被实例化的：<br>
+ + abstract
+ + 规定要继承的方法


## tsconfig.json
+ 告诉编译器如何编译
+ tsc --init
+ tsc 编译文件生效
+ 生效文件 ｜ 目录参考 { include: ["文件1", "文件2"]}
+ 生效仅文件 { files: ["文件1", "文件2"]}
+ 不生效文件用 { exclude: ["不生效文件1", "不生效文件2"]}
+ compilerOptions: 配置参数
````
compilerOptions: {
    outDir: "./build", // 配置编译后生成的js文件存放目录
    rootDir: "./src", // 配置源ts文件存放目录
    sourceMap: true, // 编译时，生成的信息文件，存储了位置信息，ts文件和js文件的映射
    removeComments: true, // 编译去掉注释
    noUnusedLocals: true, // 定义但没有使用的变量不再进行打包- 控制台会提示
    noUnusedParameters: true, // 定义但没有使用的方法不再进行打包- 控制台会提示
    strict: true, // 书写规范严格模式
    noImplicitAny: true // 一定要设置静态类型 ；strict: false时生效
    strictNullChecks: true // 不允许代码中有null; strict: false时生效
}
````


