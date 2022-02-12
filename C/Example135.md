# 练习实例135

## 题目

字符替换。要求用函数`replace`将用户输入的字符串中的字符`t`（`T`）都替换成`e`（`E`），并返回替换字符的个数。


## 分析

本题考查的知识点：
- 字符串
- 函数
- while 循环语句
- if 条件语句

分析：
- 本题不难，只需要判断字符串中的哪个字符是't'还是'T'即可，如果是则进行替换，并且计数器加2。
- 主要考查字符串和指针的用法。

## 代码

```c
#include<stdio.h>

int replace(char *str);

int main() {
    // 从键盘输入字符串
    char str[100];
    printf("请输入一个字符串：");
    gets(str);

    // 调用函数完成替换
    int result = replace(str);
    printf("%s 中被替换字符个数：%d", str, result);
}

/**
 * 将字符串中的字符`t`（`T`）都替换成`e`（`E`），并返回替换字符的个数
 * @param str 待替换的字符串
 * @return 替换字符的个数
 */
int replace(char *str) {
    int count = 0;// 记录替换字符的个数
    while (*str != '\0') {
        // 判断字符是't'还是'T'，如果是则进行替换
        if (*str == 't') {
            *str = 'e';
            count++;
        } else if (*str == 'T') {
            *str = 'E';
            count++;
        }
        str++;
    }
    return count;
}
```

代码执行结果如下：

```text
请输入一个字符串：tomTT
eomEE 中被替换字符个数：3
```