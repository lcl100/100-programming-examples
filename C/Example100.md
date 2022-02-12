# 练习实例100

## 题目

有五个学生，每个学生有3门课的成绩，从键盘输入以上数据（包括学生号，姓名，三门课成绩），计算出平均成绩，况原有的数据和计算出的平均分数存放在磁盘文件"stud"中。

## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- for 循环语句
- `printf`和`scanf`函数
- 文件操作：`fopen`、`fclose`、`fprintf`函数

分析：
- 本题考查的是如何从键盘读取信息到结构体中，然后再将结构体中的数据写入到文件中。

## 代码

```c
#include<stdio.h>

typedef struct Student {
    int number;// 学号
    char name[4];// 姓名
    float chinese;// 语文成绩
    float math;// 数学成绩
    float english;// 英语成绩
    float avg;// 三门课程的平均成绩
} Stu;

int main() {
    int len = 5;
    Stu students[len];

    // 从键盘输入5个学生的信息
    for (int i = 0; i < len; i++) {
        printf("请输入学号：");
        scanf("%d", &students[i].number);
        printf("请输入姓名：");
        scanf("%s", students[i].name);
        printf("请输入语文成绩：");
        scanf("%f", &students[i].chinese);
        printf("请输入英语成绩：");
        scanf("%f", &students[i].english);
        printf("请输入数学成绩：");
        scanf("%f", &students[i].math);
        float avgScore = (students[i].chinese + students[i].math + students[i].english) / 3;
        students[i].avg = avgScore;
        printf("\n");
    }

    // 打开文件并写入文件
    FILE *fp;
    if ((fp = fopen("stud", "w")) == NULL) {
        printf("打开文件失败！");
        return 0;
    }
    for (int i = 0; i < len; i++) {
        // 循环将结构体数组中的每一项写入到文件中
        fprintf(fp, "%d\t%s\t%.2f\t%.2f\t%.2f\t%.2f\n", students[i].number, students[i].name, students[i].chinese,
                students[i].math, students[i].english, students[i].avg);
    }
    fclose(fp);// 关闭文件
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入语文成绩：67
请输入英语成绩：89
请输入数学成绩：70

请输入学号：102
请输入姓名：jack
请输入语文成绩：89
请输入英语成绩：76
请输入数学成绩：58

请输入学号：103
请输入姓名：liyi
请输入语文成绩：89
请输入英语成绩：99
请输入数学成绩：70

请输入学号：104
请输入姓名：hanmeimei
请输入语文成绩：56
请输入英语成绩：78
请输入数学成绩：89

请输入学号：105
请输入姓名：he
请输入语文成绩：76
请输入英语成绩：89
请输入数学成绩：66

101	tom	67.00	70.00	89.00	75.33
102	jack	89.00	58.00	76.00	74.33
103	liyi	89.00	70.00	99.00	86.00
104	hanm	56.00	89.00	78.00	74.33
105	he	76.00	66.00	89.00	77.00
```