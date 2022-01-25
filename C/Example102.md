# 练习实例102

## 题目

1、在函数中进行10个学生成绩从高到低排名`sort(int a[10])`。

2、改进第一步的函数为`sort(int a[], int n)`，进行n个学生成绩从高到低排名。

3、改进第二步的函数为`sort(int a[], int n, char style)`，将n个学生成绩从高到低排名。

4、根据`sort()`函数的style参数进行，如style为'a'按升序排，style为'd'按降序排。

> 说明：a表示ascending升序；d表示descending降序。


## 分析
第一步，从高到低排序的排序函数`sort(int a[10])`如下：
```c
/**
 * 对数组进行冒泡排序，从大到小
 * @param a 待排序的数组
 */
void sort(int a[10]) {
    for (int i = 0; i < 10; i++) {
        // 对待排序序列进行冒泡排序
        for (int j = 0; j + 1 < 10 - i; j++) {
            // 相邻元素进行比较，当顺序不正确时，交换位置
            if (a[j] < a[j + 1]) {
                int temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }
}
```

第二步，指定数组长度，进行n个学生成绩从高到低排序的函数`sort(int a[], int n)`如下：
```c
/**
 * 对数组进行冒泡排序，从大到小
 * @param a 待排序的数组
 * @param n 数组长度
 */
void sort(int a[], int n) {
    for (int i = 0; i < n; i++) {
        // 对待排序序列进行冒泡排序
        for (int j = 0; j + 1 < n - i; j++) {
            // 相邻元素进行比较，当顺序不正确时，交换位置
            if (a[j] < a[j + 1]) {
                int temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }
}
```

第三步，继续改进排序函数，添加style参数，如果style参数为'a'则升序，如果style参数为'd'则降序，所以`sort(int a[], int n, char style)`如下：
```c
/**
 * 对数组进行冒泡排序，从大到小
 * @param a 待排序的数组
 * @param n 数组长度
 * @param style 如果传入'a'则按升序排序，如果传入'd'则按降序排序
 */
void sort(int a[], int n, char style) {
    for (int i = 0; i < n; i++) {
        // 对待排序序列进行冒泡排序
        for (int j = 0; j + 1 < n - i; j++) {
            // 相邻元素进行比较，当顺序不正确时，交换位置
            // 并判断style来决定是升序排序还是降序排序
            if (style == 'a') {
                // 其实就只是下面这个符号变了而已
                if (a[j] > a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            } else if (style == 'd') {
                if (a[j] < a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
    }
}
```

## 代码

```c
#include <stdio.h>

void sort(int a[], int n, char style);

int main() {
    int count;
    printf("请输入待添加的学生成绩个数：");
    scanf("%d", &count);

    int nums[count];
    printf("请输入%d个学生成绩：", count);
    for (int i = 0; i < count; i++) {
        scanf("%d", &nums[i]);
    }

    // 升序排序
    sort(nums, count, 'a');
    printf("升序排序：");
    for (int i = 0; i < count; i++) {
        printf("%d\t", nums[i]);
    }

    // 降序排序
    sort(nums, count, 'd');
    printf("\n降序排序：");
    for (int i = 0; i < count; i++) {
        printf("%d\t", nums[i]);
    }
}

/**
 * 对数组进行冒泡排序，从大到小
 * @param a 待排序的数组
 * @param n 数组长度
 * @param style 如果传入'a'则按升序排序，如果传入'd'则按降序排序
 */
void sort(int a[], int n, char style) {
    for (int i = 0; i < n; i++) {
        // 对待排序序列进行冒泡排序
        for (int j = 0; j + 1 < n - i; j++) {
            // 相邻元素进行比较，当顺序不正确时，交换位置
            // 并判断style来决定是升序排序还是降序排序
            if (style == 'a') {
                // 其实就只是下面这个符号变了而已
                if (a[j] > a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            } else if (style == 'd') {
                if (a[j] < a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
    }
}
```

代码执行结果如下：

```text
请输入待添加的学生成绩个数：5
请输入5个学生成绩：1 3 2 8 6
升序排序：1      2       3       6       8
降序排序：8     6       3       2       1
```