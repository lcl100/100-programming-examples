# 练习实例93

## 题目

时间函数举例3。


## 分析

本题考查的知识点：
- 时间和日期函数

分析
- `clock()`：记录程序从启动到函数调用所占用CPU的时间，返回的是`clock_t`类型。


## 代码

```c
#include <stdio.h>
#include <time.h>

int main() {
    clock_t start, end;// 记录一段程序从启动到函数调用占用CPU的时间

    start = clock();
    for (int i = 0; i < 10000; i++) {// 这段程序没有任何意义，仅用于测试时间函数的使用
        printf("%d", i);
    }
    end = clock();

    printf("%.3f", (double) (end - start));
}
```

代码执行结果如下（执行结果会不一样）：

```text
9799989999997.000
```