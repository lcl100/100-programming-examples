# 练习实例68

## 题目

有 n个整数，使其前面各数顺序向后移 m 个位置，最后m个数变成最前面的 m 个数。


## 分析

本题考查的知识点：
- `printf`和`scanf`函数
- for 循环语句
- 函数
- 一维数组

分析：
- 本题偏向于数据结构算法。
- 本题的核心在于如何将n个整数的数组中的前 m-1 个元素移动到最后面。如`1 2 3 4 5`向后移动 3 个位置结果是`3 4 5 1 2`。
- 核心算法就是完成三次交换：第一次，交换`1 2`变成`2 1`，数组是`2 1 3 4 5`；第二次，交换`3 4 5`变成`5 4 3`，数组是`2 1 5 4 3`；第三次，交换`2 1 5 4 3`，即结果是`3 4 5 1 2`。
- 所谓的交换就是交换对应下标处的元素，如第 i 个元素（下标）同第 len-i-1 个元素（下标）进行交换。

## 代码

```c
#include <stdio.h>

void move(int nums[], int start, int end);

int main() {
    // 从键盘输入要获得的数据
    int n;
    printf("请输入整数个数：");
    scanf("%d", &n);
    int nums[n];
    printf("请输入 %d 个整数：", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &nums[i]);
    }
    int m;
    printf("请输入要移动的位置个数：");
    scanf("%d", &m);

    // 移动分别要交换三次
    move(nums, 0, m - 2);
    move(nums, m-1, n - 1);
    move(nums, 0, n - 1);

    // 打印移动之后的结果
    printf("移动之后的数组是：");
    for (int i = 0; i < n; i++) {
        printf("%d\t", nums[i]);
    }
}

/**
 * 交换数组中指定下标范围[start, end]之内的所有元素
 * @param nums 一维数组
 * @param start 起始下标
 * @param end 结束下标
 */
void move(int nums[], int start, int end) {
    // 只需要交换 (end-start+1)/2 次
    for (int i = 0; i < (end - start + 1) / 2; i++) {
        int temp = nums[start + i];
        nums[start + i] = nums[end - i];
        nums[end - i] = temp;
    }
}
```

代码执行结果如下：

```text
请输入整数个数：5
请输入 5 个整数：1 2 3 4 5
请输入要移动的位置个数：3
移动之后的数组是：3    4       5       1       2
```