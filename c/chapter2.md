###C语言基础语法
#### chapter 3 数据和C
#####数据类型和关键字
1. short `%h`
2. int `%d 十进制 %o 八进制 %x 十六进制`
3. long
4. char
5. bool
6. float`%f %e `
7. double `%f %e `

<img src="http://osz5qtl3g.bkt.clouddn.com/note_c_chapter_2_structure.png">


#### chapter 4 字符串和格式化输入/输出
#####字符串简介
1. 字符串（character string）是一个或多个字符的序列。`"小蛋黄"`，字符`'a'`
2. C语言没有专门用于储存字符串的变量类型，字符串都被储存在char类型的数组中.数组末尾位置的字符`\0`
##### strlen()函数
- 给出字符串的长度
- 注意与sizeOf() 的区别

#####常量,C预处理器 以及const限定符
- `#define PI 3.14`
- `const定义只读`
##### printf()和 scanf()
- 转换说明和各自对应的输出类
<img src="http://osz5qtl3g.bkt.clouddn.com/note_c_chapter_2_printf.png">


####chapter 5 运算符，表达式和语句
#####基本运算符
1. `= + - * /`

#####其他运算符
1. `sizeof()`
2. `% ++ --`
#####其他赋值运算符
1. `+= -= *= /= %=`
####逗号运算符
1. 逗号运算符把两个表达式连接成一个表达式，并保证最左边的表达式最先求值
#####表达式
1. 表达式由运算符和运算对象组成

#####语句
1. 语句是C程序的基本构建块。一条语句相当于一条完整的计算机指令
#####复合语句
1. 复合语句是用花括号括起来的一条或多条语句，复合语句也称为块

####chapter 6 循环
##### while
1. while语句创建了一个循环，重复执行直到测试表达式为假或0

##### for循环 
#####do while
1. do while语句是一种出口条件循环，即在执行完循环体后才根据测试条件决定是否再次执行循环。

####chapter 7 分支和跳转
##### if
#####if else
##### ?:
##### continue,break 
##### switch,break
##### goto


   
