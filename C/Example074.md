# 练习实例74

## 题目

连接两个链表。

## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- 指针
- 函数
- 链表

分析：
- 本题还是考查的是数据结构中的链表，所谓的合并两个链表这里采用的方法是将两个链表中的所有元素都复制到新链表中，然后返回复制后的新链表。


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

LinkList concat(LinkList L1, LinkList L2);

int main() {
    // 从键盘输入个数
    int n;
    printf("请输入待插入元素的个数：");
    scanf("%d", &n);

    // 调用函数创建链表并打印链表
    LinkList list = createList(n);
    printf("刚才建立的链表中各元素如下：");
    print(list);

    // 合并链表
    LinkList concatList = concat(list, list);
    printf("合并后的链表中各元素如下：");
    print(concatList);
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

LinkList concat(LinkList L1, LinkList L2) {
    // 记录L1和L2链表中的每一个节点
    LinkList node = NULL;

    // 合并两个链表后的新链表
    LinkList L = (LinkList) malloc(sizeof(LinkList));
    L->next = NULL;
    LinkList temp = L;// 记录新链表的每一个节点

    // 将链表L1中的所有节点复制到新链表中
    node = L1->next;// 置为L1链表的第一个节点
    while (node != NULL) {
        // 创建一个新节点，将正在遍历的L1链表的节点的数据域放到新节点中
        LinkList newNode = (LinkList) malloc(sizeof(LinkList));
        newNode->data = node->data;
        newNode->next = NULL;
        // 使用尾插法将新节点插入到新链表中
        temp->next = newNode;
        temp = temp->next;
        // 继续遍历L1链表的下一个节点
        node = node->next;
    }

    // 将链表L2中的所有节点复制到新链表中
    node = L2->next;// 置为L2链表的第一个节点
    while (node != NULL) {
        // 创建一个新节点，将正在遍历的L2链表的节点的数据域放到新节点中
        LinkList newNode = (LinkList) malloc(sizeof(LinkList));
        newNode->data = node->data;
        newNode->next = NULL;
        // 使用尾插法将新节点插入到新链表中
        temp->next = newNode;
        temp = temp->next;
        // 继续遍历L2链表的下一个节点
        node = node->next;
    }

    // 返回合并完成的新链表
    return L;
}
```

代码执行结果如下：

```text
请输入待插入元素的个数：4

请输入第 1 个元素的值：1111
请输入第 2 个元素的值：2222
请输入第 3 个元素的值：3333
请输入第 4 个元素的值：4444

刚才建立的链表中各元素如下：1111    2222    3333    4444
合并后的链表中各元素如下：1111  2222    3333    4444    1111    2222    3333    4444
```