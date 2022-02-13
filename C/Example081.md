# 练习实例81

## 题目

`809*??=800*??+9*??`其中`??`代表的两位数, `809*??`为四位数，`8*??`的结果为两位数，`9*??`的结果为 3 位数。求`??`代表的两位数，及`809*??`后的结果。


## 分析

本题考查的知识点：
- for 循环语句
- if 条件语句
- `&&`运算符

分析：
- 本题很简单，多添加几个条件判断即可。

## 代码

```c
#include <stdio.h>

int main() {
    for (int i = 10; i < 100; i++) {
        int left = 809 * i;
        int right = 800 * i + 9 * i;
        if ((left > 999 && left < 10000)
            && (8 * i > 9 && 8 * i < 100)
            && (9 * i > 99 && 9 * i < 1000)
            && left == right) {
            printf("\?\?=%d, 809*\?\?=%d\n", i, 809 * i);
        }
    }
}
```

代码执行结果如下：

```text
??=12, 809*??=9708
```