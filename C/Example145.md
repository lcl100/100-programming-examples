# 练习实例145

## 题目

定义一个结构体变量，包括年、月、日。计算该日在本年中是第几天，注意闰年问题。


## 分析

本题考查的知识点：
- 结构体
- 函数
- 一维数组
- if 语句
- `printf`和`scanf`函数

分析：
- 本题主要考查的是结构体知识，关于『如何计算该日在本年中是第几天』可以参考『Example004』。


## 代码

```c
#include<stdio.h>

struct Date {
    int year;
    int month;
    int day;
};

int isLeapYear(int year);

int main() {
    // 数组，记录了从1月到12月每个月的天数
    int months[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    // 记录这一天是这一年的第几天
    int days = 0;
    struct Date date;

    printf("请输入年份：");
    scanf("%d", &date.year);
    printf("请输入月份：");
    scanf("%d", &date.month);
    printf("请输入天：");
    scanf("%d", &date.day);

    if (isLeapYear(date.year) && date.month > 2) {// 如果是闰年且月份大于2，总天数应该加一天
        days += 1;
    }
    for (int i = 1; i < date.month; i++) {// 统计每个月的天数，如7月则需要计算前6个月的总天数
        days += months[i - 1];// 注意，下标减1
    }
    days += date.day;// 计算天

    printf("这是这一年的第 %d 天", days);
}

/**
 * 判断给定年份是否是闰年
 * @param year  给定年份
 * @return 如果是闰年则返回1；否则返回0
 */
int isLeapYear(int year) {
    // 满足年份是4的倍数且不是100的倍数的为闰年或者年份是整百数的并且是400的倍数才是闰年
    if (year % 400 == 0 || (year % 4 == 0 && year % 100 != 0)) {
        return 1;
    }
    return 0;
}
```

代码执行结果如下：

```text
请输入年份：2015
请输入月份：10
请输入天：1
这是这一年的第 274 天
```