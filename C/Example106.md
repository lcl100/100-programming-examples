# 练习实例106

## 题目

学生成绩管理系统（利用顺序表完成）。需要完成下列功能：

1、输入：函数`input`把20个学生的学号、姓名、性别、年龄、四科成绩以及平均成绩和总成绩放在一个结构体数组中，学生的学号、姓名、四科成绩成绩由键盘输入，然后计算出平均成绩和总成绩放在结构体对应的域中。

2、插入：`insert`函数输入一个学生的记录，按学号的先后顺序插入该学生的全部内容。

3、排序：`sort`函数对所有学生按要求排序（学号、总成绩），并输出。

4、查找：`find`函数输入一个学生的学号或姓名，找到该学生并输出该学生的全部内容。要求能查询多次。

5、删除：`delete`函数输入一个学生的学号或姓名，找到该学生并删除该学生的全部内容。

6、输出：函数`output`输出全部学生的记录。

7、`main`：调用所有函数，并且实现全部函数功能。（注：除了定义结构之外，不允许使用全局变量，函数之间的数据全部使用参数传递。）

## 分析

利用顺序表（即数组）来实现：

- 插入：向数组中插入元素，题目要求是按照学号顺序插入，所以要先找到插入元素应该在顺序表中的位置（即下标），然后将插入位置及之后所有元素向后移动一位，最后将待插入元素填入空位，并且顺序表长度加1。
- 排序：排序就是按照学号或者总成绩排序，这里使用的是冒泡排序。
- 查找：即在数组中查找某个元素，这里是通过遍历整个数组进行查找的。注意，比较字符串是否相等使用了`strcmp()`函数，该函数表示如果两个字符串相等则返回0。
- 删除：首先要按照学号或者姓名找到待删除元素在顺序表中的下标，然后将该位置之后的所有元素向前移动一位，最后顺序表长度减1。
- 输出：即遍历顺序表。

## 代码

