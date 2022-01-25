# 练习实例103

## 题目

1、定义一个数组stu[10]存放10个学生的成绩，从键盘输入数据，要求用指针实现。

2、将数组stu[10]的内容输出到屏幕上，要求用指针实现。

3、将成绩数组按照从高到低进行排序，要求用指针实现。

4、将第三步内容放在函数中实现，在主函数中调用实现排序，用指针实现，输出排序后的成绩单。

5、采用指针方法，输入字符串"student score"，复制该字符串并输出（复制字符串采用库函数或者用户自定义函数）。

## 分析

本题考查的是指针。

## 代码

```c
#include <stdio.h>
#include <stdlib.h>

void print(int *nums, int n);

void sort(int a[], int n, char style);

char *copyStr(char src[], int srcLength);

int main() {
    // 定义一个数组存放10个学生的成绩
    int score[10];
    int *stu;
    stu = score;

    // 从键盘输入数据
    printf("请输入10个学生的成绩：");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &score[i]);
    }

    // 打印数组
    print(stu, 10);

    // 排序
    sort(stu, 10, 'a');

    // 打印数组
    print(stu, 10);

    // 复制字符串
    char *src = "student score";
    char *dest;
    dest = copyStr(src, 13);
    puts(dest);
    puts(src);
}

/**
 * 打印数组
 * @param nums 待打印的数组
 * @param n 数组长度
 */
void print(int nums[], int n) {
    printf("\n");
    for (int i = 0; i < n; i++) {
        printf("%d\t", *(nums + i));
    }
    printf("\n");
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
                if (*(a + j) > *(a + j + 1)) {
                    int temp = *(a + j);
                    *(a + j) = *(a + j + 1);
                    *(a + j + 1) = temp;
                }
            } else if (style == 'd') {
                if (*(a + j) < *(a + j + 1)) {
                    int temp = *(a + j);
                    *(a + j) = *(a + j + 1);
                    *(a + j + 1) = temp;
                }
            }
        }
    }
}

/**
 * 复制字符串
 * @param src 源字符串
 * @param srcLength 源字符串长度
 * @return 返回复制后的字符串
 */
char *copyStr(char src[], int srcLength) {
    char *dest = (char *) malloc(sizeof(char) * srcLength);
    for (int i = 0; i < srcLength; i++) {
        *(dest + i) = *(src + i);
    }
    return dest;
}
```

代码执行结果如下：

```text
请输入10个学生的成绩：1 2 3 4 5 6 7 5 6 2

1       2       3       4       5       6       7       5       6       2

1       2       2       3       4       5       5       6       6       7
student score
student score
```