# 练习实例15

## 题目

利用条件运算符的嵌套来完成此题：学习成绩>=90分的同学用A表示，60-89分之间的用B表示，60分以下的用C表示。

## 分析

本题考查的条件运算符：`?:`。`

## 代码

```c
#include <stdio.h>

int main() {
    float score;// 分数
    char level;// 等级
    printf("请输入分数：\n");
    scanf("%f", &score);

    level = (score >= 90) ? 'A' : (score < 60 ? 'C' : 'B');
    printf("等级：%c", level);
}
```

代码执行结果如下：

```text
请输入分数：
87
等级：B
```