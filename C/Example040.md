# 练习实例40

## 题目

将一个数组逆序输出。


## 分析

本题考查的知识点：
- 数组
- for 循环

分析：
- 可以用取巧的方法直接倒序输出数组。
- 也可以交换数组中第 i 个和第 len-1-i 个元素，原地修改数组。

## 代码

直接逆序输出数组中所有元素：
```c
#include <stdio.h>

int main() {
    int nums[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 0};

    printf("原数组：");
    for (int i = 0; i < 10; i++) {
        printf("%d\t", nums[i]);
    }

    // 直接逆序输出数组中所有元素
    printf("\n逆序数组：");
    for (int i = 9; i >= 0; i--) {
        printf("%d\t", nums[i]);
    }
}
```

原地修改数组元素，来逆序输出数组：
```c
#include <stdio.h>

int main() {
    int nums[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 0};

    printf("原数组：");
    for (int i = 0; i < 10; i++) {
        printf("%d\t", nums[i]);
    }

    // 交换数组中第 i 个和第 len-1-i 个元素，交换 len/2 次，原地修改数组
    for (int i = 0; i < 10 / 5; i++) {
        int temp = nums[i];
        nums[i] = nums[10 - i - 1];
        nums[10 - i - 1] = temp;
    }

    // 直接逆序输出数组中所有元素
    printf("\n逆序数组：");
    for (int i = 0; i < 10; i++) {
        printf("%d\t", nums[i]);
    }
}
```

代码执行结果如下：

```text
原数组：1       2       3       4       5       6       7       8       9       0
逆序数组：0     9       8       7       6       5       4       3       2       1
```