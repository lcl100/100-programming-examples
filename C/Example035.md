# 练习实例35

## 题目

字符串反转，如将字符串 "hello" 反转为 "olleh"。

## 分析

可以利用字符数组来完成字符串中字符的交换。还可以通过指针来实现。

## 代码

利用字符数组完成：

```c
#include <stdio.h>

/**
 * 字符串反转，如"hello world" -> "dlrow olleh"
 * @param str 待反转的字符串
 * @param length 字符串长度
 */
void reverse(char str[], int length) {
    char temp;
    for (int i = 0; i < length / 2; i++) {
        temp = str[i];
        str[i] = str[length - i - 1];
        str[length - i - 1] = temp;
    }
}

int main() {
    char str[] = "hello world";
    printf("交换前：%s\n", str);
    reverse(str, 11);
    printf("交换后：%s\n", str);
}
```

利用指针完成：

```c
#include <stdio.h>

/**
 * 计算字符串的长度
 * @param str 字符串
 * @return 字符串中的字符个数
 */
int length(char *str) {
    // 计数器，记录字符个数
    int len = 0;
    // 字符串末尾的字符是'\0'，但不计算在字符长度之内
    while (*str != '\0') {
        str++;// 指针前进一步
        len++;// 个数加1
    }
    return len;
}

/**
 * 反转字符串
 * @param str 待反转的字符串，指针原地修改
 */
void reverse(char *str) {
    char *tempStr = str;
    // 获取字符串的长度
    int len = length(tempStr);

    // 反转字符串
    char temp;
    for (int i = 0; i < len / 2; i++) {
        temp = *(str + i);
        *(str + i) = *(str + len - i - 1);
        *(str + len - i - 1) = temp;
    }
}

int main() {
    char str[] = "hello world";
    printf("交换前：%s\n", str);
    reverse(str);
    printf("交换后：%s\n", str);
}
```

代码执行结果如下：

```text
交换前：hello world
交换后：dlrow olleh
```