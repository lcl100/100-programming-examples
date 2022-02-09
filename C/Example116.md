# 练习实例116

## 题目

从键盘输入一个 0~6 的整数，转换成星期输出。

## 分析

本题考查的知识点：

- `printf`和`scanf`函数
- switch...case 语句

分析：

- 从键盘输入一个整数。
- 然后通过 switch...case 语句来判断输入的整数对应的星期数并输出。

## 代码

```c
#include <stdio.h>

int main() {
    // 输入一个整数
    int num;
    printf("请输入一个 0~6 的整数：");
    scanf("%d", &num);

    // 使用switch语句判断星期
    switch (num) {
        case 0:
            printf("Sunday");
            break;
        case 1:
            printf("Monday");
            break;
        case 2:
            printf("Tuesday");
            break;
        case 3:
            printf("Wednesday");
            break;
        case 4:
            printf("Thursday");
            break;
        case 5:
            printf("Friday");
            break;
        case 6:
            printf("Saturday");
            break;
        default:
            printf("请输入一个 0~6 的整数");
    }
}
```

代码执行结果如下：

```text
请输入一个 0~6 的整数：3
Wednesday
```