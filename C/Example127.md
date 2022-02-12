# 练习实例127

## 题目
编写一个函数，求二维数组所有元素的和，要求二维数组的行、列以及数组通过函数参数传递，并通过主函数调用求2行3列的数组的所有元素之和。


## 分析

本题考查的知识点：
- 二维数组
- 嵌套 for 循环
- 函数

分析：
- 本题就是考查二维数组的遍历和函数的声明。

## 代码

```c
#include <stdio.h>

int sum(int row, int col, int arr[2][3]);

int main() {
    // 声明二维数组
    int arr[2][3] = {{1, 2, 3},
                     {4, 5, 6}};
    // 调用sum函数
    int result = sum(2, 3, arr);
    printf("%d", result);
}

/**
 * 计算二维数组中所有元素之和
 * @param row 行数
 * @param col 列数
 * @param arr 二维数组
 * @return 所有元素之和
 */
int sum(int row, int col, int arr[2][3]) {
    // 记录所有元素之和
    int result = 0;
    // 双层for循环
    for (int i = 0; i < row; i++) {
        for (int j = 0; j < col; j++) {
            result += arr[i][j];
        }
    }
    return result;
}
```

代码执行结果如下：

```text
21
```