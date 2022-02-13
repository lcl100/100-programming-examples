# 练习实例71

## 题目

编写 input() 和 output() 函数输入，输出5个学生的数据记录。


## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- 函数
- for 循环语句
- `printf`和`scanf`函数

分析：
- 本题考查的是结构体的声明、输入和使用。


## 代码

```c
#include <stdio.h>

// 学生结构体
typedef struct {
    int number;// 学号
    char name[4];// 姓名
    int age;// 年龄
    float score;// 成绩
} Student;

Student input();

void output(Student students[], int n);

int main() {
    Student students[5];

    // 输入5个学生
    for (int i = 0; i < 5; i++) {
        students[i] = input();
    }

    // 输出5个学生
    printf("\n");
    output(students, 5);
}

/**
 * 从键盘输入学生信息
 * @return 学生结构体
 */
Student input() {
    Student student;
    printf("请输入学号：");
    scanf("%d", &student.number);
    printf("请输入姓名：");
    scanf("%s", student.name);
    printf("请输入年龄：");
    scanf("%d", &student.age);
    printf("请输入成绩：");
    scanf("%f", &student.score);
    printf("\n");
    return student;
}

/**
 * 输出所有的学生信息
 * @param students 学生结构体数组
 * @param n 数组长度
 */
void output(Student students[], int n) {
    for (int i = 0; i < n; i++) {
        Student stu = students[i];
        printf("%d\t%s\t%d\t%.2f\n", stu.number, stu.name, stu.age, stu.score);
    }
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入年龄：19
请输入成绩：66

请输入学号：102
请输入姓名：jack
请输入年龄：20
请输入成绩：77

请输入学号：103
请输入姓名：rose
请输入年龄：21
请输入成绩：88

请输入学号：104
请输入姓名：lili
请输入年龄：22
请输入成绩：99

请输入学号：105
请输入姓名：lihua
请输入年龄：23
请输入成绩：100


101     tom     19      66.00
102     jack   20      77.00
103     rose   21      88.00
104     lili   22      99.00
105     lihu   23      100.00
```