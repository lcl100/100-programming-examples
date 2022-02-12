# 练习实例140

## 题目

编写函数实现，用指针方式计算字符串的串长。


## 分析

本题考查的知识点：
- `printf`和`scanf`函数
- while 循环语句
- 函数
- 字符串
- 指针
- `const`关键字

分析：
- 在C语言中字符串以字符`'\0'`结尾，遍历字符串，统计字符个数，当遍历到字符`'\0'`时结束循环，统计完成。
- 使用了`const`关键字后在函数内部对字符串指针的遍历，也不会影响函数外面的实参。

## 代码

```c
#include<stdio.h>

int length(const char *str);

int main() {
    // 从键盘输入一个字符串
    char str[10];
    printf("请输入一个字符串：");
    scanf("%s", str);

    // 调用函数并且打印结果
    int len = length(str);
    printf("%s 长度为：%d", str, len);
}

/**
 * 统计字符串的实际字符个数
 * @param str 字符串
 * @return 字符串的实际长度
 */
int length(const char *str) {
    int len = 0;
    while (*str != '\0') {
        len++;
        str++;
    }
    return len;
}
```

代码执行结果如下：

```text
请输入一个字符串：hello
hello 长度为：5
```