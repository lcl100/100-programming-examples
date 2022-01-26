# 练习实例104

## 题目

1、定义一个结构体数组，存放10个学生的学号，姓名，三门课的成绩。

2、从键盘输入10个学生的以上内容。

3、输出单门成绩最高的学生的学号、姓名、以及该门课程的成绩。

4、输出三门课程的平均分数最高的学生的学号、姓名及其平均分。

5、将10个学生按照平均分数从高到低进行排序，输出结果，格式如下：

```text
number  name  math  chinese  english  average
103     tom   90    90       90       90
101     jack  65    75       70       70 
```

## 分析

本题考查的是结构体相关的知识。

三门课程单独定义一个`Course`结构体：

```c
struct Course {
    float math;// 数学
    float chinese;// 语文
    float english;// 英语
};
```

而学生单独定义一个结构体，并且包含三门课程这个结构体，而且由于后面要根据平均成绩排序，需要再增加一个`avg`字段保存三门课程的平均分数。

```c
struct Student {
    int number;// 学号
    char name[10];// 姓名
    struct Course course;// 三门课程
    float avg;// 三门课程的平均分数
};
```

排序可以利用冒泡排序来排序结构体数组。

## 代码

```c
#include <stdio.h>

struct Course {
    float math;// 数学
    float chinese;// 语文
    float english;// 英语
};

struct Student {
    int number;// 学号
    char name[10];// 姓名
    struct Course course;// 三门课程
    float avg;// 三门课程的平均分数
};

void sort(struct Student students[], int n);

int main() {
    // 定义一个10个学生的结构体数组
    int count = 10;
    struct Student students[count];

    // 从键盘输入10个学生
    printf("请输入%d个学生的信息：\n", count);
    for (int i = 0; i < count; i++) {
        printf("请输入学号：");
        scanf("%d", &students[i].number);
        printf("请输入姓名：");
        scanf("%s", &students[i].name);
        printf("请输入数学成绩：");
        scanf("%f", &students[i].course.math);
        printf("请输入语文成绩：");
        scanf("%f", &students[i].course.chinese);
        printf("请输入英语成绩：");
        scanf("%f", &students[i].course.english);
        printf("\n");
    }

    // 打印输入的10个学生的信息
    for (int i = 0; i < count; i++) {
        printf("学号：%d\t", students[i].number);
        printf("姓名：%s\t", students[i].name);
        printf("数学成绩：%.1f\t", students[i].course.math);
        printf("语文成绩：%.1f\t", students[i].course.chinese);
        printf("英语成绩：%.1f\n", students[i].course.english);
    }

    // 求得单门成绩最高的学生并打印结果
    float maxMath = students[0].course.math;// 保存数学最高分
    struct Student maxMathStudent = students[0];// 保存数学最高分的学生
    float maxChinese = students[0].course.chinese;// 保存语文最高分
    struct Student maxChineseStudent = students[0];// 保存语文最高分的学生
    float maxEnglish = students[0].course.english;// 保存英语最高分
    struct Student maxEnglishStudent = students[0];// 保存英语最高分的学生
    for (int i = 0; i < count; i++) {
        // 判断数学最高分
        if (students[i].course.math > maxMath) {
            maxMath = students[i].course.math;
            maxMathStudent = students[i];
        }
        // 判断语文最高分
        if (students[i].course.chinese > maxChinese) {
            maxChinese = students[i].course.chinese;
            maxChineseStudent = students[i];
        }
        // 判断英语最高分
        if (students[i].course.english > maxEnglish) {
            maxEnglish = students[i].course.english;
            maxEnglishStudent = students[i];
        }
    }
    printf("数学成绩最高的学生：\n");
    printf("\t学号：%d", maxMathStudent.number);
    printf("\t姓名：%s", maxMathStudent.name);
    printf("\t数学成绩：%.1f\n", maxMathStudent.course.math);
    printf("语文成绩最高的学生：\n");
    printf("\t学号：%d", maxChineseStudent.number);
    printf("\t姓名：%s", maxChineseStudent.name);
    printf("\t语文成绩：%.1f\n", maxChineseStudent.course.chinese);
    printf("英语成绩最高的学生：\n");
    printf("\t学号：%d", maxEnglishStudent.number);
    printf("\t姓名：%s", maxEnglishStudent.name);
    printf("\t英语成绩：%.1f\n", maxEnglishStudent.course.english);

    // 输出三门课程平均分数最高的学生
    float maxAvg = (students[0].course.math + students[0].course.chinese + students[0].course.english) / 3;// 保存最高平均分
    struct Student maxAvgStudent = students[0];// 保存最高平均分的学生
    for (int i = 0; i < count; i++) {
        // 计算正在遍历的学生的三门课程的平均分
        float avg = (students[i].course.math + students[i].course.chinese + students[i].course.english) / 3;
        // 将平均分保存到该学生的avg字段上
        students[i].avg = avg;
        // 判断最高平均分
        if (avg > maxAvg) {
            maxAvg = avg;
            maxAvgStudent = students[i];
        }
    }
    printf("三门课程平均分数最高的学生：\n");
    printf("\t学号：%d", maxAvgStudent.number);
    printf("\t姓名：%s", maxAvgStudent.name);
    printf("\t平均分：%f\n", maxAvg);

    // 将10个学生按照平均分数从高到低进行排序，输出结果
    sort(students, count);
    printf("将10个学生按照平均分数从高到低进行排序：\n");
    printf("number\t\tname\t\tmath\t\tchinese\t\tenglish\t\taverage\n");
    for (int i = 0; i < count; i++) {
        printf("%d\t\t", students[i].number);
        printf("%s\t\t", students[i].name);
        printf("%.1f\t\t", students[i].course.math);
        printf("%.1f\t\t", students[i].course.chinese);
        printf("%.1f\t\t", students[i].course.english);
        printf("%.1f\t\t", students[i].avg);
        printf("\n");
    }

}

/**
 * 对学生结构体数组进行排序，根据平均分从高到低
 * @param students 学生结构体数组
 * @param n 数组长度
 */
void sort(struct Student students[], int n) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j + 1 < n - i; j++) {
            if (students[j].avg < students[j + 1].avg) {
                struct Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
}
```

