# JS是一种客户端语言
> js是一种客户端语言，他不仅要操作dom对象，还要操作浏览器的某些功能
- ECMAScript ES3/5 (老版本规范) ES6/7(新语法规范)：他提供了变量，语法，操作语句等
- DOM （document object model）：他提供了一些js的属性和方法，用来操做页面当中的dom元素
- BOM （browser object model）：他提供了一些js属性和方法，用来操作浏览器

# js中的变量
- let      （ES6的语法。创建一个变量，不能重复创建同一个变量）
- var      (可以重复创建)
- function fn(){} 函数创建变量
- const 创建常量（不允许被修改，ES6）
- class F{}
- import f from '../a.css'(ES6的语法，导入)
- Symbol 创建唯一值

# js的命名规范
- 严格区分大小写
- 变量名由数字字母下划线$组成，不能以数字开头
- 不能以关键字或者保留字作为变量
- 变量遵循驼峰命名法（变量第一个单词开头小写，以后每一个有意义的单词开头大写）

> class/name/add/delete/update/get/set

# js中的数据类型
- 基本数据类型
    + number  12 NaN
    + string 单引号、双引号  ``(ES6模板字符串)
    + boolean false、true
    + null 空指针对象
    + undefined 未定义
- 引用数据类型
    + object 对象
        + 普通对象 {name:'xxx', age:11}
        + 数组 [18,'刘德华']
        + Math
        + Date
        + /^$/

    + function

# number 数据类型
> NaN（not a number）  有效数字

- NaN：和任何值都不相等（包括自己）

- 把数据类型转换为数字类型（number） Number(val) 

## 把字符串转换为数字
> 只要字符串出现了非有效数字，那就是NaN（第一个小数点不算）

> 空字符串转数字是0

```
console.log(Number('15')) => 15
console.log(Number('15px')) => NaN
console.log(Number('')) => 0
console.log(Number('   ')) => 0
console.log(Number('13.5')) => 13.5
console.log(Number('13.4.5')) =>NaN
console.log(Number('.5')) => 0.5
```
## 把布尔转数字

```
console.log( Number(true) ) => 1
console.log(Number(false)) => 0
```

## 把null和undefined转数字

```
console.log(Number(null))=> 0
console.log(Number(undefined)) =>NaN
```

## 对象转数字
 > 先把对象转字符串，然后在把字符串转数字

 - {} 转字符串(不管里边有没有东西) => '[object Object]'
    ```
    {}.toString() => '[object Object]'
    {name:'xxx'}.toString() => '[object Object]'
    ```

 - [] 转字符串=>把左右两边的中括号去掉，然后加上引号

    ```
    [].toString() => '' (空字符串)
    [1,2].toString() =>'1,2'
    ```

    ```
    Number({}) =>NaN
    {}.toString()=>'[xxxx]'=>NaN

    Number({name: 'xxx'})
    {}.toString()=>'[xxxx]'=>NaN

    Number([])
    [].toString()=> '' =>0

    Number([1,2])
    [1,2].toString()=> '1,2'=>NaN
    ```

    ```
    Number({name: {name:'xxx'} }) =>NaN
    Number('3.1415926') => 3.1415926
    Number([]) =>0
    Number([12.31415926]) => '12.31415926' => 12.31415926
    Number( Number(false) )
    Number( 0 ) =>0

    Number( Number( Number(true) ) ) =>1
    Number( Number(undefined) ) =>NaN

    Number(null) // 0
    Number(undefined) // NaN
    Number(true) // 1
    Number(false) // 0

    ```
