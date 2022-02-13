# 练习实例44

## 题目

学习使用如何调用外部函数。

## 分析

本题考查的知识点：
- 函数

分析：
- 本题考查的是函数的定义和使用。


## 代码

```c
#include <stdio.h>

int add(int x, int y) {
    return x + y;
}

int main() {
    int result = add(10, 5);
    printf("%d + %d = %d", 10, 5, result);
}
```

代码执行结果如下：

```text
10 + 5 = 15
```