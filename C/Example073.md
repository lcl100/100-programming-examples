# 练习实例73

## 题目

反向输出一个链表。


## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- 指针
- 函数
- 链表

分析：
- 本题还是考查的是数据结构中的链表，不过生成逆序链表只是将原链表中的所有元素重新通过头插法插入到新链表中。

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

LinkList reverse(LinkList L);

int main() {
    // 从键盘输入个数
    int n;
    printf("请输入待插入元素的个数：");
    scanf("%d", &n);

    // 调用函数创建链表并打印链表
    LinkList list = createList(n);
    printf("刚才建立的链表中各元素如下：");
    print(list);

    // 生成逆序链表并打印链表
    LinkList reverseList = reverse(list);
    printf("逆序链表各元素如下：");
    print(reverseList);
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
    printf("\n");
}

/**
 * 生成链表的逆序链表
 * @param L 正序链表
 * @return 逆序链表
 */
LinkList reverse(LinkList L) {
    // 正序链表的第一个节点
    LinkList node = L->next;

    // 创建逆序链表，即逆序链表的第一个节点
    LinkList RL = (LinkList) malloc(sizeof(LinkList));
    RL = NULL;

    // 循环遍历正序链表的所有节点
    while (node != NULL) {
        // 正序链表的节点数据
        int data = node->data;
        // 创建一个新节点，该节点的数据即当前正在遍历的正序链表的节点数据
        LinkList newNode = (LinkList) malloc(sizeof(LinkList));
        newNode->next = NULL;
        newNode->data = data;
        // 采用头插法，但这里没有头节点
        newNode->next = RL;
        RL = newNode;
        // 继续正序链表的下一个节点
        node = node->next;
    }

    // 因为上面创建的逆序链表没有头节点，所以要在最后添加一个头节点
    LinkList head = (LinkList) malloc(sizeof(LinkList));
    head->next = RL;

    // 返回创建成功的逆序链表
    return head;
}
```

代码执行结果如下：

```text
请输入待插入元素的个数：3

请输入第 1 个元素的值：111
请输入第 2 个元素的值：222
请输入第 3 个元素的值：333

刚才建立的链表中各元素如下：111   222     333
逆序链表各元素如下：333   222     111
```