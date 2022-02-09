# 练习实例114

## 题目

求自然数 1~10 之和。

## 分析

本题考查的知识点：

- while 循环

分析：

- 即利用while循环来求和，当然也可以使用 for 或者 do...while 循环。

## 代码

```c
#include <stdio.h>

int main() {
    int sum = 0;
    int i = 1;
    while (i <= 10) {
        sum += i;
        i++;
    }
    printf("自然数 1~10 之和为：%d", sum);
}
```

代码执行结果如下：

```text
自然数 1~10 之和为：55
```