# 练习实例78

## 题目

找到年龄最大的人，并输出。


## 分析

本题考查的知识点：
- 结构体
- 结构体数组
- 求最大值

分析：
- 循环遍历结构体数组，根据年龄寻找最大年龄的人即可。


## 代码

```c
#include <stdio.h>

typedef struct {
    char name[4];
    int age;
} Person;

int main() {
    Person persons[3] = {{"tom",  18},
                         {"jack", 22},
                         {"rose", 21}};

    // 保存年龄最大的人
    Person max = persons[0];
    // 循环数组，判断年龄最大的人
    for (int i = 0; i < 3; i++) {
        // 根据年龄比较
        if (persons[i].age > max.age) {
            max = persons[i];
        }
    }

    printf("年龄最大的人：%s-%d", max.name, max.age);
}
```

代码执行结果如下：

```text
年龄最大的人：jack-22
```