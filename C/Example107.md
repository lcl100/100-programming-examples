# 练习实例107

## 题目

学生成绩管理系统（利用链表完成）。需要完成下列功能：

1、输入：函数`input`把20个学生的学号、姓名、性别、年龄、四科成绩以及平均成绩和总成绩放在一个结构体数组中，学生的学号、姓名、四科成绩成绩由键盘输入，然后计算出平均成绩和总成绩放在结构体对应的域中。

2、插入：`insert`函数输入一个学生的记录，按学号的先后顺序插入该学生的全部内容。

3、排序：`sort`函数对所有学生按要求排序（学号、总成绩），并输出。

4、查找：`find`函数输入一个学生的学号或姓名，找到该学生并输出该学生的全部内容。要求能查询多次。

5、删除：`delete`函数输入一个学生的学号或姓名，找到该学生并删除该学生的全部内容。

6、输出：函数`output`输出全部学生的记录。

7、`main`：调用所有函数，并且实现全部函数功能。（注：除了定义结构之外，不允许使用全局变量，函数之间的数据全部使用参数传递。）


## 分析

利用单链表来实现：

- 插入：向链表中插入元素，题目要求是按照学号顺序插入，所以要先找到插入元素应该在链表中的位置，注意在链表中插入一个新节点需要知道待插入节点的前驱节点，然后将前驱节点的 next 指针指向新节点，新节点的 next 指针指向查找到的节点。
- 排序：排序就是按照学号或者总成绩排序，这里使用的是冒泡排序。但链表排序比较麻烦，这里使用的方式是将链表中的所有节点的数据域保存到一个数组中，然后对这个数组进行排序，最后根据这个排好序的数组生成一个新的链表，新生成的链表中的节点必然是有序的。
- 查找：即遍历链表中的所有节点，再查找到某个元素。注意，比较字符串是否相等使用了`strcmp()`函数，该函数表示如果两个字符串相等则返回0。
- 删除：首先要按照学号或者姓名找到待删除元素在链表中的节点，然后将待删除节点的前驱节点的 next 指针指向待删除节点的后继节点。
- 输出：即遍历整个单链表。

> 注：该单链表是有头节点的。

## 代码

