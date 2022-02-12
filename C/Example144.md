# 练习实例144

## 题目

输入一名学生的学号、姓名、年龄和身高等信息，用结构体保存，然后再把输入的信息输出到屏幕上。


## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- `printf`和`scanf`函数

分析：
- 本题主要考查的是结构体的声明和使用。


## 代码

```c
#include<stdio.h>

typedef struct Student {
    int number;
    char name[4];
    int age;
    float height;
} Student;

int main() {
    Student student;
    printf("请输入学号：");
    scanf("%d", &student.number);
    printf("请输入姓名：");
    scanf("%s", student.name);
    printf("请输入年龄：");
    scanf("%d", &student.age);
    printf("请输入身高：");
    scanf("%f", &student.height);

    printf("学号：%d\t姓名：%s\t年龄：%d\t身高：%.2f", student.number, student.name, student.age, student.height);
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入年龄：18
请输入身高：180
学号：101       姓名：tom       年龄：18        身高：180.00
```