# 练习实例134

## 题目

计算字符串中子串出现的次数。要求：用一个子函数`subString()`实现，参数为指向字符串和要查找的子串的指针，返回次数。


## 分析

本题考查的知识点：
- 字符串
- `printf`和`scanf`函数
- 函数
- 指针

分析：
- 本题偏向于数据结构，着重于指针语法。
- 遍历字符串中的每个字符，从该字符开始与子串的字符相比较，如果完全匹配则出现次数加1，如果出现不匹配则继续比较字符串的下一个字符。
- 注意由于使用了指针所以要恢复子串的初始地址和字符串的下一个字符的地址。


## 代码

```c
#include<stdio.h>

int subString(const char *str, const char *substr);

int main() {
    // 从键盘输入字符串和子串
    char str[100], substr[100];
    printf("请输入一个字符串：");
    scanf("%s", str);
    printf("请输入一个待判断的子字符串：");
    scanf("%s", substr);

    // 调用函数统计子串出现次数
    int result = subString(str, substr);
    printf("%s 在 %s 中出现了 %d 次", substr, str, result);
}

/**
 * 计算字符串中子串出现的次数
 * @param str 字符串
 * @param substr 子串
 * @return 子串的出现次数
 */
int subString(const char *str, const char *substr) {
    int count = 0;// 记录子串的出现次数
    const char *tstr = str;// 保存字符串str
    const char *tsubstr = substr;// 保存子串substr

    // 循环遍历字符串str中的每个字符，用来匹配子串
    while (*str != '\0') {
        // 从当前字符开始，比较后面的字符是否与子串的每个字符相等
        while (*tstr == *tsubstr && *tsubstr != '\0') {
            tstr++;// 字符串tstr指针前进一步
            tsubstr++;// 子串tsubstr指针前进一步
        }
        // 统计子串的出现次数，当tsubstr遍历完成表示子串匹配成功一次
        if (*tsubstr == '\0') {
            count++;
        }
        // 恢复tstr和tsubstr
        tsubstr = substr;// 由于tsubstr指针向后移动了，所以要恢复初始子串地址
        str++;
        tstr = str;// 而tstr指针要指向字符串的下个字符，并且开始匹配子串
    }
    return count;
}
```

代码执行结果如下：

```text
请输入一个字符串：helloworldhello
请输入一个待判断的子字符串：hello
hello 在 helloworldhello 中出现了 2 次
```