```c
#include <stdio.h>
#include <string.h>
#include <malloc.h>

#define MAXSIZE 20

typedef struct {
    float math;// 数学
    float chinese;// 语文
    float english;// 英语
    float music;// 音乐
} Course;

typedef struct {
    int number;// 学号
    char name[10];// 姓名
    char gender[1];// 性别
    int age;// 年龄
    Course course;// 四门课程
    float avg;// 平均成绩
    float sum;// 总成绩
} Student;

typedef struct StudentNode {
    Student data;// 数据域
    struct StudentNode *next;// 指针域
} StudentNode, *StudentList;

StudentList input(int count);

void output(StudentList L);

void insert(StudentList L);

Student findByName(StudentList L, char name[]);

Student findByNumber(StudentList L, int number);

void deleteByNumber(StudentList L, int number);

void deleteByName(StudentList L, char name[]);

StudentList sortByTotalScore(StudentList L);

StudentList sortByNumber(StudentList L);

void print(Student student);

Student create();

int length(StudentList L);

int main() {
    setbuf(stdout, NULL);
    // 定义一个20个学生的结构体数组
    int count = 2;
    StudentList L = input(count);
    output(L);

    insert(L);
    output(L);

    printf("根据总成绩排序：\n");
    StudentList sort1 = sortByTotalScore(L);
    output(sort1);

    printf("根据学号排序：\n");
    StudentList sort2 = sortByNumber(L);
    output(sort2);

    printf("根据学号查询学生：\n");
    Student stu1 = findByNumber(L, 101);
    print(stu1);

    printf("根据姓名查询学生：\n");
    Student stu2 = findByName(L, "jack");
    print(stu2);

    printf("根据学号删除学生：\n");
    deleteByNumber(L, 102);
    output(L);

    printf("根据姓名删除学生：\n");
    deleteByName(L, "tom");
    output(L);
}

/**
 * 输入指定个数学生的全部信息
 * @return 包含输入学生信息的结构体
 */
StudentList input(int count) {
    // 创建链表的头节点
    StudentList L = (StudentList) malloc(sizeof(StudentNode));
    L->next = NULL;
    StudentList temp = L;

    for (int i = 0; i < count; i++) {
        // 从键盘输入数据
        Student student = create();
        // 创建新节点
        StudentList newNode = (StudentList) malloc(sizeof(StudentNode));
        newNode->data = student;
        newNode->next = NULL;
        // 将创建好的新节点插入到链表的尾部
        temp->next = newNode;
        temp = newNode;
    }

    return L;
}

/**
 * 将指定学生插入到学生链表中，按照学号先后顺序插入
 * @param L 包含所有学生的链表
 */
void insert(StudentList L) {
    if (L == NULL) {
        printf("请先创建链表！");
    }
    // 从键盘输入数据
    Student student = create();
    // 创建新节点
    StudentList newNode = (StudentList) malloc(sizeof(StudentNode));
    newNode->data = student;
    newNode->next = NULL;

    // 将输入的学生插入到链表中
    // 链表的第一个节点
    StudentList node = L->next;
    // 先查找可插入节点该在链表中的位置
    StudentList pre = L;// 保存前驱节点，第一个节点的前驱节点是头节点。要在链表中插入节点必须知道前驱节点
    while (node != NULL) {
        // 判断插入位置
        if ((newNode->data).number < (node->data).number) {
            // 将新节点插入到链表中
            pre->next = newNode;
            newNode->next = node;
            // 插入之后一定要跳出循环
            break;
        }
        // 保存前驱节点
        pre = node;
        // 继续遍历链表的下一个节点
        node = node->next;
    }
    // 如果待插入学生的学号比链表中所有学生都大，则插入到表尾
    if (pre->next == NULL) {
        pre->next = newNode;
    }
}

/**
 * 按总成绩对所有学生进行排序
 * @param L 待排序的链表
 * @return 排序后的链表
 */
StudentList sortByTotalScore(StudentList L) {
    // 链表的第一个节点
    StudentList node = L->next;
    // 用一个数组来存放所有的元素
    int len = length(L);
    Student students[len];
    // 将链表中的所有节点的数据域保存到数组中
    int i = 0;
    while (node != NULL) {
        students[i] = node->data;
        i++;
        node = node->next;
    }
    // 对数组进行排序
    for (int m = 0; m < len; m++) {
        for (int n = 0; n + 1 < len - m; n++) {
            if (students[n].sum > students[n + 1].sum) {
                Student temp = students[m];
                students[m] = students[m + 1];
                students[m + 1] = temp;
            }
        }
    }
    // 根据排序后的数组重新生成链表
    StudentList newL = (StudentList) malloc(sizeof(StudentNode));
    StudentList temp = newL;
    newL->next = NULL;
    for (int j = 0; j < len; j++) {
        // 创建新节点
        StudentList newNode = (StudentList) malloc(sizeof(StudentNode));
        newNode->data = students[j];
        newNode->next = NULL;
        // 将节点插入到链表中
        temp->next = newNode;
        temp = newNode;
    }
    return newL;
}

/**
* 按学号对所有学生进行排序
* @param L 待排序的链表
* @return 排序后的链表
*/
StudentList sortByNumber(StudentList L) {
    // 链表的第一个节点
    StudentList node = L->next;
    // 用一个数组来存放所有的元素
    int len = length(L);
    Student students[len];
    // 将链表中的所有节点的数据域保存到数组中
    int i = 0;
    while (node != NULL) {
        students[i] = node->data;
        i++;
        node = node->next;
    }
    // 对数组进行排序
    for (int m = 0; m < len; m++) {
        for (int n = 0; n + 1 < len - m; n++) {
            if (students[n].number > students[n + 1].number) {
                Student temp = students[m];
                students[m] = students[m + 1];
                students[m + 1] = temp;
            }
        }
    }
    // 根据排序后的数组重新生成链表
    StudentList newL = (StudentList) malloc(sizeof(StudentNode));
    StudentList temp = newL;
    newL->next = NULL;
    for (int j = 0; j < len; j++) {
        // 创建新节点
        StudentList newNode = (StudentList) malloc(sizeof(StudentNode));
        newNode->data = students[j];
        newNode->next = NULL;
        // 将节点插入到链表中
        temp->next = newNode;
        temp = newNode;
    }
    return newL;
}

/**
 * 通过学号查找学生
 * @param L 包含所有学生信息的链表
 * @param number 学号
 * @return 根据学号查找成功的学生
 */
Student findByNumber(StudentList L, int number) {
    Student student;
    // 链表的第一个节点
    StudentList node = L->next;
    // 循环链表中的所有节点
    while (node != NULL) {
        // 判断正在遍历的节点的学号是否等于学号参数
        if ((node->data).number == number) {
            student = node->data;
        }
        node = node->next;
    }
    return student;
}

/**
 * 通过姓名查找学生
 * @param L 包含所有学生信息的单链表
 * @param name 待查找的学生姓名
 * @return 根据姓名查找成功的学生
 */
Student findByName(StudentList L, char name[]) {
    // 链表的第一个节点
    StudentList node = L->next;
    // 保存查找到的学生信息
    Student student;
    // 循环遍历链表
    while (node != NULL) {
        // 比较链表中节点的姓名是否与姓名参数相等，通过strcmp()函数进行比较
        if (strcmp((node->data).name, name) == 0) {
            student = node->data;
        }
        node = node->next;
    }
    return student;
}

/**
 * 根据学号删除学生
 * @param L 包含所有学生信息的链表
 * @param number 待删除学生的学号
 */
void deleteByNumber(StudentList L, int number) {
    // 链表的第一个节点
    StudentList node = L->next;
    // 保存前驱节点，链表的第一个节点的前驱节点是头节点。删除链表节点必须知道链表的前驱节点
    StudentList pre = L;
    // 循环链表中的每个节点
    while (node != NULL) {
        // 寻找到待删除的节点
        if ((node->data).number == number) {
            // 删除链表上的节点
            pre->next = node->next;
            break;
        }
        // 保存前驱节点
        pre = node;
        // 继续遍历链表的下一个节点
        node = node->next;
    }
}

/**
 * 根据姓名删除学生
 * @param studentList 学生顺序表
 * @param name 待删除学生的姓名
 */
void deleteByName(StudentList L, char name[]) {
    // 链表的第一个节点
    StudentList node = L->next;
    // 保存前驱节点，链表的第一个节点的前驱节点是头节点。删除链表节点必须知道链表的前驱节点
    StudentList pre = L;
    // 循环链表中的每个节点
    while (node != NULL) {
        // 寻找到待删除的节点
        if (strcmp((node->data).name, name) == 0) {
            // 删除链表上的节点
            pre->next = node->next;
            break;
        }
        // 保存前驱节点
        pre = node;
        // 继续遍历链表的下一个节点
        node = node->next;
    }
}

/**
 * 输出全部的学生记录
 * @param students 学生数组
 * @param n 数组长度
 */
void output(StudentList L) {
    // 链表的第一个节点
    StudentList node = L->next;
    printf("学号\t姓名\t性别\t年龄\t语文\t数学\t英语\t音乐\t总成绩\t平均成绩\n");
    while (node != NULL) {
        // 获取当前节点的数据域
        Student student = node->data;
        // 打印数据中的属性
        print(student);
        // 继续输出下一个节点
        node = node->next;
    }
}

/**
 * 从键盘输入单个学生信息
 * @return 单个学生
 */
Student create() {
    Student student;
    printf("\n请输入学号：");
    scanf("%d", &student.number);
    printf("请输入姓名：");
    scanf("%s", student.name);
    printf("请输入性别：");
    scanf("%s", student.gender);
    printf("请输入年龄：");
    scanf("%d", &student.age);
    printf("请输入语文成绩：");
    scanf("%f", &student.course.chinese);
    printf("请输入数学成绩：");
    scanf("%f", &student.course.math);
    printf("请输入英语成绩：");
    scanf("%f", &student.course.english);
    printf("请输入音乐成绩：");
    scanf("%f", &student.course.music);
    float sum = student.course.chinese + student.course.math + student.course.english + student.course.music;
    student.sum = sum;// 计算总成绩并且保存到结构体中
    float avg = sum / 4;
    student.avg = avg;// 计算平均成绩并且保存到结构体中
    return student;
}

/**
 * 打印单个学生记录
 * @param student 单个学生
 */
void print(Student student) {
    printf("%d\t", student.number);
    printf("%s\t", student.name);
    printf("%s\t", student.gender);
    printf("%d\t", student.age);
    printf("%.1f\t", student.course.chinese);
    printf("%.1f\t", student.course.math);
    printf("%.1f\t", student.course.english);
    printf("%.1f\t", student.course.music);
    printf("%.1f\t", student.sum);
    printf("%.1f\t\n", student.avg);
}

/**
 * 计算链表中的节点个数
 * @param L 学生链表
 * @return 节点个数
 */
int length(StudentList L) {
    // 链表的第一个节点
    StudentList node = L->next;
    int len = 0;
    while (node != NULL) {
        len++;
        node = node->next;
    }
    return len;
}
```

