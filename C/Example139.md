# 练习实例139

## 题目

实现模拟彩票的程序设计，随机产生6个数字，与用户输入的数字进行比较，输出它们相同的数字个数。使用动态内存分配。


## 分析

本题考查的知识点：
- 指针
- `malloc`与`free`函数
- 字符串
- `printf`与`scanf`函数
- 随机数
- while 循环语句
- if 条件语句

分析：
- 本题难点在于产生随机数，可以利用`rand()`函数完成，而`rand()%10`可以随机产生`[0,9]`之间任意一个数。
- 注意，`toascii()`函数可以将指定数字转换成对应的ASCII码所表示的字符，如`toascii(97)='a'`。要想将数字存放在子串中必须先将数字转换成字符。
- 统计相同的数字个数只需要循环遍历两个字符串，然后相同下标的字符是否相等，如果相等则计数器加1，否则继续判断下一个。


## 代码

```c
#include<stdio.h>
#include<stdlib.h>
#include <ctype.h>
#include <time.h>

int main() {
    // 创建字符串并动态分配内存空间
    char *str = (char *) malloc(sizeof(char) * 6);

    // 赋予随机数
    srand((unsigned) time(NULL));// 如果不指定这句代码那么下面的 rand()%10 产生的结果每次都会相同
    for (int i = 0; i < 6; i++) {
        int num = rand() % 10;// 产生[0,9]之间任何一个的随机数
        *(str + i) = toascii(num + '0');// 除以10表示获取10以内的随机数
    }

    // 接收从键盘输入的6位数字
    printf("请输入一个 6 位数字：");
    char *num = (char *) malloc(sizeof(char) * 6);
    scanf("%s", num);

    // 统计相等的数字个数
    int eqCount = 0;
    char *tStr = str;
    char *tNum = num;
    while (*str != '\0' && *num != '\0') {
        // 循环遍历字符串str中的每个字符，如果相等则计数器加1
        if (*str == *num) {
            eqCount++;
        }
        // 指针前进一步，指向下一个字符继续比较
        str++;
        num++;
    }

    printf("%s 与 %s 中相同的数字个数：%d", tStr, tNum, eqCount);
    free(str);
    free(num);
}
```

代码执行结果如下：

```text
请输入一个 6 位数字：123456
042656 与 123456 中相同的数字个数：2
```