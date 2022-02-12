# 练习实例142

## 题目

编程序，用指针数组在主函数中输入十个等长的字符串。用另一个函数对它们排序，然后在主函数中输出10个已经排好序的字符串。


## 分析

本题考查的知识点：
- 函数
- `printf`和`scanf`函数
- 指针
- 指针数组
- 字符串
- 二维数组
- for 循环语句
- if 条件语句
- 排序（冒泡排序）
- `strcmp`函数

分析：
- 本题的难点在于如何用字符指针数组来表示字符串数组，然后通过键盘输入字符串。
- 至于对字符串数组排序这里是通过冒泡排序实现的。
- `strcmp`函数比较的是字符的ASCII码，如果相等则返回0，如果大于则返回1，如果小于则返回-1。


## 代码

```c
#include<stdio.h>
#include<string.h>

void sort(char *strs[10]);

int main() {
    // 从键盘输入10个字符串
    char s[10][100];
    char *strs[10];
    for (int i = 1; i <= 10; i++) {
        printf("请输入第 %d 个字符串：", i);
        scanf("%s", s[i - 1]);
        strs[i - 1] = s[i - 1];
    }

    // 调用函数进行排序
    sort(strs);

    // 输出排序后的字符串
    for (int i = 0; i < 10; i++) {
        printf("%s\n", strs[i]);
    }
}

/**
 * 对字符串数组进行排序
 * @param strs 字符串数组
 */
void sort(char *strs[10]) {
    for (int i = 0; i < 10; i++) {
        for (int j = i + 1; j < 10; j++) {
            if (strcmp(strs[i], strs[j]) > 0) {
                char *temp = strs[i];
                strs[i] = strs[j];
                strs[j] = temp;
            }
        }
    }
}
```

代码执行结果如下：

```text
请输入第 1 个字符串：hello
请输入第 2 个字符串：world
请输入第 3 个字符串：tom
请输入第 4 个字符串：jack
请输入第 5 个字符串：java
请输入第 6 个字符串：c++
请输入第 7 个字符串：c
请输入第 8 个字符串：python
请输入第 9 个字符串：javascript
请输入第 10 个字符串：mysql
c
c++
hello
jack
java
javascript
mysql
python
tom
world
```