代码执行结果如下：

```text
请输入10个学生的信息：
请输入学号：100
请输入姓名：张三
请输入数学成绩：78
请输入语文成绩：68
请输入英语成绩：99

请输入学号：101
请输入姓名：李四
请输入数学成绩：98
请输入语文成绩：88
请输入英语成绩：69

请输入学号：102
请输入姓名：王五
请输入数学成绩：82
请输入语文成绩：65
请输入英语成绩：59

请输入学号：103
请输入姓名：赵六
请输入数学成绩：66
请输入语文成绩：45
请输入英语成绩：88

请输入学号：104
请输入姓名：吴七
请输入数学成绩：74
请输入语文成绩：69
请输入英语成绩：72

请输入学号：105
请输入姓名：王八
请输入数学成绩：71
请输入语文成绩：86
请输入英语成绩：93

请输入学号：106
请输入姓名：郑九
请输入数学成绩：54
请输入语文成绩：48
请输入英语成绩：88

请输入学号：107
请输入姓名：午十
请输入数学成绩：100
请输入语文成绩：78
请输入英语成绩：68

请输入学号：108
请输入姓名：萧十一
请输入数学成绩：95
请输入语文成绩：88
请输入英语成绩：76

请输入学号：109
请输入姓名：燕十二
请输入数学成绩：65
请输入语文成绩：78
请输入英语成绩：45

学号：100       姓名：张三      数学成绩：78.0  语文成绩：68.0  英语成绩：99.0
学号：101       姓名：李四      数学成绩：98.0  语文成绩：88.0  英语成绩：69.0
学号：102       姓名：王五      数学成绩：82.0  语文成绩：65.0  英语成绩：59.0
学号：103       姓名：赵六      数学成绩：66.0  语文成绩：45.0  英语成绩：88.0
学号：104       姓名：吴七      数学成绩：74.0  语文成绩：69.0  英语成绩：72.0
学号：105       姓名：王八      数学成绩：71.0  语文成绩：86.0  英语成绩：93.0
学号：106       姓名：郑九      数学成绩：54.0  语文成绩：48.0  英语成绩：88.0
学号：107       姓名：午十      数学成绩：100.0 语文成绩：78.0  英语成绩：68.0
学号：108       姓名：萧十一    数学成绩：95.0  语文成绩：88.0  英语成绩：76.0
学号：109       姓名：燕十二    数学成绩：65.0  语文成绩：78.0  英语成绩：45.0
数学成绩最高的学生：
        学号：107       姓名：午十      数学成绩：100.0
语文成绩最高的学生：
        学号：101       姓名：李四      语文成绩：88.0
英语成绩最高的学生：
        学号：100       姓名：张三      英语成绩：99.0
三门课程平均分数最高的学生：
        学号：108       姓名：萧十一    平均分：86.333336
将10个学生按照平均分数从高到低进行排序：
number          name            math            chinese         english         average
108             萧十一          95.0            88.0            76.0            86.3
101             李四            98.0            88.0            69.0            85.0
105             王八            71.0            86.0            93.0            83.3
107             午十            100.0           78.0            68.0            82.0
100             张三            78.0            68.0            99.0            81.7
104             吴七            74.0            69.0            72.0            71.7
102             王五            82.0            65.0            59.0            68.7
103             赵六            66.0            45.0            88.0            66.3
106             郑九            54.0            48.0            88.0            63.3
109             燕十二          65.0            78.0            45.0            62.7
```