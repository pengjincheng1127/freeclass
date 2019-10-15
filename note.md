# 第一天

## 浏览器

- webkit内核(V8引擎)
    + 谷歌Chrome
    + Safari
    + Opera >=V14
    + 国产浏览器
    + 手机浏览器
    + 。。。
- Gecko 
    + 火狐Firefox
- Presto 
    + Opera <V14
- Trident 
    + IE
    + IE EDGE 开始采用双内核(其中包括Chrome迷你) 


## JS 
     js作为客户端的一种语言，不仅要做操作dom对象，还要操作浏览器的某些功能

- ECMAScript ： 规定了js的语法，变量，操作语句
- DOM：文档对象模型（document object model）：提供了一些js的语法和功能来操作页面中的DOM元素
- BOM（browser object model）浏览器对象模型：提供了一些js的语法和功能来操作浏览器

## JS中的变量
- let 创建变量：不能重复创建一样变量
- var 创建变量 
- const 创建常量，不允许被修改
- function 创建函数变量
- class 创建类
- import 导入
- Symbol 创建唯一值

## js中创建变量的命名规范
- 严格区分大小写
- 由数字、字母、下划线、$组成，但是不能以数字开头
- 不能以保留字或者关键字作为变量名
- 变量名遵循驼峰命名法(变量名的开头第一个单词的首字母开头小写，以后每一个有意义的单词开头的首字母都大写)

## js中的数据类型

- 基本数据类型
     + number 数字
     + string  字符串
     + boolean 布尔值
     + null    空指针对象
     + undefined    未定义
     + Symbol  唯一值
     
- 引用数据类型
     + object  对象数据类型
          + { }
          + [ ]
          + Math
          + 正则
          + Date
     + function 函数

## 基本数据类型
### number
> 包括NaN和有效数字

- 把值转换为数字（Number(val)） 
>  规律：只要字符串中出现了非有效数字，那么结果就是NaN（第一个小数点不算）
- 空字符串转数字为0
### 把布尔值转换为数字
```js
     console.log(Number(true));//1
     console.log(Number(false));//0     
```
### null和undefined转换为数字
```js
     console.log(Number(null))//0
     console.log(Number(undefined))//NaN
```

### NaN转数字
```js
     console.log(Number(NaN))//NaN
```

### 引用数据类型转数字
     普通对象、数组转数字，是先把对象或者数组转为字符串，然后在转数字
```js
     console.log(Number({}))//NaN
```
### 数组转数字
     数组转字符串就把外层的[]去掉，然后那里面的内容加字符串
     空数组转字符串是 '' 再转number是0
```js
     console.log(Number([]))//0
     console.log(Number([12,12]))//NaN
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

  ```
    //  举个例子：那么孙悟空的父亲，我们现在大家公认的就是没有，他是石头缝里出来的，那他的父亲就是undefined；
    猪无能我们知道它是有父亲的，但是我们现在还不能确定是哪一头猪，所以现在他的父亲就是null，但是以后经过我们的打听，我们知道了，它的父亲是隔壁村小花，那么这时我们再把它的父亲赋值为'xiaohua'
  ```




