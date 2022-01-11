# 练习实例4

## 题目

输入某年某月某日，判断这一天是这一年的第几天？

## 分析

以3月5日为例，应该先把前两个月的加起来，然后再加上5天即本年的第几天，特殊情况，闰年且输入月份大于3时需考虑多加一天。

## 代码

```c
#include <stdio.h>

#define true 1
#define false 0

/**
 * 判断给定年份是否是闰年
 * @param year  给定年份
 * @return 如果是闰年则返回1；否则返回0
 */
int isLeapYear(int year) {
    // 满足年份是4的倍数且不是100的倍数的为闰年或者年份是整百数的并且是400的倍数才是闰年
    if (year % 400 == 0 || (year % 4 == 0 && year % 100 != 0)) {
        return true;
    }
    return false;
}

int main() {
    // 数组，记录了从1月到12月每个月的天数
    int months[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    // 记录这一天是这一年的第几天
    int days = 0;

    int year;
    int month;
    int day;
    printf("请按如下格式输入日期（2022-01-11）：\n");
    scanf("%d-%d-%d", &year, &month, &day);// 获取用户输入的年月日

    if (isLeapYear(year) && month > 2) {// 如果是闰年且月份大于2，总天数应该加一天
        days += 1;
    }
    for (int i = 1; i < month; i++) {// 统计每个月的天数，如7月则需要计算前6个月的总天数
        days += months[i - 1];// 注意，下标减1
    }
    days += day;// 计算天

    printf("这是这一年的第 %d 天", days);
}
```

代码执行结果如下：

```text
请按如下格式输入日期（2022-01-11）：
2015-10-01
这是这一年的第 274 天
```