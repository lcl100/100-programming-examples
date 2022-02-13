# 练习实例72

## 题目

创建一个链表。


## 分析

本题考查的知识点：
- 链表
- 指针
- 结构体
- `printf`和`scanf`函数

分析：
- 本题考查的链表已经涉及数据结构的知识了。

## 代码

```c
#include <stdio.h>
#include <malloc.h>

/**
 * 链表的结构体
 */
typedef struct LNode {
    int data;// 数据域
    struct LNode *next;// 指针域
} LNode, *LinkList;

LinkList createList(int n);

void print(LinkList L);

int main() {
    // 从键盘输入个数
    int n;
    printf("请输入待插入元素的个数：");
    scanf("%d", &n);

    // 调用函数创建链表
    LinkList list = createList(n);

    // 打印链表
    printf("刚才建立的链表中各元素如下：");
    print(list);
}

/**
 * 创建链表并且在链表中插入 n 个指定值
 * @param n 待插入元素的个数
 * @return 创建成功的链表
 */
LinkList createList(int n) {
    // 创建链表的头节点
    LinkList L = (LinkList) malloc(sizeof(LinkList));
    L->next = NULL;
    LinkList temp = L;// 记录链表的最后一个节点

    // 循环从键盘输入数据
    for (int i = 0; i < n; i++) {
        // 创建一个待插入的新节点
        LinkList node = (LinkList) malloc(sizeof(LinkList));
        // 从键盘输入数据
        int num;
        printf("请输入第 %d 个元素的值：", i + 1);
        scanf("%d", &num);
        // 设置数据到新节点中
        node->data = num;
        node->next = NULL;
        // 将新节点插入到原链表中
        temp->next = node;
        temp = node;
    }

    // 返回创建成功的链表
    return L;
}

/**
 * 打印链表
 * @param L 待打印的链表（链表存在头节点）
 */
void print(LinkList L) {
    // 链表的第一个节点
    LinkList node = L->next;
    // 通过 while 循环打印链表
    while (node != NULL) {
        // 打印当前遍历节点的值
        printf("%d\t", node->data);
        // 指向链表的下一个节点
        node = node->next;
    }
}
```

代码执行结果如下：

```text
请输入待插入元素的个数：4

请输入第 1 个元素的值：111
请输入第 2 个元素的值：222
请输入第 3 个元素的值：333
请输入第 4 个元素的值：444

刚才建立的链表中各元素如下：111     222     333     444
```