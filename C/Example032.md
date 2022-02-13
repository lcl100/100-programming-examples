# 练习实例32

## 题目

删除一个字符串中的指定字母，如：字符串 "aca"，删除其中的 a 字母。


## 分析

分析：
- 本题采用了取巧的方法，直接输出不是待删除字符的字符。

## 代码

```c
#include <stdio.h>
#include <string.h>

int isPrime(int num);

int main() {
    char str[11];
    char c;
    printf("请输入一个字符串：");
    scanf("%s", str);
    getchar();// 吸收掉'\n'换行符
    printf("请输入待删除的字符：");
    scanf("%c", &c);

    // 直接输出不是待删除字符的字符
    int len = strlen(str);// 获取字符串中实际字符个数
    for (int i = 0; i < len; i++) {
        if (str[i] != c) {// 如果不是待删除的字符则进行输出
            printf("%c", str[i]);
        }
    }
}
```

代码执行结果如下：

```text
请输入一个字符串：aca
请输入待删除的字符：a
c
```