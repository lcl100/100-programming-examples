# 练习实例96

## 题目
计算字符串中子串出现的次数。


## 分析

本题考查的知识点：
- `printf`和`scanf`函数
- for 和 while 循环语句
- if 语句
- `strlen`函数

分析：
- 本题偏向于数据结构。
- 判断子串是否在字符串中出现，从字符串中的每一个字符开始同子串的每个字符相比较。
- 如果该字符及之后的所有字符能够完全匹配子串中的所有字符，则算匹配成功一次。
- 如果在匹配过程中发现不匹配，则继续判断字符串中的下一个字符，直到判断到字符串的最后一个字符（其实没必要判断到字符串的最后一个字符）。


## 代码

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];// 字符串
    char substr[10];// 子串

    // 从键盘输入字符串和子串
    printf("请输入字符串：");
    scanf("%s", str);
    printf("请输入子串：");
    scanf("%s", substr);

    int strL = strlen(str);// 字符串长度
    int substrL = strlen(substr);// 子串长度
    int count = 0;// 子串在字符串中的出现次数
    // 最多只需要循环 strL-substrL 次
    for (int i = 0; i <= strL - substrL; i++) {
        int j = 0;// 子串的下标
        int k = i;// 字符串的匹配下标
        while (j < substrL && str[k] == substr[j]) {
            j++;
            k++;
        }
        // 如果j的值等于子串的长度时，表示成功匹配一次，则计数器加1
        if (j == substrL) {
            count++;
        }
    }
    // 打印结果
    printf("%s 在 %s 中出现了 %d 次", substr, str, count);
}
```

代码执行结果如下：

```text
请输入字符串：helloworldhello
请输入子串：hello
hello 在 helloworldhello 中出现了 2 次
```