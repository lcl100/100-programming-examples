# 练习实例113

## 题目

比较两个数的大小。如果 x 大于 y，则输出：x>y，否则输出：x<y。

## 分析

本题考查的知识点：

- `printf`和`scanf`函数
- if 条件语句

分析：

- 使用`scanf`函数输入两个数
- 然后使用 if...else... 语句来判断大小并输出不同的结果

## 代码

```c
#include <stdio.h>

int main() {
    int x, y;
    // 从键盘输入两个数
    printf("请输入两个数：");
    scanf("%d%d", &x, &y);
    // 使用if语句比较大小
    if (x > y) {
        printf("x>y");
    } else {
        printf("x<y");
    }
}
```

代码执行结果如下：

```text
请输入两个数：3 5
x<y
```