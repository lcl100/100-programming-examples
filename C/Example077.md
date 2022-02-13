# 练习实例77

## 题目

指向指针的指针。


## 分析

考查的知识点：
- 字符串数组
- 指向指针的指针

分析：
- 本题考查的是指向指针的指针。

## 代码

```c
#include <stdio.h>

int main() {
    char *strs[] = {"tom", "jack", "liyi", "rose"};
    char **q;

    for (int i = 0; i < 4; i++) {
        q = &strs[i];
        printf("%s\n", *q);
    }
}
```

代码执行结果如下：

```text
tom
jack
liyi
rose
```