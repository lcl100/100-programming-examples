# 练习实例53

## 题目

学习使用按位异或 ^。


## 分析

本题考查的知识点：
- 位运算

分析：
- 异或运算的规则是：0^0=0; 0^1=1; 1^0=1; 1^1=0。

## 代码

```c
#include <stdio.h>

int main() {
    int a = 5;// 它的二进制是 0000 0101
    int b = a ^ 3;// 进行异或运算，即 0000 0101 ^ 0000 0011 = 0000 0110
    printf("%d", b);// 6
}
```

代码执行结果如下：

```text
6
```