```c
#include <stdio.h>
#include <string.h>

#define MAXSIZE 20

struct Course {
    float math;// 数学
    float chinese;// 语文
    float english;// 英语
    float music;// 音乐
};

struct Student {
    int number;// 学号
    char name[10];// 姓名
    char gender[1];// 性别
    int age;// 年龄
    struct Course course;// 四门课程
    float avg;// 平均成绩
    float sum;// 总成绩
};

struct StudentList {
    struct Student students[MAXSIZE];
    int length;// 顺序表中元素实际个数
};

struct Student input();

void output(struct StudentList studentList);

void insert(struct StudentList *studentList, struct Student student);

void sortByTotalScore(struct StudentList *studentList);

void sortByNumber(struct StudentList *studentList);

struct Student findByName(struct StudentList studentList, char name[]);

struct Student findByNumber(struct StudentList studentList, int number);

void deleteByName(struct StudentList *studentList, char name[]);

void deleteByNumber(struct StudentList *studentList, int number);


int main() {
    // 定义一个20个学生的结构体数组
    int count = 2;
    struct StudentList studentList;
    studentList.length = 0;

    // 输入指定个数的学生
    for (int i = 0; i < count; i++) {
        studentList.students[i] = input();
        studentList.length++;
    }
    output(studentList);

    // 插入一条学生记录
    struct Student student = input();
    insert(&studentList, student);
    output(studentList);

    printf("\n根据总成绩排序：\n");
    sortByTotalScore(&studentList);
    output(studentList);

    printf("\n根据学号排序：\n");
    sortByNumber(&studentList);
    output(studentList);

    printf("\n根据姓名查找学生：\n");
    struct Student stu1;
    stu1 = findByName(studentList, "tom");
    printf("学号\t姓名\t性别\t年龄\t语文\t数学\t英语\t音乐\t总成绩\t平均成绩\n");
    printf("%d\t", stu1.number);
    printf("%s\t", stu1.name);
    printf("%s\t", stu1.gender);
    printf("%d\t", stu1.age);
    printf("%.1f\t", stu1.course.chinese);
    printf("%.1f\t", stu1.course.math);
    printf("%.1f\t", stu1.course.english);
    printf("%.1f\t", stu1.course.music);
    printf("%.1f\t", stu1.sum);
    printf("%.1f\t\n", stu1.avg);

    printf("\n根据学号查找学生：\n");
    struct Student stu2;
    stu2 = findByNumber(studentList, 101);
    printf("学号\t姓名\t性别\t年龄\t语文\t数学\t英语\t音乐\t总成绩\t平均成绩\n");
    printf("%d\t", stu2.number);
    printf("%s\t", stu2.name);
    printf("%s\t", stu2.gender);
    printf("%d\t", stu2.age);
    printf("%.1f\t", stu2.course.chinese);
    printf("%.1f\t", stu2.course.math);
    printf("%.1f\t", stu2.course.english);
    printf("%.1f\t", stu2.course.music);
    printf("%.1f\t", stu2.sum);
    printf("%.1f\t\n", stu2.avg);

    printf("\n根据姓名删除学生：\n");
    deleteByName(&studentList, "tom");
    output(studentList);

    printf("\n根据学号删除学生：\n");
    deleteByNumber(&studentList, 102);
    output(studentList);
}

/**
 * 输入一个学生的全部信息
 * @return 包含输入学生信息的结构体
 */
struct Student input() {
    struct Student student;
    printf("\n请输入学号：");
    scanf("%d", &student.number);
    printf("请输入姓名：");
    scanf("%s", student.name);
    printf("请输入性别：");
    scanf("%s", student.gender);
    printf("请输入年龄：");
    scanf("%d", &student.age);
    printf("请输入语文成绩：");
    scanf("%f", &student.course.chinese);
    printf("请输入数学成绩：");
    scanf("%f", &student.course.math);
    printf("请输入英语成绩：");
    scanf("%f", &student.course.english);
    printf("请输入音乐成绩：");
    scanf("%f", &student.course.music);
    // 计算总成绩并且保存到结构体中
    float sum = student.course.chinese + student.course.math + student.course.english + student.course.music;
    student.sum = sum;
    // 计算平均成绩并且保存到结构体中
    float avg = sum / 4;
    student.avg = avg;
    return student;
}

/**
 * 将指定学生插入到学生数组中，按照学号先后顺序插入
 * 注意，数组的长度必须大于元素实际个数，否则会报错
 * @param students 学生数组
 * @param n 数组中实际元素个数
 * @param student 待插入的学生
 */
void insert(struct StudentList *studentList, struct Student student) {
    if ((*studentList).length >= MAXSIZE) {
        printf("顺序表已满，无法添加学生");
        return;
    }

    // 存放新元素的插入位置，即数组下标
    int index = -1;
    for (int i = 0; i < (*studentList).length; i++) {
        // 根据学生的学号寻找到插入位置
        if (student.number < (*studentList).students[i].number) {
            index = i;
            // 注意，必须跳出循环
            break;
        }
    }
    // 如果索引位置等于-1，则表示该插入最后一个位置
    if (index == -1) {
        (*studentList).students[(*studentList).length] = student;
        (*studentList).length++;
    } else {
        // 将指定位置及之后的所有元素向后移动一位
        for (int j = (*studentList).length; j > index; j--) {
            (*studentList).students[j] = (*studentList).students[j - 1];
        }
        // 然后将空出的位置填入待插入的学生
        (*studentList).students[index] = student;
        // 同时length加1
        (*studentList).length++;
    }
}

/**
 * 按总成绩对所有学生进行排序
 * @param studentList 待排序的学生顺序表
 */
void sortByTotalScore(struct StudentList *studentList) {
    for (int i = 0; i < (*studentList).length; i++) {
        for (int j = 0; j + 1 < (*studentList).length - i; j++) {
            if ((*studentList).students[j].sum > (*studentList).students[j + 1].sum) {
                struct Student temp = (*studentList).students[j];
                (*studentList).students[j] = (*studentList).students[j + 1];
                (*studentList).students[j + 1] = temp;
            }
        }
    }
}

/**
 * 按学号对所有学生进行排序
 * @param studentList 待排序的学生顺序表
 */
void sortByNumber(struct StudentList *studentList) {
    for (int i = 0; i < (*studentList).length; i++) {
        for (int j = 0; j + 1 < (*studentList).length - i; j++) {
            if ((*studentList).students[j].number > (*studentList).students[j + 1].number) {
                struct Student temp = (*studentList).students[j];
                (*studentList).students[j] = (*studentList).students[j + 1];
                (*studentList).students[j + 1] = temp;
            }
        }
    }
}

/**
 * 通过学号查找学生
 * @param studentList 学生顺序表
 * @param number 学号
 * @return 根据学号查找成功的学生
 */
struct Student findByNumber(struct StudentList studentList, int number) {
    struct Student student;
    for (int i = 0; i < studentList.length; i++) {
        if (studentList.students[i].number == number) {
            student = studentList.students[i];
        }
    }
    return student;
}

/**
 * 通过姓名查找学生
 * @param studentList 学生顺序表
 * @param name 待查找的学生姓名
 * @return 根据姓名查找成功的学生
 */
struct Student findByName(struct StudentList studentList, char name[]) {
    struct Student student;
    for (int i = 0; i < studentList.length; i++) {
        if (strcmp(studentList.students[i].name, name) == 0) {
            student = studentList.students[i];
        }
    }
    return student;
}

/**
 * 根据学号删除学生
 * @param studentList 学生顺序表
 * @param number 待删除学生的学号
 */
void deleteByNumber(struct StudentList *studentList, int number) {
    for (int i = 0; i < (*studentList).length; i++) {
        if ((*studentList).students[i].number == number) {
            for (int j = i; j < (*studentList).length - 1; j++) {
                (*studentList).students[j] = (*studentList).students[j + 1];
            }
            (*studentList).length--;
            break;
        }
    }
}

/**
 * 根据姓名删除学生
 * @param studentList 学生顺序表
 * @param name 待删除学生的姓名
 */
void deleteByName(struct StudentList *studentList, char name[]) {
    for (int i = 0; i < (*studentList).length; i++) {
        if (strcmp((*studentList).students[i].name, name) == 0) {
            for (int j = i; j < (*studentList).length - 1; j++) {
                (*studentList).students[j] = (*studentList).students[j + 1];
            }
            (*studentList).length--;
            break;
        }
    }
}

/**
 * 输出全部的学生记录
 * @param students 学生数组
 * @param n 数组长度
 */
void output(struct StudentList studentList) {
    printf("学号\t姓名\t性别\t年龄\t语文\t数学\t英语\t音乐\t总成绩\t平均成绩\n");
    for (int i = 0; i < studentList.length; i++) {
        struct Student student = studentList.students[i];
        printf("%d\t", student.number);
        printf("%s\t", student.name);
        printf("%s\t", student.gender);
        printf("%d\t", student.age);
        printf("%.1f\t", student.course.chinese);
        printf("%.1f\t", student.course.math);
        printf("%.1f\t", student.course.english);
        printf("%.1f\t", student.course.music);
        printf("%.1f\t", student.sum);
        printf("%.1f\t\n", student.avg);
    }
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入性别：f
请输入年龄：18
请输入语文成绩：19
请输入数学成绩：86
请输入英语成绩：56
请输入音乐成绩：44

请输入学号：102
请输入姓名：jack
请输入性别：f
请输入年龄：16
请输入语文成绩：88
请输入数学成绩：79
请输入英语成绩：96
请输入音乐成绩：68
学号     姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3
102     jack    f       16      88.0    79.0    96.0    68.0    331.0   82.8

请输入学号：99
请输入姓名：liyi
请输入性别：m
请输入年龄：17
请输入语文成绩：85
请输入数学成绩：76
请输入英语成绩：66
请输入音乐成绩：69
学号
        姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
99      liyi    m       17      85.0    76.0    66.0    69.0    296.0   74.0
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3
102     jack    f       16      88.0    79.0    96.0    68.0    331.0   82.8

根据总成绩排序：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3
99      liyi    m       17      85.0    76.0    66.0    69.0    296.0   74.0
102     jack    f       16      88.0    79.0    96.0    68.0    331.0   82.8

根据学号排序：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
99      liyi    m       17      85.0    76.0    66.0    69.0    296.0   74.0
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3
102     jack    f       16      88.0    79.0    96.0    68.0    331.0   82.8

根据姓名查找学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3

根据学号查找学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       18      19.0    86.0    56.0    44.0    205.0   51.3

根据姓名删除学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
99      liyi    m       17      85.0    76.0    66.0    69.0    296.0   74.0
102     jack    f       16      88.0    79.0    96.0    68.0    331.0   82.8

根据学号删除学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
99      liyi    m       17      85.0    76.0    66.0    69.0    296.0   74.0
```