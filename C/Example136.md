# 练习实例136

## 题目

编写一个程序，输入星期，输出该星期的英文名。用指针数组处理。


## 分析

本题考查的知识点:
- 字符串数组
- 指针
- `printf`和`scanf`函数

分析：
- 本题考查的就是字符串数组的声明和使用。


## 代码

```c
#include<stdio.h>

int main() {
    // 声明字符串数组
    char *week[7] = {"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"};

    // 从键盘输入数字
    int num;
    printf("请输入一个表示星期的数字：");
    scanf("%d", &num);

    // 打印结果
    printf("%s", week[num]);
}
```

代码执行结果如下：

```text
请输入一个表示星期的数字：1
Monday
```