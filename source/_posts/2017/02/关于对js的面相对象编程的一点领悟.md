---
title: 关于对js的面相对象编程的一点领悟
tags:
  - js面向对象编程
categories:
  - javascript
date: 2017-02-19 17:21:08
---
一开始，程序员是直接通过new Object()来创建一个对象，再后来就是通过字面量形式定义好所有的对象上的属性和方法

这时候发现创造多个功能一样的对象会重复写很多代码，于是产生了工厂方法，该方法里new一个对象，然后返回该对象。但是该方式的问题是，无法判断对象的类型归属问题，不知道该对象是不是由某对象创造。

于是产生了构造函数方式，函数里使用this，this上绑定属性和方法。这种方式可以使用instanceof关键字解决上面的问题。然而，潜在的问题是，每次new一个对象时，调用this上的方法都是返回的不同的方法的实例，即便功能完全一样。造成不必要的浪费。

最后，推出prototype结合构造函数方式。普遍的做法是，在构造函数的this上定义好属性，然后在原型上定义好方法，这样保证了每次调用的方法是同一个方法。(若在原型上也定义属性，那么该属性将会被所有创造的对象所共享，一般而言是不建议的。构造函数的原型对象会被所有由构造函数创建的对象所共享)
