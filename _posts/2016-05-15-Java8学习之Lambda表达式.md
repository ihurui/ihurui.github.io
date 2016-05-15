---
layout: post
title: "Java8学习之Lambda表达式"
subtitle: ""
date: 2016-05-15 14:23:11
categories: [design, tool]
---

Lambda号称是Java8中最大的特点，来自于函数式编程思想。Java8的学习首先就从它开始了。

## 一、Lambda介绍
lambda的语法表达式如下：
	```
	参数 -> 表达式 
	parameter -> expression
	```
具体的代码栗子：
	```
	(int a, int b) ->  {return a+b;};
```
上面的代码返回了两个整数相加的和。
lambda表达式还有些重要的特征是：
* **可选类型声明**
上面代码中a,b参数的类型声明是可选的，编译器可以自己从参数的值来判断。即
```(a,b)->{return a+b;}```
也是可以的。
* **可选花括号和return关键字**
上面代码中花括号和return关键字也是可选的，因为表达式主体只有一个语句，
```(a,b)->a+b;```
如果不止一句，还是需要大括号的。


多么简洁是吧，简洁大概就是lambda最大的优点了，减少了复杂代码的编写，使代码看上去更优雅更有逼格。（但是对一些不熟悉lambda的程序员来阅读呢，可读性大大减弱了吧。。。）

## 二、完整的代码示例
```
public class Java8Tester {
    interface MathOperation{int operate(int a,int b);}
    interface PrintMessage{void print(String message);}

    public static void main(String[] args) {
        MathOperation addition = ( a,b) -> a+b;
        MathOperation subtraction = (int a,int b) ->{return a-b;};
        MathOperation multiplication = ( a,b) ->  a*b;
        MathOperation division = (int a, int b) -> a/b;

        System.out.println("3+4 ="+addition.operate(3,4));
        System.out.println("5-1 ="+subtraction.operate(5,1));
        System.out.println("3*4 ="+multiplication.operate(3,4));
        System.out.println("15/3 ="+division.operate(15,3));

        PrintMessage printMessage = (String s) -> {
            System.out.println("this is message:" + s);
        };
        printMessage.print("hello world");

    }
}
```
在idea和jdk1.8环境下测试结果如下：
```
	3+4 =7
	5-1 =4
	3*4 =12
	15/3 =5
this is message:hello world
```
## 三、总结
* **lambda表达式主要用于定义内联执行的功能的接口，即只有一个单一的方法接口。在上面的例子中，我们使用不同类型的lambda表达式定义MathOperation接口的operate方法。然后，我们定义PrintMessage的print实现**
* **Lambda表达式消除匿名类的需求，并给出了一个非常简单但功能强大的函数式编程能力。**

