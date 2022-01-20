# 练习实例5

## 题目

输入三个整数x,y,z，请把这三个数由小到大输出。

## 分析

想办法把最小的数放到x上，先将x与y进行比较，如果x>y则将x与y的值进行交换，然后再用x与z进行比较，如果x>z则将x与z的值进行交换，这样能使x最小。

## 代码

```c
#include <stdio.h>

int main() {
    int x, y, z, temp;
    printf("请输入三个整数：\n");
    scanf("%d%d%d", &x, &y, &z);

    // 交换值，使得x值最小
    if (x > y) {// 交换x与y的值
        temp = x;
        x = y;
        y = temp;
    }
    if (x > z) {// 交换x与z的值
        temp = x;
        x = z;
        z = temp;
    }
    if (y > z) {// 交换y与z的值
        temp = y;
        y = z;
        z = temp;
    }

    printf("从小到大排序：%d %d %d", x, y, z);
}
```

还可以利用指针来完成，主要是练习下指针的使用：
```c
#include <stdio.h>

void swap(int* a, int* b) {
    int temp;
    temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x, y, z;
    int* a;
    int* b;
    int* c;

    printf("请输入三个整数：\n");
    scanf("%d%d%d", &x, &y, &z);
    a = &x;
    b = &y;
    c = &z;

    if (x > y) {
        swap(a, b);
    }
    if (x > z) {
        swap(a, c);
    }
    if (y > z) {
        swap(b, c);
    }

    printf("按从小到大顺序：%d %d %d", *a, *b, *c);
}
```

代码执行结果如下：

```text
请输入三个整数：
2 3 1
从小到大排序：1 2 3
```