## isNaN
 > 判断你要检测的数据值是否是一个非有效数字，如果是非有效数字就是true，反之就是false

 - 检测是值是不是一个有效数字，如果是有效数字就是fasle，反之就是true

 > 如果检测的值不是number类型，就把那个值先转为number类型，在判断

 ```
    isNaN(1) // false
    isNaN(NaN) // =true

    isNaN('13px') // true
    isNaN(true) // false
    isNaN(false) // false
    isNaN(null) // false
    isNaN(undefined) // true
    isNaN({}) //true
    isNaN([1,2]) // true

    isNaN( Number(false) ) // false
 ```

 ## parseInt 转数字  parseFloat

 > 他是从左往右依次查找，一旦遇到非有效数字，就立即停止，把数字返回

 > 如果把数组转数字，那就看数组的第一项， 从左往右依次查找，一旦遇到非有效数字，就立即停止，把数字返回

 > parseFloat 可以识别一位小数点

 ```
 parseInt(1.2); // 1
 parseInt(3.1415926) // 3
 parseInt('3.1415926') // 3
 parseInt('3px') // 3
 parseInt([3.12, '20']) // 3
 parseFloat([3.12, '20']) // 3.12
 parseInt('px12')  // NaN
 parseInt(null) // NaN
 parseInt(null) // NaN
 parseInt(undefined) // NaN
 parseInt(false) // NaN
 parseInt(true) // NaN
 
 parseFloat('3.13.12') // 3.13
 parseFloat('3.12px') // 3.12
 ```

# string字符串类型
 > 用单引号、双引号、反引号（``）【ES6的模板字符串】
 - 把别的数据类型转换为string类型（val.toString();字符串拼接）
 ## val.toString()
    + 把对象转字符串 => '[object Objtct]'
    + 把数组转换为字符串 : 把数组的中括号去掉，然后加上引号
    + 数字、布尔转字符串是直接加引号
    + null和undefined不能直接调用toString方法，他会报错（可以使用字符串拼接）

    ```
    ({}).toString() // '[object Object]'
    [].toString() // ''
    (23).toString() // '23'
    true.toString() // 'true'
    false.toString() // 'false'
    ```
## 四则运算（加法有可能出现字符串拼接）
- 在四则运算中包括加减乘除，除了加法，其他的都是正常科学运算，

- 加法就有可能出现字符串拼接，如果在加法中出现了字符串，那就不是数学运算，就是字符串拼接
- 如果在运算中出现了不是数字类型的值，先把值转换为数字类型的，在运算
- 在转换的时候遇到字符串，就直接拼接
- 运算过程当中出现NaN，结果就是NaN
- 在拼接过程中如果有数组或者普通对象，要给他转数字

-*/ paseInt paseFloat Number 
```
console.log('10' + 10) // '1010'
console.log('10' - 10) // 0
console.log('10px' - 10) // NaN
console.log( [] + []) // => '' + []=> '' + ''
console.log('12px'*0) // NaN
console.log([] + false) // ''+ false=>'fasle'
    console.log([31415926] + {name: 31415926})
    // '31415926' +{name: 34151926} =>'31415926'+ '[object Object]'

console.log(1 + null + false + '珠峰' + [] + null + undefined)
    // 1+0 =>1+0=>'1珠峰'=> '1珠峰' =>'1珠峰null'=>'1珠峰nullundefined'

console.log(1 + true + [] + false + [12] + null)
// 1+ 1=>2+ ''=>'2false'=>'2false12'=>'2false12null'

console.log(undefined+1+null+false+'珠峰'+[]+null)
            // NaN+1=>NaN + 'NaN珠峰null'
            // NaN+1=>NaN+0=>NaN+0=>NaN+'珠峰'=>'NaN珠峰'+ ''=>'NaN珠峰' + null=> 'NaN珠峰null'
```

## boolean 布尔
> false/true
- Boolean
- !/!!
- if判断

### Boolean
- 其他数据类型转布尔有且只有null、undefined、0、''、NaN是false，其余都是true，没有意外

```
    Boolean(null) // false
    Boolean(undefined) // false
    Boolean('') // false
    Boolean(0) // false
    Boolean(NaN) // false
    Boolean(false) // false
    Boolean('   ') // true
```
 
### !和!!
 - 取反：先把值把转布尔之后在取反
 ```
 !'' // true
 !null // true
 ! undefined //true

 ```
 - !! 先把值把转布尔之后取反再取反（转布尔）

 ```
 !!1 // true
 !!'' // false
 !! NaN // false
 ```

### if条件判断
> 如果判断的条件转布尔是true，就执行大括号里的代码，如果是false就不执行
```
// 大括号里的值会转布尔，如果括号里布尔是true就执行大括号里的东西（大括号里的值就是判断条件）
if('1'){
    console.log('xxx')
}
```

### null和undefined
    > null和undefined代表空
