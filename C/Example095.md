# 练习实例95

## 题目

简单的结构体应用实例。


## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- `printf`和`scanf`函数

分析：
- 本题就是考查的是结构体知识，结构体的声明、输入、输出等。

## 代码

```c
#include <stdio.h>

typedef struct Student {
    int number;
    char name[4];
    char gender;
    int age;
    float score;
} Stu;

int main() {
    Stu stu;

    printf("请输入学号：");
    scanf("%d", &stu.number);
    printf("请输入姓名：");
    scanf("%s", stu.name);
    getchar();// 吸收掉换行符'\n'
    printf("请输入性别：");
    scanf("%c", &stu.gender);
    printf("请输入年龄：");
    scanf("%d", &stu.age);
    printf("请输入成绩：");
    scanf("%f", &stu.score);

    printf("%d %s %c %d %.2f", stu.number, stu.name, stu.gender, stu.age, stu.score);
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入性别：f
请输入年龄：18
请输入成绩：85.5
101 tom f 18 85.50
```