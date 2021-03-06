# 练习实例115

## 题目

从键盘输入10个整数，求奇数之和以及偶数之和。

## 分析

本题考查的知识点：

- for 循环语句
- `printf`和`scanf`函数
- 奇数与偶数的判断

分析：

- 通过循环输入 10 个整数，在输入的同时就判断并且求和。
- 核心是判断一个数是奇数还是偶数，方法就是能被 2 整除的就是偶数，否则就是奇数。

## 代码

```c
#include <stdio.h>

int main() {
    int oddSum = 0, evenSum = 0;// 记录奇数和与偶数和
    int num;// 记录从键盘输入的数

    // 输入10个整数
    printf("请输入 10 个整数：");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &num);
        // 判断奇数或者偶数，然后求和
        if (num % 2 == 0) {
            evenSum += num;
        } else {
            oddSum += num;
        }
    }

    // 打印结果
    printf("奇数和：%d\n偶数和：%d\n", oddSum, evenSum);
}
```

代码执行结果如下：

```text
请输入 10 个整数：1 2 3 4 5 6 7 8 9 10
奇数和：25
偶数和：30
```