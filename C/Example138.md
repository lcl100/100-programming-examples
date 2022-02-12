# 练习实例138

## 题目

定义一个动态数组，长度为变量n，用随机数给数组各元素赋值，然后对数组各单元排序，定义`swap`函数交换数据单元，要求参数使用指针传递。


## 分析

本题考查的知识点：
- `printf`和`scanf`函数
- for 循环语句
- 获取随机数
- 指针
- 一维数组
- 排序（冒泡排序）

分析：
- 本题比较新颖的地方是生成随机数赋给数组，然后对数组进行排序，排序算法可以自己任意实现，然后利用指针完成元素的交换。


## 代码

```c
#include<stdio.h>
#include<stdlib.h>

void swap(int *a, int *b);

void sort(int a[], int n);

int main() {
    int n, a[10];
    // 从键盘输入数组实际元素个数
    scanf("%d", &n);

    // 为数组实际元素赋予随机数值
    int i, j;
    for (i = 0; i < n; i++) {
        a[i] = rand();
    }

    // 输出随机数
    printf("\n得到的随机数：");
    for (i = 0; i < n; i++) {
        printf("%d\t", a[i]);
    }

    printf("\n从大到小的结果：");
    sort(a, n);// 调用函数进行排序
    for (i = 0; i < n; i++) {
        printf("%d\t", a[i]);
    }

    printf("\n输入你要交换的两个数的下标：");
    scanf("%d%d", &i, &j);
    swap(&a[i], &a[j]);// 调用函数进行交换
    for (i = 0; i < n; i++) {
        printf("%d\t", a[i]);
    }
}

/**
 * 交换任意两个变量的值
 * @param a 一个变量
 * @param b 另一个变量
 */
void swap(int *a, int *b) {
    int t;
    t = *a;
    *a = *b;
    *b = t;
}

/**
 * 对一维数组进行排序，使用的是冒泡排序
 * @param a 一维数组
 * @param n 数组中实际元素个数
 */
void sort(int a[], int n) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (a[j] < a[j + 1]) {
                int t = a[j];
                a[j] = a[j + 1];
                a[j + 1] = t;
            }
        }
    }
}
```

代码执行结果如下：

```text
6
得到的随机数：41        18467   6334    26500   19169   15724
从大到小的结果：26500   19169   18467   15724   6334    41
输入你要交换的两个数的下标：2 4
26500       19169   6334    15724   18467   41
```