# 练习实例50

## 题目

`#include`的应用练习。


## 分析

本题考查的知识点：
- `#include`

分析：
- 可以通过`#include`来引入一些公共代码或者配置文件。

## 代码

先定义一个 test.h 文件，存放了一些定义的宏：
```c
#define RT >
#define LT <
#define EQ ==
```
然后在主代码文件中引入：
```c
#include <stdio.h>
#include "test.h"

int main() {
    int a = 10, b = 20;
    if (a RT b) {
        printf("%d 大于 %d", a, b);
    } else if (a LT b) {
        printf("%d 小于 %d", a, b);
    } else if (a EQ b) {
        printf("%d 等于 %d", a, b);
    }
}
```

代码执行结果如下：

```text
10 小于 20
```