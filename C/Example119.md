# 练习实例119

## 题目
从键盘输入一个十进制整型数据，计算并输出其各位上数字之和（忽略正负号）。例如，输入1234则输出10；输入-1234则输出10。



## 分析

本题考查知识点：
- `printf`和`scanf`函数
- 获取一个整数的每一位数
- while 循环
- 字符串
- 指针

分析：
- 本题的难点在于如何获取到一个正整数的每一位，如 123 的个位是 3、十位是 2、百位是 1。
- 如果我们输入的正整数是123，如果要获取最后一位数字则应该让它对 10 取余，即 123 % 10 = 3，即能够得到个位数字 3。
- 如果我们需要获取到下一位数字，这时就需要将数字除以 10，即 123 / 10 = 12，再让 12 % 10 = 2，即可以得到倒数第二位数字 2。
- 然后继续让 12 / 10 = 1，再让 1 % 10 = 1，就得到了倒数第三位数字 1。
- 此时让 1 / 10 = 0 得到 0 的结果，结束 while 循环，在这个过程中可以统计正整数的位数和逆序输出每一位数字。


## 代码

如果输入的是一个十进制整数，则代码如下：

```c
#include<stdio.h>

int main() {
    // 如果输入的是一个整数
    int num;
    printf("请输入一个十进制整数：");
    scanf("%d", &num);

    // 如果是负数则转换成正数去处理
    if (num < 0) {
        num = -num;
    }

    // 获取每一位的数然后求和
    int sum = 0;// 记录每一位相加的总和
    while (num > 0) {
        // 其中 num%10 可以获取到正整数的每一位
        sum += num % 10;
        num = num / 10;
    }
    printf("%d", sum);
}
```

如果输入的是一个十进制整数字符串，那么可以用如下代码处理：
```c
#include<stdio.h>
#include<stdlib.h>

int main() {
    // 如果输入的是一个十进制整数字符串

    // 创建字符串并为其分配内存空间
    char *str = (char *) malloc(sizeof(char) * 10);

    // 从键盘输入字符串
    printf("请输入一个十进制整数：");
    scanf("%s", str);

    // 如果是负数，即字符串的第一个字符是'-'，则跳过，从第二个字符开始处理
    if (*str == '-') {
        str++;
    }

    // 统计整数字符串中有多少位数字
    int sum = 0;
    while (*str != '\0') {// 循环字符串中的每一位字符，字符串中最后一位字符是'\0'，结束循环
        // *str 可以获取到当前的字符
        // *str-'0' 可以获取这个数字字符实际表示的数字，如'9'-'0'=9
        sum += *str - '0';
        // 字符指针向下一位字符继续
        str++;
    }
    printf("%d", sum);
}
```

代码执行结果如下：

```text
请输入一个十进制整数：1234
10
请输入一个十进制整数：-1234
10
```