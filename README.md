# 100-programming-examples

经典100编程实例

## 题目1

有1、2、3、4个数字，能组成多少个互不相同且无重复数字的三位数？都是多少？

## 题目2

企业发放的奖金根据利润提成。利润(I)
低于或等于10万元时，奖金可提10%；利润高于10万元，低于20万元时，低于10万元的部分按10%提成，高于10万元的部分，可提成7.5%；20万到40万之间时，高于20万元的部分，可提成5%；40万到60万之间时高于40万元的部分，可提成3%；60万到100万之间时，高于60万元的部分，可提成1.5%，高于100万元时，超过100万元的部分按1%提成，从键盘输入当月利润I，求应发放奖金总数？

## 题目3

一个整数，它加上100后是一个完全平方数，再加上168又是一个完全平方数，请问该数是多少？

## 题目4

输入某年某月某日，判断这一天是这一年的第几天？

## 题目5

输入三个整数x,y,z，请把这三个数由小到大输出。

## 题目6

用`*`号输出字母C的图案。

## 题目7

输出特殊图案。

## 题目8

输出9*9口诀。

## 题目9

要求输出国际象棋棋盘。

## 题目10

打印楼梯。

## 题目12

判断 101 到 200 之间的素数。

## 题目13

打印出所有的"水仙花数"，所谓"水仙花数"是指一个三位数，其各位数字立方和等于该数本身。

## 题目15

利用条件运算符的嵌套来完成此题：学习成绩>=90分的同学用A表示，60-89分之间的用B表示，60分以下的用C表示。

## 题目17

输入一行字符，分别统计出其中英文字母、空格、数字和其它字符的个数。

## 题目18

求s=a+aa+aaa+aaaa+aa...a的值，其中a是一个数字。例如2+22+222+2222+22222(此时共有5个数相加)，几个数相加有键盘控制。

## 题目25

求1+2!+3!+...+20!的和。

## 题目26

利用递归方法求5!。

## 题目30

一个5位数，判断它是不是回文数。即12321是回文数，个位与万位相同，十位与千位相同。

## 题目31

请输入星期几的第一个字母来判断一下是星期几，如果第一个字母一样，则继续判断第二个字母。

## 题目34

练习函数调用。

## 题目35

字符串反转，如将字符串 "hello" 反转为 "olleh"。

## 题目70

写一个函数，求一个字符串的长度，在 main 函数中输入字符串，并输出其长度。

## 题目90

利用指针倒序输出数组。

## 题目91

时间函数举例1。

## 题目92

时间函数举例2。

## 题目93

时间函数举例3。

## 题目94

猜谜游戏。

## 题目95

简单的结构体应用实例。

## 题目96

计算字符串中子串出现的次数。

## 题目97

从键盘输入一些字符，逐个把它们送到磁盘上去，直到输入一个#为止。

## 题目98

从键盘输入一个字符串，将小写字母全部转换成大写字母，然后输出到一个磁盘文件"test"中保存。 输入的字符串以!结束。

## 题目100

有五个学生，每个学生有3门课的成绩，从键盘输入以上数据（包括学生号，姓名，三门课成绩），计算出平均成绩，况原有的数据和计算出的平均分数存放在磁盘文件"stud"中。

## 题目101

1、定义一个数组a[11]，用以存放学生的成绩。

2、从键盘输入10个学生成绩。

3、采用冒泡法，将学生成绩按从高到低进行排序。

4、再输入一个学生的成绩，将此成绩按照排序规律插入原学生成绩数组。

5、将排好序的成绩单进行反序存放，即原来是从高到低，现在改为从低到高排列。

## 题目102

1、在函数中进行10个学生成绩从高到低排名`sort(int a[10])`。

2、改进第一步的函数为`sort(int a[], int n)`，进行n个学生成绩从高到低排名。

3、改进第二步的函数为`sort(int a[], int n, char style)`，将n个学生成绩从高到低排名。

4、根据`sort()`函数的style参数进行，如style为'a'按升序排，style为'd'按降序排。

> 说明：a表示ascending升序；d表示descending降序。

## 题目103

1、定义一个数组stu[10]存放10个学生的成绩，从键盘输入数据，要求用指针实现。

2、将数组stu[10]的内容输出到屏幕上，要求用指针实现。

3、将成绩数组按照从高到低进行排序，要求用指针实现。

4、将第三步内容放在函数中实现，在主函数中调用实现排序，用指针实现，输出排序后的成绩单。

5、采用指针方法，输入字符串"student score"，复制该字符串并输出（复制字符串采用库函数或者用户自定义函数）。

## 题目104

1、定义一个结构体数组，存放10个学生的学号，姓名，三门课的成绩。

2、从键盘输入10个学生的以上内容。

3、输出单门成绩最高的学生的学号、姓名、以及该门课程的成绩。

4、输出三门课程的平均分数最高的学生的学号、姓名及其平均分。

5、将10个学生按照平均分数从高到低进行排序，输出结果，格式如下：

```text
number  name  math  chinese  english  average
103     tom   90    90       90       90
101     jack  65    75       70       70 
```

## 题目105

1、定义一个结构体数组，存放10个学生的学号，姓名，三门课的成绩。

2、从键盘输入10个学生的以上内容，存入文件stud.dat，关闭文件。

3、打开 stud.dat 文件，将数据读出，查看是否正确写入，关闭文件。

4、打开文件 stud.dat 文件，读出数据，将10个学生按照平均分数从高到低进行排序，分别将结果输出到屏幕上和另一文件 studsort.dat 中。

5、从 studsort.dat 文件中读取第2、4、6、8、10个学生的数据。

## 题目106

