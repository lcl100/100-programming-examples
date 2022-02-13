# 练习实例46

## 题目

宏 #define 命令练习。


## 分析

本题考查的知识点：
- 预处理命令


## 代码

```c
#include <stdio.h>

// 宏定义
#define PI 3.14159

int main() {
    int r = 5;
    printf("%f", PI * r * r);
}
```

代码执行结果如下：

```text
78.539750
```