# 练习实例88

## 题目

读取7个数（1—50）的整数值，每读取一个值，程序打印出该值个数的*。


## 分析

本题考查的知识点：
- for 循环语句
- `printf`和`scanf`函数
- 嵌套 for 循环

分析：
- 本题很简单，直接输出指定个数的指定字符即可。


## 代码

```c
#include <stdio.h>

/**
 * 输出指定个数的星号
 * @param num 星号的个数
 */
void print(int num) {
    for (int i = 0; i < num; i++) {
        printf("%c", '*');
    }
    printf("\n");
}

int main() {
    int num;
    for (int i = 0; i < 7; i++) {
        printf("请输入一个整数（1-50）：");
        scanf("%d", &num);
        // 判断输入数的范围
        if (num >= 1 && num <= 50) {
            print(num);
        } else {
            printf("请输入符合范围的数字！");
        }
    }
}
```

代码执行结果如下：

```text
请输入一个整数（1-50）：7
*******
请输入一个整数（1-50）：6
******
请输入一个整数（1-50）：5
*****
请输入一个整数（1-50）：4
****
请输入一个整数（1-50）：3
***
请输入一个整数（1-50）：2
**
请输入一个整数（1-50）：1
*
```