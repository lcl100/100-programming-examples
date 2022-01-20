# 练习实例30

## 题目

一个5位数，判断它是不是回文数。即12321是回文数，个位与万位相同，十位与千位相同。

## 分析

如果只是一个5位数，则可以分别获取万位、千位和个位、十位的数字，然后判断它们是否相等，如果只要有一对不等则表示不是回文数。

或者还可以转换成字符串来处理。

下面的代码是将数的每一位都放到数组中，然后循环数组来判断前后对应下标的数是否相等，这样写扩展性比较好，只需要改变数组的长度就可以判断6位数、7位数等是否是回文数。

## 代码

```c
#include <stdio.h>

int main() {
    int size = 5;// 数的位数，便于扩展为其他位数该程序也可以使用

    int nums[size];// 存放5位数的每一位
    int flag = 1;// 标记输入的数是否是回文数，如果是1则是回文数，是0则不是回文数
    int number;
    printf("请输入一个%d位数：\n", size);
    scanf("%d", &number);

    // 通过循环将数的每一位放到数组中
    for (int i = 0; i < size; i++) {
        // 数的每一位
        int place = number % 10;
        nums[size - i - 1] = place;
        number = number / 10;
    }

    // 然后判断它是否是回文数
    for (int i = 0; i < size / 2; i++) {
        if (nums[i] != nums[size - i - 1]) {
            flag = 0;// 标记为不是回文数
        }
    }

    // 打印结果
    if (flag) {
        printf("这是回文数");
    } else {
        printf("这不是回文数");
    }
}
```

还可以转换成字符串利用指针来完成：
```c
#include <stdio.h>
#include <stdlib.h>

/**
 * 判断一个5位数的数字字符串是否是回文数字
 * @param num 5位数的数字字符串
 * @return 如果是回文数字符串则返回1；如果不是则返回0
 */
int palindrome(char* num) {
    for (int i = 0; i < 5 / 2; i++) {
        // 比较字符是否相等
        if (*(num + i) != *(num + 5 - i - 1)) {
            return 0;
        }
    }
    return 1;
}

int main() {
    int num;
    printf("请输入一个5位数：\n");
    scanf("%d", &num);

    // 定义一个字符串
    char str[5];
    // itoa()是一个函数，用来将整数转换成字符串，第三个参数表示进制
    itoa(num, str, 10);

    printf("%d", palindrome(str));
}
```

代码执行结果如下：

```text
请输入一个5位数：
12321
这是回文数
```