代码执行结果如下：

```text
请输入学号：101
请输入姓名：tom
请输入性别：f
请输入年龄：19
请输入语文成绩：56
请输入数学成绩：67
请输入英语成绩：78
请输入音乐成绩：90

请输入学号：103
请输入姓名：jack
请输入性别：m
请输入年龄：20
请输入语文成绩：66
请输入数学成绩：77
请输入英语成绩：88
请输入音乐成绩：99

学号     姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5

请输入学号：102
请输入姓名：rose
请输入性别：f
请输入年龄：17
请输入语文成绩：67
请输入数学成绩：98
请输入英语成绩：66
请输入音乐成绩：34

学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
102     rose    f       17      67.0    98.0    66.0    34.0    265.0   66.3
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
根据总成绩排序：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
102     rose    f       17      67.0    98.0    66.0    34.0    265.0   66.3
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
根据学号排序：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
102     rose    f       17      67.0    98.0    66.0    34.0    265.0   66.3
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
根据学号查询学生：
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
根据姓名查询学生：
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
根据学号删除学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
101     tom     f       19      56.0    67.0    78.0    90.0    291.0   72.8
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
根据姓名删除学生：
学号    姓名    性别    年龄    语文    数学    英语    音乐    总成绩  平均成绩
103     jack    m       20      66.0    77.0    88.0    99.0    330.0   82.5
```