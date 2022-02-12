# 练习实例130

## 题目
用指针的方法，把输入的一个字符串按逆序重新排序其字符，并输出。


## 分析

本题考查的知识点：
- `printf`和`scanf`函数
- 字符串
- 指针

分析：
- 本题的难点在于如何逆转字符串，如`abcd`：可以交换第1位和第4位的字符（即`dbca`）；然后交换第2位和第3位的字符（即`dcba`）。
- 所以逆转字符串只需要交换 i 和 len-1-i 下标所表示的字符，交换 len/2 次即可。
- 同 Example126 题一样，只是本题采用指针去访问和修改字符串中的字符。

## 代码

```c
#include <stdio.h>
#include <string.h>

int main() {
    // 从键盘输入字符串
    char str[10];
    printf("请输入一个字符串：");
    scanf("%s", str);

    int len = strlen(str);// 获取字符串中实际字符个数
    // 交换字符串中 i 和 len-i-1 对应下标的字符，交换 len/2 次
    for (int i = 0; i < len / 2; i++) {
        char temp = *(str + i);
        *(str + i) = *(str + len - i - 1);
        *(str + len - i - 1) = temp;
    }

    printf("逆序重排字符串：%s", str);
}
```

代码执行结果如下：

```text
请输入一个字符串：helloworld
逆序重排字符串：dlrowolleh
```