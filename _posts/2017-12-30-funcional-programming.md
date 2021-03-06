---
title: 函数式编程
date: 2017-12-30 19:13:38
tags: 编程
---

函数式编程是种编程方式，它将电脑运算视为函数的计算。函数编程语言最重要的基础是λ演算（lambda calculus），而且λ演算的函数可以接受函数当作输入和输出。

## 定义

"函数式编程"是一种"编程范式"（programming paradigm），也就是如何编写程序的方法论。主题思想是把运算过程尽量写成一系列嵌套的函数调用。现在有一个这个样的数学表达式：

```
(1 + 2) * 3 - 4
```

传统的过程式编程写法：

```
var a = 1 + 2; 
var b = a * 3;
var c = b - 4:
``` 

函数式编程要求使用函数，写法如下：

```
var result = subtract(multiply(add(1,2), 3), 4);
```
这就是函数式编程

## 特点
函数式编程有五个鲜明的特点
### 函数是第一等公民
函数和其他数据类型一样，处于平等地位，可以赋值给其他变量，也可以作为参数，传入另一个函数，或者作为别的函数的返回值。

举例来说， 下面代码中的print变量就是一个函数，可以作为另外一个函数的参数。

```
var print = function(i){ console.log(i) }

[1, 2, 3].forEach(print)
```

### 只用“表达式”， 不用“语句”
“表达式（expression）”是一个单纯的运算过程，总是有返回值；“语句”（statement）是执行某种操作，没有返回值。函数式编程要求，只使用表达式，不使用语句。也就是说要求每一步运算都有返回值。

### 没有“副作用”
所谓“副总用”（side effect），指的是函数内部与外部互动，产生的预算以外的其他结果。最典型的情况就是修改全局变量的值。

函数式编程没有“副作用”，意味着函数要保持独立，所有功能就是返回一个新的值，没有其他行为，尤其是不得修改外部变量的值。

### 不修改状态
函数式编程只是返回新的值，不修改系统变量。因此，不修改变量，也是函数式编程的一个重要特性。

在其他语言中，变量往往用来保存“状态”（state）。不修改变量，意味着状态不能保存在变量中。函数式编程使用参数保存状态。最好的例子就是递归。

```
   function reverse(string){
        
        if(string.length == 0){
            
            return string;
            
        }else{
            
            return reverse(string.substring(1, string.length)) +string.substring(0, 1);
                    
        }
    }
    
```

使用递归， 函数式语言的运行速度比较慢，这个它长期不能在业界推广的主要原因。

### 引用透明
引用透明（Referential transparency）,指的是函数的运行不依赖外部变量或“状态”， 只依赖输入的参数， 任何时候只要参数相同， 引用函数所得到的返回值是相同的。


## 意义
函数式编程的好处

### 代码简洁
函数式编程大量使用函数，减少了代码的重复，因此程序比较短，开发速度快。


### 接近自然语言，易于理解
函数式编程的自由度很高，可以写出接近自然语言的代码。

```
subtract(multiply(add(1, 2), 3), 4)

```
对他进行变形，可以得到另外一种写法

```
add(1, 2).multiply(3).subtract(4)

```

这基本就是自然语言的表达了， 再看下面的代码

```
merge([1, 2], [3, 4]).sort().search("2")

```
因此函数式编程更加容易理解


### 更加方便的代码管理
函数式编程不依赖，也不会改变外界的状态， 只要给定输入状态，返回的结果必定相同。因此，每一个函数都可以被看成独立单元，有利于进行单元测试和出错。以及模块化组合。

### 易于“并发编程”
函数式编程不需要考虑死锁，因为它不修改变量， 所以根本不存在锁的问题。不必担心一个线程的数据被另外一个线程修改。所以可以很放心的把工作分摊到多个线程，部署并发编程。

```
var sl = op1();
var s2 = op2()'
var s3 = concat(s1, s2);

```
多核CPU是未来的潮流， 所以函数式编程的这个特性十分重要。

### 代码的热升级
函数式编程没有副作用，只要保证接口不变。内部实现式外部无关的。