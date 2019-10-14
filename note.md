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

### isNaN
     检测数据类型是否是非有效数字如果是就是true反之为false
     在检测数据类型的时候，如果发现数据类型不是number类型的，要把他先转换为数字，再判断
```js
     //用它检测有效数字返回false
     console.log(isNaN(1)) //false
     //用它检测的是非有效数字 返回true
     console.log(isNaN(NaN))//true
```