学生成绩管理系统。需要完成下列功能：

1、输入：函数`input`把20个学生的学号、姓名、性别、年龄、四科成绩以及平均成绩和总成绩放在一个结构体数组中，学生的学号、姓名、四科成绩成绩由键盘输入，然后计算出平均成绩和总成绩放在结构体对应的域中。

2、插入：`insert`函数输入一个学生的记录，按学号的先后顺序插入该学生的全部内容。

3、排序：`sort`函数对所有学生按要求排序（学号、总成绩），并输出。

4、查找：`find`函数输入一个学生的学号或姓名，找到该学生并输出该学生的全部内容。要求能查询多次。

5、删除：`delete`函数输入一个学生的学号或姓名，找到该学生并删除该学生的全部内容。

6、输出：函数`output`输出全部学生的记录。

7、`main`：调用所有函数，并且实现全部函数功能。（注：除了定义结构之外，不允许使用全局变量，函数之间的数据全部使用参数传递。）

## 题目108

编写函数实现将输入的字母转换成大写字母（若输入小写则转换，大写字母直接输出，其他字母请输出提示『请输入字母』）。

## 题目109

从键盘输入若干个计算机课程期末考试成绩（学生人数可由用户输入），求该课程的期末成绩的平均分并输出。

## 题目110

计算 3 到 100 之间所有素数的平方根之和。

## 题目111

求一个任意边长的矩形面积。矩形的长和宽通过键盘输入。

## 题目112

求一个任意半径的圆的面积和周长。半径通过键盘输入。

## 题目113

比较两个数的大小。如果 x 大于 y，则输出：x>y，否则输出：x<y。

## 题目114

求自然数 1~10 之和。

## 题目115

从键盘输入10个整数，求奇数之和以及偶数之和。

## 题目116

从键盘输入一个 0~6 的整数，转换成星期输出。

## 题目117

从键盘输入一个字符串，再输入两个正整数m和n，输出字符串中从 m 开始，连续 n 个字符。例如，输入`abcdefg, 2, 3`则输出`bcd`。

## 题目118

输入一个不多于5位的正整数，判断它是几位数，并逆序输出各位数字。

## 题目119

从键盘输入一个十进制整型数据，计算并输出其各位上数字之和（忽略正负号）。例如，输入1234则输出10；输入-1234则输出10。

## 题目120

判断输入的字符串是否是『回文』。所谓『回文』是指顺读和倒读都一样，如 abcba 是回文，而 abc 不是回文。

## 题目121

编写程序，将用户输入的字符串中删除所有的数字，然后输出剩余的字符。

## 题目122

编程计算`1*2*3+3*4*5+5*6*7+...+99*100*101`的值。

## 题目123

编写程序，将用户输入的字符串中所有的字符`a`用`*`代替，然后输出。

## 题目124

输入一个华氏温度，输出摄氏温度，计算公式为`c=5/9*(F-32)`。要求结果保留两位小数。

## 题目125

输入一个整数，将各位数字反转后输出。如：输入 365，则输出显示为 563。

## 题目126

把输入的一个字符串按逆序重新排序其字符并输出。

## 题目127

编写一个函数，求二维数组所有元素的和，要求二维数组的行、列以及数组通过函数参数传递，并通过主函数调用求2行3列的数组的所有元素之和。

## 题目128

编写一个函数，求一维数组的平均值和最大值。

## 题目129

编写一个函数，求 N 阶二维矩阵的主和辅对角线元素之和。

## 题目130

用指针的方法，把输入的一个字符串按逆序重新排序其字符，并输出。

## 题目131

用指针的方法，将键盘输入的两个字符串连接起来形成一个新的字符串。

## 题目132

用指针的方法，将键盘输入的一串数值字符串转换为数值输出。如输入：'-123'，则输出为：-123。

## 题目133

在主函数中初始化一个3行4列的矩阵并将每个元素都输出，然后调用子函数，分别计算每一行的元素之和，将和直接存放在每行的第一个元素中，返回主函数之后输出各行元素的和。

## 题目134

计算字符串中子串出现的次数。要求：用一个子函数`subString()`实现，参数为指向字符串和要查找的子串的指针，返回次数。

## 题目135

字符替换。要求用函数`replace`将用户输入的字符串中的字符`t`（`T`）都替换成`e`（`E`），并返回替换字符的个数。

## 题目136

编写一个程序，输入星期，输出该星期的英文名。用指针数组处理。

## 题目137

有 5 个字符串，首先将它们按照字符串中的字符个数由小到大排列，再分别取出每个字符串的第三个字母合并成一个新的字符串输出（若少于三个字符的输出空格）。要求：利用字符串指针和指针数组实现。

## 题目138

定义一个动态数组，长度为变量n，用随机数给数组各元素赋值，然后对数组各单元排序，定义`swap`函数交换数据单元，要求参数使用指针传递。

## 题目139

实现模拟彩票的程序设计，随机产生6个数字，与用户输入的数字进行比较，输出它们相同的数字个数。使用动态内存分配。

## 题目140

编写函数实现，用指针方式计算字符串的串长。

## 题目141

编写函数实现，计算一个字符在一个字符串中出现的次数。

## 题目142

编程序，用指针数组在主函数中输入十个等长的字符串。用另一个函数对它们排序，然后在主函数中输出10个已经排好序的字符串。

## 题目143

自己实现一个比较字符串大小的函数，即实现 strcmp 函数。

## 题目144

输入一名学生的学号、姓名、年龄和身高等信息，用结构体保存，然后再把输入的信息输出到屏幕上。

## 题目145

定义一个结构体变量，包括年、月、日。计算该日在本年中是第几天，注意闰年问题。