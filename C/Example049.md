# 练习实例49

## 题目

`#if`、`#ifdef`和`#ifndef`的综合应用。


## 分析

本题考查的知识点：
- 预处理命令

分析：

预处理程序提供了条件编译的功能。可以按不同的条件去编译不同的程序部分，因而产生不同的目标代码文件，这对于程序的移植和调试是很有用的。类似于if语句，满足条件才会执行对应的语句块。

- 第一种形式

基本语法如下：

```c
#ifdef 标识符
	程序段1
#else
	程序段2
#endif

// 可以省略#else

#ifdef 标识符
	程序段
#endif
```

功能：如果标识符已被`#define`命令定义过则对程序段1进行编译；否则对程序段2进行编译。

示例：

```c
#include <stdio.h>

#define true 1

int main() {
#ifdef true
    printf("true");
#else
    printf("false");
#endif
}
```

- 第二种形式

基本语法如下：

```c
#ifndef 标识符
	程序段1
#else
    程序段2
#endif
```

功能：如果标识符未被#define命令定义过则对程序段1进行编译，否则对程序段2进行编译。这与第一种形式的功能正相反。

示例：

```c
#include <stdio.h>

#define true 1

int main() {
#ifndef true
    printf("true");
#else
    printf("false");
#endif
}
```

- 第三种形式

基本语法如下：

```c
#if 常量表达式
	程序段1
#else
    程序段2
#endif
```

功能：如果常量表达式的值为真(非0)，则对程序段1进行编译，否则对程序段2进行编译。

示例：

```c
#include <stdio.h>

#define R 1

int main() {
    float c, r, s;
    printf("input a number:  ");
    scanf("%f", &c);

#if R
    r = 3.14159 * c * c;
    printf("area of round is: %f\n", r);
#else
    s=c*c;
    printf("area of square is: %f\n",s);
#endif
}
```

为什么要用条件编译：上面介绍的条件编译当然也可以用条件语句来实现，但是用条件语句将会对整个源程序进行编译，生成的目标代码程序很长，而采用条件编译，则根据条件只编译其中的程序段1或程序段2，生成的目标程序较短。如果条件选择的程序段很长，采用条件编译的方法是十分必要的。


## 代码

```c
#include <stdio.h>

#define  R 1
#define true 1

int main() {
    float r = 0;
    int c = 5;
#if R
    r = 3.14159 * c * c;
    printf("area of round is: %f\n", r);
#else
    s = c * c;
    printf("area of square is: %f\n", s);
#endif

#ifdef true
    printf("true\n");
#else
    printf("false\n");
#endif

#ifndef true
    printf("true\n");
#else
    printf("false\n");
#endif
}
```

代码执行结果如下：

```text
area of round is: 78.539749
true
false
```