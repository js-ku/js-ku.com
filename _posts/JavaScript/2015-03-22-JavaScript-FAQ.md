---
layout: detail_tmp
title: JavaScript 常见问题汇总
intro: JavaScript 他的设计有很多的问题、或者你也可以叫他'特性'。
categories: JavaScript
keyword: JavaScript变量提升,JavaScript函数提升,JavaScript常见问题
author: li
show_type: image
show_intro: /res/img/page/JavaScript/JavaScript-FAQ.png
tags: [JavaScript]
---

#JavaScript 常见问题汇总# 

>JavaScript Frequently Asked Questions

>JavaScript 作为一门编程语言，JavaScript 的流行几乎不受他的质量影响。


###1.  作用域###
 `JavaScript` 没有块级作用域。在其他编程语言中(`c`、`java`..)，一个代码块(`{}`)会创造一个作用域，在这个作用域声明的变量在外部是不可见的。
因为`JavaScript` 不存在块级作用域。所以在函数中，代码块内外声明的变量都是可见的。 在其他编程语言中，变量总是在使用之前就乎其去声明，但是在`JavaScript`中
确是在函数开始时声明变量。

###2. 自动插入分号###
    
    function test1(obj){
        return 
        {
            name:obj.name
        }
    };
    var o = {name:'js-ku'};
    test1(o)

结果是什么呢：`undefined`.
 因为 `JavaScript` 有个自动修复机制，没有以分号结尾时，他会自作聪明插入分号来修复程序。
所以上面的代码的 `return;` 没有返回值，就是 `undefined`。把 花括号 放在return 后。就可以避免这个问题。 

###4.typeof ###
 `typeof` 运算符返回一个识别其类型的字符串；

例如：

    typeof 98.9 // 'number'
    typeof 'asd' // 'string'

但是：

    typeof null // 'object' wtf?
    typeof NaN // 'number' wtf?

如果你想判断是 `null` 可以这样：

    null_var === null //true

如果想判断为对象且不为空：

    object&& typeof object == 'object' //true

如果你想判断 `NaN`：

    NaN_var === NaN_var //NaN 就是一个连自己都不相等的东西。 

###5.parseInt ###
 `parseInt` 函数 可以把字符串转换为整数的函数，他在遇到一个 非数字 时会停止转换。
 所以：

    parseInt("123@123"); //123
    parseInt("asdasd");  //NaN

如果我们传入的参数不是 `string` 类型，会先调用 `String()`

    String(0.0000008);  //'8e-7'

可想而知如果

    parseInt(0.0000008)；//8

###6. + 加 ###
 + 既是加法操作符,同时也是字符串连接符。他什么时候是加什么时候连接字符串、取决于参数的类型。
 使用 `+` 前 注意保证类型一致性。否则 你得到的结果不是你想要的。

 如果两个或多个值中 有一个为字符串，既是为空。会把其他的不是`string`的类型转换为字符串，然后连接再一起。

 如果都是数字，返回他们的和。
