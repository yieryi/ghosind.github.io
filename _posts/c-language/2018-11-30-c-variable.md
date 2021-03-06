---
layout: post
title: C语言从零开始0X01：变量与基本运算
date: 2018-11-30
categories: [C]
tags: [C, Tutorial, Getting Start, Variable, Type]
excerpt: 主要介绍C语言中的变量、常量、基本类型以及其基本的运算。
---

## 前言

在拖稿将近两年以后，终于动手把这个坑继续填下去。在写第一篇的时候就只是发在[博客](http://www.ghosind.com/2016/12/29/c-getting-start)上没想会有多少人看，也顺手就备份发在了CSDN上。前段时间上CSDN一看发现第一篇的阅读量已经达到一万多，虽然说对于大佬们来说这只是一个小数目，但是对于一个基本没有存在感的水货来说已经是一种很大的激励了。废话也就不多说，直接进入正题。本章主要是介绍C语言中变量的概念，以及变量的基本类型及其基本运算。

## 变量

关于变量，相信大家都已经非常熟悉，在中学阶段的数学教学中就已经涉及到了代数学中的变量。在这里随手摘抄了苏联数学家菲赫金哥尔兹的著作《微积分学教程》中对于变量的一段描述。

> 在物理学及其他自然科学内读者曾经遇到各种不同的**量**：时间，长度，体积，重量等。任一种量，按照不同的情况，有时具有不同的值，有时仅取一值。在第一种情形我们称它为**变量**，在第二种情形称它为**常量**。
>
> 但在数学上我们不顾所考察的量的物理意义，仅关心于表示这量的数字。...对于我们来说，变量仅为赋予数值的符号（例如，字母x）而已。

与数学中相同，C语言中的变量也是具有值的一种量，他们同样拥有值以及对应的符号。但与数学中不同的是，C语言中的变量的值的类型更为广泛，不再局限于数字。在C语言中，每个变量都拥有对应的类型，例如整数型、浮点型等。变量的符号（变量名）在C语言中也比数学中的符号具有更大的意义。为了使得程序代码更易于阅读，通常变量的名称都会根据用途赋予对应的名称。

关于变量，就可以简单的理解它是一种具有不同形状的容器。每一个容器都有其特定的形状（变量类型），容器内也可以存放不同的物质（值），而为了区别不同的容器，每个容器都有一个独特的标签（变量名）。

在C语言中，所有的变量在使用前需要声明。变量的声明通常位于函数的最前端，任何可执行语句之前（C89规定变量的声明必须位于函数的最前端，而自C99起已经支持在任意位置声明变量，只需要在使用前声明即可）。变量声明时必须指定该变量的类型，格式为`变量类型 变量名;`，例如：

```c
int height;
double weight;

height = 170;
weight = 70.0;
```

如上述所示，声明了两个变量，分别为整数型变量height及双精度浮点型变量weight，并分别赋予了不同的值。在变量声明时，同一类型的变量可在同一行内声明，使用逗号隔开即可，格式为`变量类型 变量名1, 变量名2;`。但在使用这种格式声明变量且进行初始化时，仅有赋值的变量进行了初始化。如`int length, width = 10;`中，仅有`width`被赋予了值，而`length`并未进行初始化。

### 基本类型

C语言提供的基本类型主要有（表中位数以64位MacOS为例）：

|类型|说明|位数|
|:---:|---|:--:|
|char|字符型，占一个字节，通常用来存放ASCII字符|1|
|int|整型，用于存放整数数值|4|
|float|单精度浮点型，用于存放浮点数数值|4|
|double|双精度浮点型，与float相同，可存放浮点数数值，精度高于float|8|

如上表所述，基本类型大致可以分为整型和浮点型两种（char是一种较为特殊的整型）。整型只能用于表示整数，不能有小数部分；浮点型可以用来以近似的方式表示在允许范围内的任意的实数，包括整数及包含小数的实数。不同的类型一般占用不同的位数，用于表示不同长度要求的数值。例如无符号char类型占用8位，可表示的数值范围为$ 0 \sim 255 $之间。float与double分别能表达的范围为$ -3.4 \times 10^{38} \sim 3.4 \times 10^{38} $及$ -1.79 \times 10^{308} \sim 1.79 \times 10^{308} $。关于浮点数在此处便不仔细讨论，继续介绍C语言本身。

除上述四个基本类型以外，C语言还提供了几个限定符。首先，C语言中引入了short和long两个限定符，提供了对于不同长度的类型的支持。如在64位Mac OS中，short为2个字节，int为4个字节，long为8个字节。当short与long限定符用于限定int类型时，声明中的int可省略。long限定符除了可以限定int类型外，还可用于double类型，表示高精度的浮点类型，它的范围大约为$ -1.2 \times 10^{4932} \sim 1.2 \times 10^{4932} $。

除short和long以外，还有signed和unsigned限定符，它们分别代表有符号数值和无符号数值，可用于限定任何整数与浮点数类型。无符号类型总是正值或者0，有符号类型可以是正值、0以及负值。例如char类型，unsigned char的取值范围为$ 0 \sim 255 $，signed char取值范围为$ -128 \sim 127 $。

### 命名规则

在C语言中，变量的名称必须为字母、数字或下划线组成，且首字符必须为字母或下划线，不能为数字。字母大小写敏感，如x与X为两个不同的变量。另外，C语言中诸如int、float、if、return等关键字都是保留给语言本身使用的，具体的关键字列表将在下方给出。在C89中规定了编译器对于变量名称长度的支持至少为31，并在C99中增加到63。一般来说，建议变量使用有意义的名称，以提高可读性，也避免与其它变量混淆。传统的C语言变量名称规范为变量使用小写字母，常量使用大写字母，而非采用其它语言中常见的驼峰命名法。关于变量命名的规则，不同的开发场景下可能有不同的习惯规定，可根据具体编程规范进行调整。

#### 关键字

在C89（即ANSI C）中一共规定了32个关键字，C99中新增了5个关键字，C11中新增了7个关键字。

|C89关键字列表|||
|:---:|:---:|:---:|:---:|
|auto|double|int|struct|
|break|else|long|switch|
|case|enum|register|typedef|
|char|extern|return|union|
|const|float|short|unsigned|
|continue|for|signed|void|
|default|goto|sizeof|volatile|
|do|if|static|while|

|C99新增关键字|||
|:---:|:---:|:---:|:---:|
|inline|restrict|_Bool|_Complex|
|_Imaginary|||

|C11新增关键字|||
|:---:|:---:|:---:|:---:|
|_Alignas|_Alignof|_Atomic|_Static_assert|
|_Noreturn|_Thread_local|_Generic||

### 初始化

变量的初始化即在声明时就赋予该变量一个值，它的格式为`变量类型 变量名 = 值;`。例如：

```c
int height = 170;
double weight = 70.0;
```

若一个变量不进行初始化，在赋值前它的值将会是不确定的。所以为了避免直接使用未初始化的变量造成未知的错误，尽量在声明时就进行初始化。现在的编译器通常会在编译过程中检查是否存在未初始化就使用的变量，若存在则给出一个warning的警告，提醒程序员存在未初始化的变量。部分IDE也支持检查代码中未初始化变量的功能。

## 常量

正如同名称所示，变量是在声明后可以改变的量，而常量则就是不可改变的量。例如在表达式直接使用数值，该数值就是一个常量。在实际使用中，直接在表达式中使用数值可能会导致维护困难，这时候就可以使用宏定义的定义字符常量。定义字符常量的方式是使用`#define`指令，它的格式为`#define 名称 替换的内容`，它的替换内容不仅仅是数字，也可以是其它任意内容。宏定义在程序预处理时会被替换成我们需要的内容。

还有一种常量的定义使用const限定符，如`const double G = 6.67e-7;`即声明了一个不可更改的变量G。试图修改const限定符限定的变量的结果依具体的编译器而定，如使用gcc-8将在编译时产生一个错误。但它也不是绝对不可修改的，所以当需要使用常量时需要根据具体情况考虑声明方式。

## 运算与赋值

在C语言表达式中，等号左侧的变量将被赋予值，右侧是被赋予的值。且等号右侧可以是常数、变量或是表达式，而右侧只能是一个变量，且需为相同的类型（部分情况下将被自动转换）。

C语言可以使用`+`、`-`、`*`、`/`运算符完成数学中的四则运算，并支持使用`%`进行取模运算（即取除法时的余数）。下面是一个简单的摄氏度转换为华氏度的例子。

```c
double celsius = 30.0;
double fahr = 0;

fahr = celsius * 9.0 / 5.0 + 32.0;

printf("%.2lf - %.2lf\n", celsius, fahr);
// 30.00 - 86.00
```

## 结束语

本章简单介绍了C语言中的整数、浮点数类型，变量与常量，以及其基本的四则运算及赋值。当写完文章第一个版本时，介绍的内容还比较粗糙，后续也将会以更新的方式修改文章并加入一些内容。下一章的安排为简单介绍C语言中的控制流。

## 参考资料

Brian W. Kernighan, Dennis M. Ritchie. *The C Programming Language (2nd Edition)*.