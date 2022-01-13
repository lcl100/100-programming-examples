# 练习实例31

## 题目

请输入星期几的第一个字母来判断一下是星期几，如果第一个字母一样，则继续判断第二个字母。

## 分析

星期一到星期日的英文分别是，星期一：Monday、星期二：Tuesday、星期三：Wednesday、星期四：Thursday、星期五：Friday、星期六：Saturday、星期日：Sunday。

用`case`语句判断第一个字符，而第二个字符可以在判断第一个字符之后判断，如`Tuesday`和`Thursday`的第一个字符相同，所以需要判断第二个字符。

## 代码

```c
#include <stdio.h>

int main() {
    char w;
    printf("请输入第一个字母：\n");
    scanf("%c", &w);

    switch (w) {
        case 'M':
            printf("星期一");
            break;
        case 'T':
            printf("请输入第二个字母：\n");
            getchar();// 吃掉换行符
            scanf("%c", &w);
            if (w == 'u') {
                printf("星期二");
            } else if (w == 'h') {
                printf("星期四");
            } else {
                printf("没有符合的星期");
            }
            break;
        case 'W':
            printf("星期三");
            break;
        case 'F':
            printf("星期五");
            break;
        case 'S':
            printf("请输入第二个字母：\n");
            getchar();// 吃掉换行符
            scanf("%c", &w);
            if (w == 'a') {
                printf("星期六");
            } else if (w == 'u') {
                printf("星期天");
            } else {
                printf("没有符合的星期");
            }
            break;
        default:
            printf("没有符合的星期");
            break;
    }
}
```

代码执行结果如下：

```text
请输入第一个字母：
S
请输入第二个字母：
a
星期六
```