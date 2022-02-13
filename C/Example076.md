# 练习实例76

## 题目

编写一个函数，输入n为偶数时，调用函数求`1/2+1/4+...+1/n`，当输入n为奇数时，调用函数`1/1+1/3+...+1/n`(利用指针函数)。


## 分析

本题考查的知识点：
- 函数
- 指针函数
- 奇数与偶数
- for 循环语句
- if 条件语句
- `printf`与`scanf`函数

分析：
- 本题不难，主要考查如何用指针函数来调用函数。


## 代码

```c
#include <stdio.h>

float sum(int n);

int main() {
    // 声明指针函数
    float (*pfun)(int);
    pfun = sum;

    // 从键盘获取数字输入
    int num;
    printf("请输入一个数字：");
    scanf("%d", &num);

    // 调用函数
    float result = (*pfun)(num);
    printf("%.2f", result);
}

float sum(int n) {
    float result = 0;
    if (n % 2 == 0) {// n是偶数
        for (int i = 2; i <= n; i += 2) {
            result += 1.0f / i;
        }
    } else {// n是奇数
        for (int i = 1; i <= n; i += 2) {
            result += 1.0f / i;
        }
    }
    return result;
}
```

代码执行结果如下：

```text
请输入一个数字：2
0.50
```