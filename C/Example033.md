# 练习实例33

## 题目

判断一个数字是否为质数。


## 分析

本题考查的知识点：
- 函数
- for 循环语句
- if 条件语句

分析：
- 质数（prime number）又称素数，有无限个。一个大于1的自然数，除了1和它本身外，不能被其他自然数整除。


## 代码

```c
#include <stdio.h>

int isPrime(int num);

int main() {
    // 从键盘输入数
    int num;
    printf("请输入一个数：");
    scanf("%d", &num);

    // 调用函数判断是否是素数
    int result = isPrime(num);

    // 打印结果
    if (result) {
        printf("%d 是素数！", num);
    } else {
        printf("%d 不是素数！", num);
    }
}

/**
 * 判断一个数是否是素数
 * @param num 待判断的数
 * @return 如果是素数则返回1，如果不是素数则返回0
 */
int isPrime(int num) {
    if (num < 2) {
        return 0;
    }
    for (int i = 2; i < num; i++) {
        if (num % i == 0) {
            return 0;
        }
    }
    return 1;
}
```

代码执行结果如下：

```text
请输入一个数：5
5 是素数！
```