# 练习实例12

## 题目

判断 101 到 200 之间的素数。

## 分析

素数就是只能被1和它本身整除的数。

## 代码

```c
#include <stdio.h>

/**
 * 判断指定数是否是素数
 * 素数只能被1和它自身整除，所以循环[2,number-1]之间的所有数，如果能被整除则表示不是素数
 * @param number 待判断的数
 * @return 如果是素数则返回1；如果不是素数则返回0
 */
int isPrimeNumber(int number) {
    // [2, number-1]是为了排除1和它本身
    for (int i = 2; i <= number - 1; i++) {
        // 判断能否被整除
        if (number % i == 0) {
            return 0;
        }
    }
    return 1;
}

int main() {
    int count = 1;
    for (int i = 101; i <= 200; i++) {
        // 判断是否是素数
        if (isPrimeNumber(i)) {
            printf("%d\t", i);
            // 每五个换一次行
            if (count % 5 == 0) {
                printf("\n");
            }
            count++;
        }
    }
}
```

代码执行结果如下：

```text
101     103     107     109     113
127     131     137     139     149
151     157     163     167     173
179     181     191     193     197
199
```