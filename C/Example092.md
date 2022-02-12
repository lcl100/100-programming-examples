# 练习实例92

## 题目

时间函数举例2。


## 分析

本题考查的知识点：
- 时间和日期函数

分析：
- `difftime(time1, time2)`：计算两次时间的差值。
-  可以用来统计一段程序的执行时间。


## 代码

```c
#include <stdio.h>
#include <time.h>

int main() {
    time_t start, end;// 记录一段程序执行开始的时间和结束的时间

    start = time(NULL);
    for (int i = 0; i < 10000; i++) {// 这段程序没有任何意义，仅用于测试时间函数的使用
        printf("%d", i);
    }
    end = time(NULL);

    // 返回 time1 和 time2 之间相差的秒数 (time1 - time2)
    printf("%.3f", difftime(end, start));
}
```

代码执行结果如下（执行结果会不一样）：

```text
97999899991.000
```