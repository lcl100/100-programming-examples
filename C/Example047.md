# 练习实例47

## 题目

宏 #define 命令练习2。


## 分析

本题考查的知识点：
- 预处理命令

## 代码

```c
#include <stdio.h>

int y = 5;

#define PI 3.1415626
#define S PI*y*y // 宏定义允许嵌套，在宏定义的字符串中可以使用已经定义的宏名

int main() {
    printf("%f\n", S);
    // 等价于
    printf("%f\n", 3.1415926 * y * y);
}
```

代码执行结果如下：

```text
78.539065
78.539815
```