# 练习实例143

## 题目
自己实现一个比较字符串大小的函数，即实现 strcmp 函数。


## 分析

本题考查的知识点：
- 函数
- 字符串
- 指针
- 一维数组
- `const`关键字
- while 循环语句

分析：
- 同时循环遍历两个待比较的字符串中的所有字符，如果字符相等则继续比较下一对字符；
- 如果不相等则跳出循环，对两个字符作减法运算，如果得到的结果等于0表示两个字符串相等；
- 如果得到的结果大于0则表示前者大于后者；如果得到的结果小于0则表示前者小于后者。
- `const`关键字可以在函数内修改形参指针变量后而不改变函数外实参的值。


## 代码

```c
#include<stdio.h>

int strcmp(const char *str1, const char *str2);

int main() {
    // 声明字符串
    char str1[10] = "hello";
    char str2[10] = "hellowo";

    // 调用函数进行比较
    int result = strcmp(str1, str2);
    printf("%d", result);
}

/**
 * 进行字符串比较
 * @param str1 第一个字符串
 * @param str2 第二个字符串
 * @return 如果字符串相等则返回0，如果大于则返回的数大于0，如果小于则返回的数小于0
 */
int strcmp(const char *str1, const char *str2) {
    while (*str1 != '\0' && *str2 != '\0' && *str1 == *str2) {
        str1++;
        str2++;
    }
    return *str1 - *str2;
}
```

代码执行结果如下：

```text
-119
```