# 练习实例94

## 题目

猜谜游戏。


## 分析

本题考查的知识点：
- 随机数：`rand()`函数

分析：
- `rand()%10`能够产生一个[0,9]的随机数。对10取余才能将范围限制在10以内。
- 需要死循环，才能让用户不断输入参与判断。

## 代码

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand((int) time(NULL));// 产生变化的随机数
    int random = rand() % 10;// 产生一个[0,9]的随机数
    int num;

    while (1) {
        printf("请输入一个0到9的任意数字：");
        scanf("%d", &num);
        if (num == random) {
            printf("恭喜你，答对了！\n");
            break;
        } else if (num > random) {
            printf("不好意思，你的数大了！\n");
        } else if (num < random) {
            printf("不好意思，你的数小了！\n");
        }
    }
}
```

代码执行结果如下：

```text
请输入一个0到9的任意数字：5
不好意思，你的数大了！
请输入一个0到9的任意数字：3
不好意思，你的数小了！
请输入一个0到9的任意数字：4
恭喜你，答对了！
```