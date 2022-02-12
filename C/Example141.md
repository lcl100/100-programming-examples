# 练习实例141

## 题目
编写函数实现，计算一个字符在一个字符串中出现的次数。


## 分析

本题考查的知识点：
- 字符串
- 函数
- `printf`和`scanf`函数
- 指针
- `const`关键字
- while 循环语句
- if 条件语句

分析：
- 循环遍历字符串中的每个字符，如果当前遍历的字符与传入的字符相等，则计数器加1，当遍历到'\0'字符时结束循环。
- 本题不难，难点在于使用指针来表示字符串和`const`关键字。


## 代码

```c
#include<stdio.h>

int stat(const char *str, char c);

int main() {
    // 从键盘输入字符串和字符
    char str[11];
    char c;
    printf("请输入一个字符串：");
    scanf("%s", str);
    getchar();// 吸收掉上面结束有的'\n'换行符，否则会被下面的c接收到
    printf("请输入一个字符：");
    scanf("%c", &c);

    // 调用函数进行统计
    int result = stat(str, c);
    printf("字符 %c 在字符串 %s 中出现了 %d 次", c, str, result);
}

/**
 * 统计字符串 str 中字符 c 的出现次数
 * @param str 字符串
 * @param c 待统计的字符
 * @return 字符 c 的出现次数
 */
int stat(const char *str, char c) {
    int count = 0;// 计数器，统计字符c在字符串中的出现次数
    while (*str != '\0') {
        // 判断当前遍历的字符是否等于字符c，如果相等则计数器加1
        if (*str == c) {
            count++;
        }
        str++;
    }
    return count;
}
```

代码执行结果如下：

```text
请输入一个字符串：helloworld
请输入一个字符：l
字符 l 在字符串 helloworld 中出现了 3 次
```