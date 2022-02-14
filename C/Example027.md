# 练习实例27

## 题目

利用递归函数调用方式，将所输入的5个字符，以相反顺序打印出来。


## 分析

本题考查的知识点：
- 函数
- 递归


## 代码

```c
#include <stdio.h>
#include <string.h>

/**
 * 利用递归逆序打印字符串
 * @param str 待打印的字符串
 * @param len 字符串长度
 */
void reversePrint(char str[], int len) {
    if (len >= 1) {
        printf("%c", str[len - 1]);
        reversePrint(str, len - 1);
    }
}

int main() {
    // 从键盘输入字符串
    char str[10];
    printf("请输入一个字符串：");
    scanf("%s", str);

    // 调用函数递归逆序打印字符串，其中strlen()函数可以获取字符串的实际字符个数
    printf("字符串逆序结果：");
    reversePrint(str, strlen(str));
}
```

代码执行结果如下：

```text
请输入一个字符串：hello
字符串逆序结果：olleh
```