# 练习实例37

## 题目

对 10 个数进行排序。


## 分析

本题考查的知识点：
- 一维数组
- `printf`和`scanf`函数
- 排序（冒泡排序）

分析：
- 本题考查的知识点就是排序。这里采用的是冒泡排序算法，也可以采用其他排序算法。


## 代码

```c
#include <stdio.h>

void sort(int nums[], int len);

int main() {
    int nums[10];
    int len = 10;
    printf("请输入10个元素：");
    for (int i = 0; i < len; i++) {
        scanf("%d", &nums[i]);
    }

    // 调用函数进行排序
    sort(nums, len);

    printf("排序后的数组：");
    for (int i = 0; i < len; i++) {
        printf("%d\t", nums[i]);
    }
}

/**
 * 对数组进行排序，采用的是冒泡排序算法
 * @param nums 待排序的一维数组
 * @param len 数组实际元素个数
 */
void sort(int nums[], int len) {
    for (int i = 0; i < len - 1; i++) {
        for (int j = 0; j < len - 1 - i; j++) {
            if (nums[j] > nums[j + 1]) {
                int temp = nums[j];
                nums[j] = nums[j + 1];
                nums[j + 1] = temp;
            }
        }
    }
}
```

代码执行结果如下：

```text
请输入10个元素：2 5 8 9 1 0 2 4 7 6

排序后的数组：0        1       2       2       4       5       6       7       8       9
```