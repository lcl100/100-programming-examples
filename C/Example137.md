# 练习实例137

## 题目

有 5 个字符串，首先将它们按照字符串中的字符个数由小到大排列，再分别取出每个字符串的第三个字母合并成一个新的字符串输出（若少于三个字符的输出空格）。要求：利用字符串指针和指针数组实现。


## 分析

本题考查的知识点：
- 二维数组
- 字符串数组
- 字符串
- 排序（冒泡排序）
- `gets`、`printf`、strlen`、`strcpy`函数等
- for 循环语句
- if 条件语句

分析：
- 本题难点在于排序，这里使用的是冒泡排序，根据字符串的长度进行冒泡排序。
- 本题难点在于字符串数组的声明和使用。

## 代码

```c
#include<stdio.h>
#include<string.h>

void sort(char strs[5][100]);

int main() {
    // 从键盘输入指定个数的字符串
    char strs[5][100];
    for (int i = 0; i < 5; i++) {
        printf("请输入第 %d 个字符串：", i + 1);
        gets(strs[i]);
    }

    // 调用函数进行排序
    sort(strs);

    // 分别取出每个字符串的第三个字母合并成一个新的字符串输出（若少于三个字符的输出空格）
    char newStr[5];
    for (int i = 0; i < 5; i++) {
        if (strlen(strs[i]) >= 3) {
            newStr[i] = strs[i][2];
        } else {
            newStr[i] = ' ';
        }
    }
    printf("%s", newStr);
}

/**
 * 对字符串数组进行排序，按照字符串长度进行排序
 * 下面使用的是冒泡排序
 * @param strs 待排序的字符串数组
 */
void sort(char strs[5][100]) {
    for (int i = 0; i < 5; i++) {
        for (int j = i + 1; j < 5; j++) {
            if (strlen(strs[i]) > strlen(strs[j])) {
                // 交换字符串strs[i]和strs[j]中的值
                char temp[100];
                strcpy(temp, strs[i]);
                strcpy(strs[i], strs[j]);
                strcpy(strs[j], temp);
            }
        }
    }
}
```

代码执行结果如下：

```text
请输入第 1 个字符串：hellotom
请输入第 2 个字符串：bc
请输入第 3 个字符串：tom
请输入第 4 个字符串：jack
请输入第 5 个字符串：java
 mcvl
```