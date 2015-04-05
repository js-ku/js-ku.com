---
layout: detail_tmp
title: JavaScript 常见问题汇总2
intro: JavaScript 他的设计有很多的问题、或者你也可以叫他'特性'。
categories: JavaScript
keyword: JavaScript变量提升,JavaScript函数提升,JavaScript常见问题
author: li
show_type: image
show_intro: /res/img/page/JavaScript/JavaScript-FAQ.png
tags: [JavaScript]
---

#JavaScript 常见问题汇总2# 

>JavaScript Frequently Asked Questions

>JavaScript 作为一门编程语言，JavaScript 的流行几乎不受他的质量影响。


###1.  NaN###
 `NaN` 在`JavaScript` 中定义的是一个特殊数量值。表示不是一个数字(Not a Number) 
    
    typeof NaN === 'number';// true

 尽管返回值为`true`。
 如果你的运算结果为 `NaN` 那一定是有某一个值为`NaN`。
NaN是一个奇怪的类型。如果你想要检测一个变量是否为`NaN`。`typeof` 是不能分辨 数字的和`NaN`的区别。
 可以使用这样的方法：
    
    NaN == NaN;//false
    NaN === NaN;//false

 在ECMAScript6中提供了一个方法 `isNaN()` 来判断是否为`NaN`
    
    isNaN(NaN);       // true
    isNaN(undefined); // true
    isNaN({});        // true

    isNaN(true);      // false
    isNaN(null);      // false
    isNaN(37);        // false

###2. == 与 ===###
 在`JavaScript`中提供了两组比较的运算符:`==` 相等，`!=` 不等 和 `===` 全等，`!==` 全不等。
`==` 和 `!=` 判断比较的时候，如果类型不同，会试图进行强制类型转换。有些规则很难理解。
`===` 和 `!==` 在判断的时候，如果类型不同会返回`false`。正如所期望的那样.

    '' == '0';  //false
    0 == '';    //true
    '0' == 0; //true

    false == '0'; //false
    false == '';  //false

 如果你觉得上面的不可思议，下面的就更不能理解。

    false == undefined; //false
    false == null;      //false 
    null == undefined;  //true wtf?

 这 `false` 与 `undefined` 和 `null` 在 `==` 比较的时候都是`false`。根据 *传递性* `null` 和 `undefined` 也应该是 `false`
`==` 却违背了 *传递性*。这些让人匪夷所思的问题,在`===` 和 `!==` 身上不会发生。所以建议使用 `===` 和 `!==` 做比较运算。