#### null
 - 是意料之中的（一般我们开始不知道值，我们先手动这只为null，后期再给予赋值操作）

 ```
 let num = null;(num一开始没有值，但是经过一系列js逻辑操作之后再给他赋值)

  num  = 12

// 例如我们的汽车，一开始没有汽油【相当于let num = null】，但是我以后肯定会加油的（这是我意料之中的事）,那以后加油时就是赋值【num = 12】
 ```
 #### undefined
  - 意料之外（不是我能决定的，一般是默认机制）
    
    + 出现undefined的情况

        + 对象中，获取属性名对应的属性值不存在就是undefined
        + 函数中没有给形参赋值，那在函数体中获取形参变量就是undefined
        + 函数中没有返回值（return）那函数执行返回结果就是unedfined
        + 创建一个变量，没有赋值，那么获取这个变量是undefined
    
  ```
    //  举个例子：那么孙悟空的父亲，我们现在大家公认的就是没有，他是石头缝里出来的，那他的父亲就是undefined；
    猪无能我们知道它是有父亲的，但是我们现在还不能确定是哪一头猪，所以现在他的父亲就是null，但是以后经过我们的打听，我们知道了，它的父亲是隔壁村小花，那么这时我们再把它的父亲赋值为'xiaohua'
  ```


## object的普通对象

任何一个对象外层由大括号包裹，由0到多组键值对组成，键值对之间拿逗号隔开，每一个键值对由属性名和属性值组成，属性名由字符串或者数字组成
属性名不能重复，如果重复会覆盖前面的

查找属性：对象.属性名 对象['属性名']，如果属性名是数字，不能用对象.属性名去取

新增键值对：对象.属性名 = xxx（如果获取的这个特属性名就是修改，如果没有就是新增）

删除：　假删除＝》手动赋值为null 真删除=》delete 对象.属性名
 
 如果查找属性名对应的属性值不存在  就是undefined

 ## 数组
    外层由中括号包裹 [1,1.1]



## 数据类型比较
 =    赋值
 ==   比较（进行数据类型转换）
 !=   不等（进行数据类型转换）
 ===  绝对比较（不进行数据类型转换）
 !=== 绝对不相等（不进行数据类型转换）

 对象 == 对象 比较空间地址（永远不相等）
 对象 == 数字 对象转数字在比较
 对象 == 字符串 把对象转换为字符串在比较
 对象 == 布尔 会把两边全部转数字在进行比较
 数字 == 字符串 会把字符串转数字再比较
 数字 == 布尔 把布尔转数字进行比较
 字符串 == 布尔 把两边全部转换为数字在进行比较

 null == undefined
 null和其他值都不想等（undefined也是）


 ## 逻辑运算符
- %模 (取余数)
    i++（先取值后运算）
    ++i（先运算后取值）
    -=/+=（自增）

## js操作的语句（循环、判断语句）
- if/else if /else
- 三元运算符
- switch case


### if/else if/else

```js
    //判断的条件回转布尔
    //如果有一个条件成立，别的条件不管成立不成立都不执行了
    if(判断的条件){
        执行的代码
    }
    else if(判断的条件){

    }
    else{
        如果以上条件都不成立就走else里的代码
    }

``` 
### 三元运算符
    判断的条件?如果条件成立处理的事情 : 如果条件不成立处理的事情 

## 数据类型的检测
- typeof 检测数据类型的属性（不是方法）
- instanceof  检测当前实例是否属于某个类
- constructor 基于构造函数检测数据类型
-  Object。prototype。toString.call()检测数据类型最好的方法

## typeof
- 检测的返回值一定是一个字符串
- 字符串里放的是检测出来的类型
- typrof null => 'object'
- 检测对象返回都是'object'不能够详细区分数组和普通对象

## 循环
- for
- while
- for in
- for of(ES6)

## for
> 重复的做某一件事

- 创建循环的初始值
- (设置)判断循环的执行的条件
- 执行循环体中的内容
- 当前循环结束，进行步长累计操作
- continue:结束当前轮循环（continue后面的代码不执行）
- break：结束整个循环（break后面的不再执行）

## 函数
> 函数就是一个方法或者说是功能体，他把实现一些功能的代码封装到一起，以后如果想执行这个方法，就执行函数就可以了，（可以减少重复的代码提高代码的复用率）【高内聚低耦合】

-
