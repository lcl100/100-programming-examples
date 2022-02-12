# 练习实例126

## 题目
把输入的一个字符串按逆序重新排序其字符并输出。


## 分析

本题考查的知识点：
- 字符串
- `printf`和`scanf`函数
- 逆转字符串

分析：
- 本题的难点在于如何逆转字符串，如`abcd`：可以交换第1位和第4位的字符（即`dbca`）；然后交换第2位和第3位的字符（即`dcba`）。
- 所以逆转字符串只需要交换 i 和 len-1-i 下标所表示的字符，交换 len/2 次即可。


## 代码

```c
#include <stdio.h>
#include <string.h>

int main() {
    // 输入一个字符串
    char str[10];
    printf("请输入一个字符串：");
    scanf("%s", str);

    // 交换字符串中对应位置的字符，完成字符串的逆转
    int len = strlen(str);// 获取字符串中实际字符个数
    for (int i = 0; i < len / 2; i++) {
        char temp = str[i];
        str[i] = str[len - 1 - i];
        str[len - 1 - i] = temp;
    }

    printf("逆序字符串：%s", str);
}
```

代码执行结果如下：

```text
请输入一个字符串：helloworld
逆序字符串：dlrowolleh
```