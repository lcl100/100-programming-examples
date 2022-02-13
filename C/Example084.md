# 练习实例84

## 题目

一个偶数总能表示为两个素数之和。


## 分析

本题考查的知识点：
- 函数
- `printf`和`scanf`函数
- if 条件语句
- while 循环语句

分析：
- 输入一个偶数，来寻找它是否由两个素数之和组成。
- 素数是指只能被 1 和本身整除的数。
- 第一步，循环从 [2, num) 之间的所有素数，然后用 num 减去这个素数，得到另外一个数，如果这个数也是素数则表示找到了该偶数可以有两个素数之和组成，则输出结果。


## 代码

```c
#include <stdio.h>

int isPrime(int num);

int main() {
    int num;
    printf("请输入一个偶数：");
    scanf("%d", &num);
    if (num % 2 != 0) {
        printf("请输入一个偶数！");
        return 0;
    }

    // 搜索两个数是素数并且之和等于num
    for (int i = 2; i < num; i++) {
        if (isPrime(i)) {
            // 如果 i 是素数，那么直接用 num 来计算另外一个数
            int n = num - i;
            // 如果计算出来的这个数也是素数则输出结果
            if (isPrime(n)) {
                printf("%d + %d = %d\n", i, n, num);
            }
        }
    }
}

/**
 * 判断一个数是否是素数
 * @param num 待判断的数
 * @return 如果是素数则返回1，否则返回0
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
请输入一个偶数：24
5 + 19 = 24
7 + 17 = 24
11 + 13 = 24
13 + 11 = 24
17 + 7 = 24
19 + 5 = 24
```