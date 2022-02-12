# 练习实例98

## 题目

从键盘输入一个字符串，将小写字母全部转换成大写字母，然后输出到一个磁盘文件"test"中保存。 输入的字符串以!结束。


## 分析

本题考查的知识点：
- `getchar`和`printf`函数
- 字符串
- for 循环语句
- if 条件语句
- ASCII码
- 文件操作：`fopen`、`fputs`、`fclose`等函数

分析：
- 第一步，从键盘输入一个字符串，并且输入的字符串以'!'字符结尾，即当输入'!'字符后结束用户的输入。所以用`getchar()`方法不断读取输入的单个字符。
- 第二步，将小写字母转换成大写字母，首先要判断字符是否是小写字母，只要字符的ASCII码值在'a'字符和'z'字符之间，即是小写字母。小写字母与大写字母的ASCII码值相差32，如果想要将小写字母转换成大写字母，只需要将小写字母的ASCII码值减去32即可得到对应的大写字母。
- 第三步，将这个字符串写入文件，可以使用`fput()`方法直接写入。


## 代码

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    char c;
    int i = 0;
    printf("请输入一个字符串（以!字符结束）：");
    while ((c = getchar()) != '!') {
        str[i] = c;
        i++;
    }

    // 将小写字母全部转换成大写字母
    int len = strlen(str);
    for (int i = 0; i < len; i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] = str[i] - 32;
        }
    }

    // 将结果输出到test文件中
    FILE *fp;
    if ((fp = fopen("test.txt", "w")) == NULL) {
        printf("打开文件失败！");
        return 0;
    }
    fputs(str, fp);
    fclose(fp);
}
```

代码执行结果如下：

```text
请输入一个字符串（以!字符结束）：hello world!

HELLO WORLD
```