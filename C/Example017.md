# 练习实例17

## 题目

输入一行字符，分别统计出其中英文字母、空格、数字和其它字符的个数。

## 分析

题目难点主要在于判断字符类别，可以根据字符的ASCII码值范围来判断，注意字符可以与数字进行运算也可以进行比较。

## 代码

```c
#include <stdio.h>

int main() {
    int letters = 0, spaces = 0, digits = 0, others = 0;
    char c;
    printf("请输入一行字符：\n");

    // 当输入'\n'字符（按回车键）后结束循环，统计输入字符串中字符的个数
    while ((c = getchar()) != '\n') {
        if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z')) { // 判断字母，即英文大写字母和英文小写字母，只需要它的ASCII码值在范围之内即可
            letters++;
        } else if (c >= '0' && c <= '9') {// 判断数字
            digits++;
        } else if (c == ' ') {// 判断空格
            spaces++;
        } else {// 其他字符
            others++;
        }
    }

    printf("字母=%d, 数字=%d, 空格=%d, 其他=%d\n", letters, digits, spaces, others);
}
```

代码执行结果如下：

```text
请输入一行字符：
http://www.baidu.com 123456 HELLO WORLD
字母=25, 数字=6, 空格=3, 其他=5
```