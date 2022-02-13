# 练习实例67

## 题目

输入数组，最大的与第一个元素交换，最小的与最后一个元素交换，输出数组。


## 分析

本题考查的知识点：
- 一维数组
- `printf`和`scanf`函数
- for 循环语句
- 求最大值和最小值
- 交换元素

分析：
- 本题考查的还是对一维数组的应用。
- 找到一维数组的最大值，保存它的值和索引；找到一维数组的最小值，保存它的值和索引。
- 然后利用数组下标进行交换即可。

## 代码

```c
#include<stdio.h>

int main() {
    // 从键盘输入10个数
    int nums[10];
    printf("请输入一个数组：");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &nums[i]);
    }

    int maxIndex = 0;// 最大元素的下标
    int max = nums[maxIndex];// 最大元素的值
    int minIndex = 0;// 最小元素的下标
    int min = nums[minIndex];// 最小元素的值
    for (int i = 0; i < 10; i++) {
        // 寻找最大值，并保存值和下标
        if (nums[i] > max) {
            max = nums[i];
            maxIndex = i;
        }
        // 寻找最小值，并保存值和下标
        if (nums[i] < min) {
            min = nums[i];
            minIndex = i;
        }
    }

    // 将最大的与第一个元素交换
    int temp = nums[0];
    nums[0] = max;
    nums[maxIndex] = temp;
    // 最小的与最后一个元素交换
    temp = nums[10 - 1];
    nums[10 - 1] = min;
    nums[minIndex] = temp;

    // 输出数组
    for (int i = 0; i < 10; i++) {
        printf("%d\t", nums[i]);
    }
}
```

代码执行结果如下：

```text
请输入一个数组：3 2 1 4 5 8 6 11 10 7
11      2       7       4       5       8       6       3       10      1
```