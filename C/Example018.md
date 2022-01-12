# 练习实例

## 题目

求s=a+aa+aaa+aaaa+aa...a的值，其中a是一个数字。例如2+22+222+2222+22222(此时共有5个数相加)，几个数相加有键盘控制。

## 分析

关键是计算出每一项的值，可以写一个函数来专门计算。

## 代码

```c
#include <stdio.h>

/**
 * 生成重复数，如生成3个重复2得到222
 * @param num 指定数
 * @param count 重复次数
 * @return 生成的重复数
 */
int repeatNumber(int num, int count) {
    int number = num;
    for (int i = 1; i < count; i++) {
        num = num * 10;
        number += num;
    }
    return number;
}

int main() {
    int a, n, sum = 0;
    printf("请输入a和n：\n");
    scanf("%d%d", &a, &n);

    for (int i = 1; i <= n; i++) {
        // 计算和
        sum += repeatNumber(a, i);
    }
    printf("a+aa+...=%d\n", sum);
}
```

代码执行结果如下：

```text
请输入a和n：
2 5
a+aa+...=24690
```