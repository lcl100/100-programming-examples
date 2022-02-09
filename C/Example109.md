# 练习实例109

## 题目

从键盘输入若干个计算机课程期末考试成绩（学生人数可由用户输入），求该课程的期末成绩的平均分并输出。

## 分析

本题考查的知识点：

- 函数
- `printf`函数和`scanf`函数
- for 循环语句
- 浮点数

分析：

- 通过键盘接收同学个数。
- 调用求平均分函数。函数中通过 for 循环获取每个学生输入的成绩，并记入总分，然后通过总分和学生人数求得平均分。
- 输出平均成绩。

## 代码

```c
#include <stdio.h>

float avg(int num);

int main() {
    // 从键盘输入若干个同学的期末考试成绩
    int num;
    printf("请输入学生人数：");
    scanf("%d", &num);

    // 调用函数计算平均分
    float avgScore;
    avgScore = avg(num);
    printf("平均分：%f", avgScore);
}

float avg(int num) {
    // 循环输入学生成绩并统计总分
    float sum = 0;// 记录总分
    float score;
    printf("请输入 %d 个学生的成绩：", num);
    for (int i = 0; i < num; i++) {
        scanf("%f", &score);
        sum += score;// 统计总分
    }
    return sum / num;// 返回计算的平均分
}
```

代码执行结果如下：

```text
请输入学生人数：3
请输入 3 个学生的成绩：12 56 98
平均分：55.333332
```