# 练习实例131

## 题目
用指针的方法，将键盘输入的两个字符串连接起来形成一个新的字符串。


## 分析

本题考查的知识点：
- 字符串
- `printf`和`scanf`函数
- 指针

分析：
- 本题比较偏向于数据结构。
- 拼接字符串就是将 str2 中的所有字符拼接到 str1 后面，通过指针来完成。
- 由于会将字符串 str2 拼接在字符串 str1 上，所以需要先跳到 str1 字符串的末尾处。
- 再循环 str2 字符串中的每个字符，然后添加到 str1 字符串的末尾处，然后 str1 和 str2 指针不断前进并插入。


## 代码

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // 创建指针变量并分配内存空间
    char *str1;
    str1 = (char *) malloc(sizeof(char) * 20);
    char *str2;
    str2 = (char *) malloc(sizeof(char) * 10);

    // 从键盘输入字符串
    printf("请输入字符串1：");
    scanf("%s", str1);
    printf("请输入字符串2：");
    scanf("%s", str2);
    char *temp = str1;// 保存str1的地址

    // 由于会将字符串 str2 拼接在字符串 str1 上，所以需要先跳到 str1 字符串的末尾处
    while (*str1 != '\0') {
        str1++;
    }
    // 再循环 str2 字符串中的每个字符，然后添加到 str1 字符串的末尾处，然后 str1 和 str2 指针不断前进并插入
    while (*str2 != '\0') {
        *str1 = *str2;
        str1++;
        str2++;
    }

    printf("新字符串：%s", temp);
}
```

代码执行结果如下：

```text
请输入字符串1：hello
请输入字符串2：world
新字符串：helloworld
```