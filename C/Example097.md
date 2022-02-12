# 练习实例97

## 题目

从键盘输入一些字符，逐个把它们送到磁盘上去，直到输入一个#为止。


## 分析

本题考查的知识点：
- `getchar`和`printf`函数
- 文件操作：`fopen`、`fputc`、`fclose`函数等

分析：
- 本题考查的就是从键盘输入大量字符，当输入指定字符时才停止输入。
- 还考查了将字符写入到文件的操作。


## 代码

```c
#include <stdio.h>
#include <string.h>

int main() {
    char name[10];// 文件名
    char c;// 保存输入的字符
    FILE *fp;// 文件指针

    printf("请输入你要保存的文件名：");
    scanf("%s", name);
    getchar();// 吸收掉'\n'符号
    printf("请输入一些字符（以#结尾）：");

    if ((fp = fopen(name, "w")) == NULL) {
        printf("打开 %s 文件失败！");
        return 0;
    }
    while ((c = getchar()) != '#') {
        fputc(c, fp);// 向文件中写入字符
    }
    fclose(fp);
}
```

代码执行结果如下：

```text
请输入你要保存的文件名：text.txt
请输入一些字符（以#结尾）：hello world! I like C!#

hello world! I like C!
```