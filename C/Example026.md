# 练习实例

## 题目

利用递归方法求5!。

## 分析

本题考查的是递归函数。

## 代码

```c
#include <stdio.h>

/**
 * 利用阶乘来计算指定数的阶乘
 * @param num 指定数
 * @return 阶乘结果
 */
long factorial(int num) {
    if (num == 0) {
        return 1;
    }
    return num * factorial(num - 1);
}

int main() {
    for (int i = 0; i <= 5; i++) {
        printf("%d!=%ld\n", i, factorial(i));
    }
}
```

代码执行结果如下：

```text
0!=1
1!=1
2!=2
3!=6
4!=24
5!=120
```