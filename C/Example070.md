# 练习实例70

## 题目

写一个函数，求一个字符串的长度，在 main 函数中输入字符串，并输出其长度。

## 分析

循环计算字符串中的每个字符，当不等于`'\0'`字符时表示已经到了字符串尾部，统计结束。

## 代码

```c
#include <stdio.h>

/**
 * 计算字符串的长度
 * @param str 待计算的字符串
 * @return 字符串的长度
 */
int length(char *str) {
    int len = 0;
    while ((*str) != '\0') {
        len++;
        str++;
    }
    return len;
}

int main() {
    char str[20];
    printf("请输入字符串：");
    scanf("%s", &str);

    int len = length(str);
    printf("%d", len);
}
```

函数还可以写成这样利用for循环：

```c
/**
 * 计算字符串的长度
 * @param str 待计算的字符串
 * @return 字符串的长度
 */
int length(char *str) {
int len = 0, i = 0;
for (; str[i] != '\0'; i++) {
len++;
}
return len;
}
```

代码执行结果如下：

```text
请输入字符串：helloworld
10
```