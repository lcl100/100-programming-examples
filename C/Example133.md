# 练习实例133

## 题目

在主函数中初始化一个3行4列的矩阵并将每个元素都输出，然后调用子函数，分别计算每一行的元素之和，将和直接存放在每行的第一个元素中，返回主函数之后输出各行元素的和。


## 分析

本题考查的知识点：
- 二维数组
- 函数
- 嵌套 for 循环

分析：
- 本题不难，只需要能够遍历二维数组并且计算每一行元素的总和即可，主要考查二维数组相关知识。


## 代码

```c
#include<stdio.h>

void sum(int arr[][4], int row, int col);

int main() {
    // 声明一个二维数组
    int arr[3][4] = {{1, 2,  3,  4},
                     {5, 6,  7,  8},
                     {9, 10, 11, 12}};

    // 打印二维数组
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            printf("%d\t", arr[i][j]);
        }
        printf("\n");
    }

    // 调用函数处理二维数组
    sum(arr, 3, 4);

    // 打印二维数组修改后第一列的值
    for (int i = 0; i < 3; i++) {
        printf("%d\n", arr[i][0]);
    }
}

/**
 * 计算每一行的元素之和，将和直接存放在每行的第一个元素中
 * @param arr 二维数组
 * @param row 二维数组行数
 * @param col 二维数组列数
 */
void sum(int arr[][4], int row, int col) {
    for (int i = 0; i < row; i++) {
        // 记录每一行元素的和
        int rowSum = 0;
        for (int j = 0; j < col; j++) {
            rowSum += arr[i][j];
        }
        // 然后将和存放在每行的第一个元素中
        arr[i][0] = rowSum;
    }
}
```

代码执行结果如下：

```text
1       2       3       4
5       6       7       8
9       10      11      12
10
26
42
```