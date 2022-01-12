# 练习实例25

## 题目

求1+2!+3!+...+20!的和。

## 分析

由于阶乘的数会非常大，所以需要使用`long double`型。

注意：如果是在Windows下使用MinGW编译运行，那么输出`long double`值会出问题，所以使用`__mingw_printf()`
打印。更多请参考：[C语言关于long double在Windows下输出错误的问题](https://www.cnblogs.com/xh90416/p/14201035.html)

## 代码

```c
#include <stdio.h>

/**
 * 计算指定数的阶乘
 * @param num 指定数
 * @return 阶乘结果
 */
long double factorial(int num) {
    long double result = 1;
    for (int i = num; i >= 1; i--) {
        result *= i;
    }
    return result;
}

int main() {
    // 计算1+2!+3!+...+20!累加的和
    long double sum = 0;
    for (int i = 20; i >= 1; i--) {
        sum += factorial(i);
    }
    // __mingw_printf("1+2!+3!+...+20!=%Lf\n", sum);
    printf("1+2!+3!+...+20!=%Lf\n", sum);
}
```

代码执行结果如下：

```text
1+2!+3!+...+20!=2561327494111820313.000000
```