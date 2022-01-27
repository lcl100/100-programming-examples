# 练习实例105

## 题目

1、定义一个结构体数组，存放10个学生的学号，姓名，三门课的成绩。

2、从键盘输入10个学生的以上内容，存入文件stud.dat，关闭文件。

3、打开 stud.dat 文件，将数据读出，查看是否正确写入，关闭文件。

4、打开文件 stud.dat 文件，读出数据，将10个学生按照平均分数从高到低进行排序，分别将结果输出到屏幕上和另一文件 studsort.dat 中。

5、从 studsort.dat 文件中读取第2、4、6、8、10个学生的数据。

## 分析

本题考查的是文件的读取和写入的相关知识。

注意每次文件的读取和写入都要执行`fclose(fp)`方法关闭。

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
        students[i].avg = (students[i].course.math + students[i].course.chinese + students[i].course.english) / 3;
        printf("\n");
    }

    // 打印输入的10个学生的信息
    printf("打印从键盘输入的10个学生的信息：\n");
    for (int i = 0; i < count; i++) {
        printf("\t学号：%d\t", students[i].number);
        printf("姓名：%s\t", students[i].name);
        printf("数学成绩：%.1f\t", students[i].course.math);
        printf("语文成绩：%.1f\t", students[i].course.chinese);
        printf("英语成绩：%.1f\n", students[i].course.english);
    }

    // 将10个学生保存到stud.dat文件中
    char *filename = "stud.dat";
    FILE *fp;
    if ((fp = fopen(filename, "wt+")) == NULL) {
        printf("打开文件失败：%s", filename);
        return 0;
    }
    for (int i = 0; i < count; i++) {
        fwrite(&students[i], sizeof(struct Student), 1, fp);
    }
    fclose(fp);

    // 打开stud.dat文件，将数据读出，查看是否正确
    if ((fp = fopen(filename, "rt+")) == NULL) {
        printf("打开文件失败：%s", filename);
        return 0;
    }
    struct Student readStudents[count];
    for (int i = 0; i < count; i++) {
        fread(&readStudents[i], sizeof(struct Student), 1, fp);
    }
    fclose(fp);
    printf("读出stud.dat文件中的数据，核对是否正确写入：\n");
    for (int i = 0; i < count; i++) {// 打印从文件读取的数组
        printf("\t学号：%d\t", students[i].number);
        printf("姓名：%s\t", students[i].name);
        printf("数学成绩：%.1f\t", students[i].course.math);
        printf("语文成绩：%.1f\t", students[i].course.chinese);
        printf("英语成绩：%.1f\n", students[i].course.english);
    }

    // 打开文件stud.dat文件，读出数据，将10个学生按照平均分数从高到低排序，并且将结果输出和保存到另外一个文件studsort.dat中
    if ((fp = fopen(filename, "rt+")) == NULL) {
        printf("打开文件失败：%s", filename);
        return 0;
    }
    struct Student sortedStudents[count];
    for (int i = 0; i < count; i++) {
        fread(&sortedStudents[i], sizeof(struct Student), 1, fp);
    }
    fclose(fp);
    sort(sortedStudents, count);// 对十个学生按照平均分数的高低排序
    printf("将%d个学生按照平均分数从高到低进行排序：\n", count);
    for (int i = 0; i < count; i++) {
        printf("\t学号：%d\t", sortedStudents[i].number);
        printf("姓名：%s\t", sortedStudents[i].name);
        printf("数学成绩：%.1f\t", sortedStudents[i].course.math);
        printf("语文成绩：%.1f\t", sortedStudents[i].course.chinese);
        printf("英语成绩：%.1f\t", sortedStudents[i].course.english);
        printf("平均分数：%.1f\n", sortedStudents[i].avg);
    }
    filename = "studsort.dat";// 将结果保存到另一个文件studsort.dat中
    if ((fp = fopen(filename, "wt+")) == NULL) {
        printf("打开文件失败：%s", filename);
        return 0;
    }
    for (int i = 0; i < count; i++) {
        fwrite(&sortedStudents[i], sizeof(struct Student), 1, fp);
    }
    fclose(fp);// 注意，每次一定要关闭fp，否则下面使用就会无法读取到正确的数据

    // 从studsort.dat文件中读取第2、4、6、8、10个学生的数据
    if ((fp = fopen(filename, "rt+")) == NULL) {
        printf("打开文件失败：%s", filename);
        return 0;
    }
    struct Student readSortedStudents[count];
    for (int i = 0; i < count; i++) {
        fread(&readSortedStudents[i], sizeof(struct Student), 1, fp);
    }
    fclose(fp);
    printf("从studsort.dat文件中读取第2、4、6、8、10个学生的数据：\n");
    for (int i = 0; i < count; i++) {
        if ((i + 1) % 2 == 0) {// 只打印第2、4、6、8、10个学生的信息
            printf("\t学号：%d\t", readSortedStudents[i].number);
            printf("姓名：%s\t", readSortedStudents[i].name);
            printf("数学成绩：%.1f\t", readSortedStudents[i].course.math);
            printf("语文成绩：%.1f\t", readSortedStudents[i].course.chinese);
            printf("英语成绩：%.1f\t", readSortedStudents[i].course.english);
            printf("平均分数：%.1f\n", readSortedStudents[i].avg);
        }
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
请输入数学成绩：58
请输入语文成绩：68
请输入英语成绩：77

请输入学号：101
请输入姓名：李四
请输入数学成绩：98
请输入语文成绩：88
请输入英语成绩：75

请输入学号：102
请输入姓名：王五
请输入数学成绩：74
请输入语文成绩：66
请输入英语成绩：89

请输入学号：103
请输入姓名：赵六
请输入数学成绩：77
请输入语文成绩：66
请输入英语成绩：48

请输入学号：104
请输入姓名：郑七
请输入数学成绩：100
请输入语文成绩：85
请输入英语成绩：72

请输入学号：105
请输入姓名：王八
请输入数学成绩：59
请输入语文成绩：66
请输入英语成绩：87

请输入学号：106
请输入姓名：武九
请输入数学成绩：85
请输入语文成绩：86
请输入英语成绩：84

请输入学号：107
请输入姓名：孟十
请输入数学成绩：75
请输入语文成绩：99
请输入英语成绩：68

请输入学号：108
请输入姓名：萧十一
请输入数学成绩：71
请输入语文成绩：69
请输入英语成绩：80

请输入学号：109
请输入姓名：舒十二
请输入数学成绩：85
请输入语文成绩：69
请输入英语成绩：75

打印从键盘输入的10个学生的信息：
        学号：100       姓名：张三      数学成绩：58.0  语文成绩：68.0  英语成绩：77.0
        学号：101       姓名：李四      数学成绩：98.0  语文成绩：88.0  英语成绩：75.0
        学号：102       姓名：王五      数学成绩：74.0  语文成绩：66.0  英语成绩：89.0
        学号：103       姓名：赵六      数学成绩：77.0  语文成绩：66.0  英语成绩：48.0
        学号：104       姓名：郑七      数学成绩：100.0 语文成绩：85.0  英语成绩：72.0
        学号：105       姓名：王八      数学成绩：59.0  语文成绩：66.0  英语成绩：87.0
        学号：106       姓名：武九      数学成绩：85.0  语文成绩：86.0  英语成绩：84.0
        学号：107       姓名：孟十      数学成绩：75.0  语文成绩：99.0  英语成绩：68.0
        学号：108       姓名：萧十一    数学成绩：71.0  语文成绩：69.0  英语成绩：80.0
        学号：109       姓名：舒十二    数学成绩：85.0  语文成绩：69.0  英语成绩：75.0
读出stud.dat文件中的数据，核对是否正确写入：
        学号：100       姓名：张三      数学成绩：58.0  语文成绩：68.0  英语成绩：77.0
        学号：101       姓名：李四      数学成绩：98.0  语文成绩：88.0  英语成绩：75.0
        学号：102       姓名：王五      数学成绩：74.0  语文成绩：66.0  英语成绩：89.0
        学号：103       姓名：赵六      数学成绩：77.0  语文成绩：66.0  英语成绩：48.0
        学号：104       姓名：郑七      数学成绩：100.0 语文成绩：85.0  英语成绩：72.0
        学号：105       姓名：王八      数学成绩：59.0  语文成绩：66.0  英语成绩：87.0
        学号：106       姓名：武九      数学成绩：85.0  语文成绩：86.0  英语成绩：84.0
        学号：107       姓名：孟十      数学成绩：75.0  语文成绩：99.0  英语成绩：68.0
        学号：108       姓名：萧十一    数学成绩：71.0  语文成绩：69.0  英语成绩：80.0
        学号：109       姓名：舒十二    数学成绩：85.0  语文成绩：69.0  英语成绩：75.0
将10个学生按照平均分数从高到低进行排序：
        学号：101       姓名：李四      数学成绩：98.0  语文成绩：88.0  英语成绩：75.0  平均分数：87.0
        学号：104       姓名：郑七      数学成绩：100.0 语文成绩：85.0  英语成绩：72.0  平均分数：85.7
        学号：106       姓名：武九      数学成绩：85.0  语文成绩：86.0  英语成绩：84.0  平均分数：85.0
        学号：107       姓名：孟十      数学成绩：75.0  语文成绩：99.0  英语成绩：68.0  平均分数：80.7
        学号：102       姓名：王五      数学成绩：74.0  语文成绩：66.0  英语成绩：89.0  平均分数：76.3
        学号：109       姓名：舒十二    数学成绩：85.0  语文成绩：69.0  英语成绩：75.0  平均分数：76.3
        学号：108       姓名：萧十一    数学成绩：71.0  语文成绩：69.0  英语成绩：80.0  平均分数：73.3
        学号：105       姓名：王八      数学成绩：59.0  语文成绩：66.0  英语成绩：87.0  平均分数：70.7
        学号：100       姓名：张三      数学成绩：58.0  语文成绩：68.0  英语成绩：77.0  平均分数：67.7
        学号：103       姓名：赵六      数学成绩：77.0  语文成绩：66.0  英语成绩：48.0  平均分数：63.7
从studsort.dat文件中读取第2、4、6、8、10个学生的数据：
        学号：104       姓名：郑七      数学成绩：100.0 语文成绩：85.0  英语成绩：72.0  平均分数：85.7
        学号：107       姓名：孟十      数学成绩：75.0  语文成绩：99.0  英语成绩：68.0  平均分数：80.7
        学号：109       姓名：舒十二    数学成绩：85.0  语文成绩：69.0  英语成绩：75.0  平均分数：76.3
        学号：105       姓名：王八      数学成绩：59.0  语文成绩：66.0  英语成绩：87.0  平均分数：70.7
        学号：103       姓名：赵六      数学成绩：77.0  语文成绩：66.0  英语成绩：48.0  平均分数：63.7
```