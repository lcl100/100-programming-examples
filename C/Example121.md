# 练习实例121

## 题目
编写程序，将用户输入的字符串中删除所有的数字，然后输出剩余的字符。


## 分析

本题考查的知识点：
- 字符串
- `printf`和`scanf`函数
- ASCII 码

分析：
- 本题的解法采用了取巧的方法，直接输出非数字字符，而非通用的解法。
- 难点在于如何判断字符串中的字符是否是数字字符，方法是判断字符的ASCII码，如果字符的ASCII码小于'0'字符的ASCII码或者大于'9'字符的ASCII码则表示不是数字字符。


## 代码

```c
#include<stdio.h>
#include<string.h>

int main() {
    // 输入字符串
    char str[10];
    printf("请输入一个字符串：");
    scanf("%s", str);

    // 循环遍历字符串，删除数字，其实是取巧的方法
    int len = strlen(str);// 获取字符串中实际字符个数
    for (int i = 0; i < len; i++) {
        // 循环判断字符串中的每个字符，跳过数字字符进行输出
        if (str[i] < '0' || str[i] > '9') {
            printf("%c", str[i]);
        }
    }
}
```

代码执行结果如下：

```text
请输入一个字符串：hello123world456
helloworld
```