# 练习实例91

## 题目

时间函数举例1。


## 分析

本题考查的知识点：
- 时间和日期函数


## 代码

```c
#include <stdio.h>
#include <time.h>

int main() {
    // time_t类型就是long long类型
    time_t t;
    // 获取系统当前时间
    t = time(NULL);
    printf("%lld\n", t);

    // ctime()函数，将日期和时间转换成字符串，传入的应该是变量的地址
    printf("%s\n", ctime(&t));

    // localtime()是把从 1970-01-01 00:00 到当前时间系统所偏移的秒数转换为本地时间
    // asctime()函数把存放的时间转换成字符串，参数是tm类型
    printf("%s\n", asctime(localtime(&t)));
    // gmtime()函数转换后的时间是没有经过时区转换的，是UTC时间
    printf("%s\n", asctime(gmtime(&t)));
}
```

代码执行结果如下（时间是变化的，所以结果不以下面为标准）：

```text
1644678165
Sat Feb 12 23:02:45 2022

Sat Feb 12 23:02:45 2022

Sat Feb 12 15:02:45 2022
```