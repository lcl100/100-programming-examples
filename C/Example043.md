# 练习实例43

## 题目

学习使用 static 的另一用法。


## 分析

分析：
- 在`{}`中用`static`声明的变量的修改，不会影响`{}`外部同名变量。

## 代码

```c
#include <stdio.h>

int main() {
    int i, num;
    num = 2;
    for (i = 0; i < 3; i++) {
        printf("num 变量为 %d \n", num);
        num++;
        {
            static int num = 1;
            printf("内置模块 num 变量为 %d\n", num);
            num++;
        }
    }
}
```

代码执行结果如下：

```text
num 变量为 2
内置模块 num 变量为 1
num 变量为 3
内置模块 num 变量为 2
num 变量为 4
内置模块 num 变量为 3
```