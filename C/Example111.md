# 练习实例111

## 题目

求一个任意边长的矩形面积。矩形的长和宽通过键盘输入。

## 分析

本题考查的知识点：

- `printf`和`scanf`函数
- 矩形面积计算

分析：

- 通过`scanf`函数获取从键盘输入的矩形长和宽。通过`printf`函数输出矩形面积结果
- 矩形面积即是矩形的长和宽的乘积。

## 代码

```c
#include <stdio.h>

int isPrime(int num);

int main() {
    int w, h, area;
    printf("请输入矩形的长和宽：");
    scanf("%d%d", &w, &h);

    area = w * h;// 计算矩形的面积

    printf("矩形面积为：%d", area);
}
```

代码执行结果如下：

```text
请输入矩形的长和宽：5 8
矩形面积为：40
```