# 练习实例48

## 题目

宏 #define 命令练习3。


## 分析

本题考查的知识点：
- 预处理命令


## 代码

```c
#include <stdio.h>

// 带参宏定义，类似于定义带参函数
#define MAX(x, y) (x>y)?x:y
#define MIN(x, y) (x>y)?y:x

int main() {
    int x, y;
    printf("请输入两个数字：");
    scanf("%d%d", &x, &y);
    printf("最大值：%d\n", MAX(x, y));
    printf("最小值：%d\n", MIN(x, y));
}
```

代码执行结果如下：

```text
请输入两个数字：3 4
最大值：4
最小值：3
```