# 练习实例86

## 题目

两个字符串连接程序。


## 分析

本题考查的知识点：
- 字符串
- 指针
- 函数

分析：
- 本题有很多种解法，这里利用的是先创建一个新字符串并分配空间，该字符串的长度为待拼接字符串长度之和。
- 然后将第一个字符串和第二个字符串的所有字符都分别复制到新字符串中，最后返回新字符串。
- 本题综合的考查了函数、指针和字符串的知识，但也有点偏向于数据结构。


## 代码

```c
#include <stdio.h>
#include <string.h>
#include <malloc.h>

char *concat(const char *str1, const char *str2);

int main() {
    char str1[10] = "hello c ";
    char str2[5] = "world";
    char *result;
    result = concat(str1, str2);
    printf("%s", result);
}

/**
 * 连接两个字符串
 * @param str1 第一个字符串
 * @param str2 第二个字符串
 * @return 连接后的字符串
 */
char *concat(const char *str1, const char *str2) {
    // 为新字符串分配内存空间
    char *result = (char *) malloc(sizeof(char) * (strlen(str1) + strlen(str2) + 1));
    char *temp = result;// 保存新字符串的首地址
    // 将str1复制到新字符串中
    while (*str1 != '\0') {
        *result = *str1;
        result++;
        str1++;
    }
    // 将str2复制到新字符串中
    while (*str2 != '\0') {
        *result = *str2;
        result++;
        str2++;
    }
    // 新字符串的最后一个字符是'\0'字符表示结束
    *result = '\0';
    return temp;
}
```

代码执行结果如下：

```text
hello c world
```