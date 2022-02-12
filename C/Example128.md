# 练习实例128

## 题目
编写一个函数，求一维数组的平均值和最大值。


## 分析

本题考查的知识点：
- 一维数组
- 指针
- 函数
- for 循环
- 求最大值和平均值

分析：
- 本题的难点在于给函数传递指针变量来保存一维数组的最大值和平均值。
- 求一维数组的最大值就是先将第一个元素当作最大值，循环遍历一维数组的每个元素与最大值比较，如果大于最大值则将当前元素置为最大值，否则继续比较下一个元素。
- 求一维数组的平均值就是先求出一维数组所有元素的总和，然后除以数组元素个数。



## 代码

```c
#include <stdio.h>

void calculate(int nums[], int len, int *max, float *avg);

int main() {
    // 定义数组、变量、指针变量
    int arr[] = {3, 5, 7, 9, 2, 8, 6};
    int len = 7;
    int x;
    float y;
    int *max = &x;
    float *avg = &y;

    // 调用函数传递参数
    calculate(arr, len, &x, &y);
    printf("最大值：%d\n平均值：%.2f\n", *max, *avg);
}

/**
 * 求一维数组的平均值和最大值
 * @param nums 一维数组
 * @param len 数组长度
 * @param max 保存一维数组的最大值
 * @param avg 保存一维数组的平均值
 */
void calculate(int nums[], int len, int *max, float *avg) {
    // 暂时将一维数组的第一个元素作为最大值
    *max = nums[0];
    // 记录一维数组中所有元素的总和
    int sum = 0;
    // 循环遍历一维数组中的每个元素
    for (int i = 0; i < len; i++) {
        // 计算总和
        sum += nums[i];
        // 如果当前元素比最大值大，则将最大值置为当前元素
        if (nums[i] > *max) {
            *max = nums[i];
        }
    }
    // 计算品均值，使用指针变量保存
    *avg = sum / len;
}
```

代码执行结果如下：

```text
最大值：9
平均值：5.00
```