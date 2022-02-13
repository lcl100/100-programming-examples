# 练习实例87

## 题目

结构体变量传递。


## 分析

本题考查的知识点：
- 结构体
- `typedef`关键字
- 函数
- `strcpy`函数

分析：
- 本题主要考查的是结构体，当结构体作为函数形参时在函数内修改不会改变函数外的实参；当结构体指针作为函数形参时在函数内修改会改变函数外的实参。
- 注意，当结构体指针作为函数形参时，内部要访问修改结构体的属性需要通过`->`。
- 注意，如果结构体的属性是字符串，不能直接使用`person.name="tom";`，而需要通过`strcpy(person.name, "tom");`方式赋值。


## 代码

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[4];
    int age;
} Person;

void fun1(Person person);

void fun2(Person *person);

int main() {
    Person person;
    strcpy(person.name, "tom");
    person.age = 17;
    printf("%s %d\n", person.name, person.age);

    fun1(person);
    printf("%s %d\n", person.name, person.age);

    fun2(&person);
    printf("%s %d\n", person.name, person.age);
}

/**
 * 值传递，在函数内修改形参结构体变量的值不会影响到函数外的实参
 * @param person
 */
void fun1(Person person) {
    strcpy(person.name, "jack");
    person.age = 18;
}

/**
 * 址传递，在函数内修改形参结构体变量的值会影响到函数外的实参
 * @param person
 */
void fun2(Person *person) {
    strcpy(person->name, "rose");
    person->age = 19;
}
```

代码执行结果如下：

```text
tom 17
tom 17
rose 19
```