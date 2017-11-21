#CPrimerPlus6E学习笔记
[TOC]


##第1章　初识C语言 1 
###1.1　C语言的起源 1 
###1.2 选择C语言的理由 1 
####1.2.1 设计特性 1 
####1.2.2 高效性 1 
####1.2.3 可移植性 2 
####1.2.4 强大而灵活 3 
####1.2.5 面向程序员 3 
####1.2.6 缺点 3 
###1.3 C语言的应用范围 3 
###1.4 计算机能做什么 4 
###1.5 高级计算机语言和编译器 5 
###1.6 语言标准 6 
####1.6.1 第1个ANSI/ISO C标准 6 
####1.6.2 C99标准 6 
####1.6.3 C11标准 7 
###1.7 使用C语言的7个步骤 7 
####1.7.1 第1步：定义程序的目标 8 
####1.7.2 第2步：设计程序 8 
####1.7.3 第3步：编写代码 8 
####1.7.4 第4步：编译 8 
####1.7.5 第5步：运行程序 9 
####1.7.6 第6步：测试和调试程序 9 
####1.7.7 第7步：维护和修改代码 9 
####1.7.8 说明 9 
###1.8 编程机制 10 
####1.8.1 目标代码文件、可执行文件和库 10 
####1.8.2 UNIX系统 11 
####1.8.3 GNU编译器集合和LLVM项目 13 
####1.8.4 Linux系统 13 
####1.8.5 PC的命令行编译器 14 
####1.8.6 集成开发环境（Windows） 14 
####1.8.7 Windows/Linux 15 
####1.8.8 Macintosh中的C 15 
###1.9 本书的组织结构 15 
###1.10 本书的约定 16 
####1.10.1 字体 16 
####1.10.2 程序输出 16 
####1.10.3 特殊元素 17 
###1.11 本章小结 17 
###1.12 复习题 18 
###1.13 编程练习 18 
##第2章　C语言概述 19 
###2.1 简单的C程序示例 19 
###2.2 示例解释 20 
####2.2.1 第1遍：快速概要 21 
####2.2.2 第2遍：程序细节 21 
###2.3 简单程序的结构 28 
###2.4 提高程序可读性的技巧 28 
###2.5 进一步使用C 29 
####2.5.1 程序说明 30 
####2.5.2 多条声明 30 
####2.5.3 乘法 30 
####2.5.4 打印多个值 30 
###2.6 多个函数 30 
###2.7 调试程序 32 
####2.7.1 语法错误 32 
####2.7.2 语义错误 33 
####2.7.3 程序状态 34 
###2.8 关键字和保留标识符 34 
###2.9 关键概念 35 
###2.10 本章小结 35 
###2.11 复习题 36 
###2.12 编程练习 37 
##第3章　数据和C 39 
###3.1 示例程序 39 
###3.2 变量与常量数据 42 
###3.3 数据：数据类型关键字 42 
####3.3.1 整数和浮点数 43 
####3.3.2 整数 43 
####3.3.3 浮点数 43 
###3.4 C语言基本数据类型 44 
####3.4.1 int类型 44 
####3.4.2 其他整数类型 47 
####3.4.3 使用字符：char类型 50 
####3.4.4 _Bool类型 54 
####3.4.5 可移植类型：stdint.h和inttypes.h 55 
####3.4.6 float、double和long double 56 
####3.4.7 复数和虚数类型 60 
####3.4.8 其他类型 60 
####3.4.9 类型大小 62 

sizeof是C语言的内置运算符，以字节为单位给出指定类型的大小。C99和C11提供％zd转换说明匹配sizeof的返回类型。一些不支持C99和C11的编译器可用％u或％lu代替％zd。

```C
//* typesize.c -- prints out type sizes */
#include <stdio.h>
int main(void)
{
    /* c99 provides a %zd specifier for sizes */
    printf("Type int has a size of %zd bytes.\n", sizeof(int));
    printf("Type char has a size of %zd bytes.\n", sizeof(char));
    printf("Type long has a size of %zd bytes.\n", sizeof(long));
    printf("Type long long has a size of %zd bytes.\n",
           sizeof(long long));
    printf("Type double has a size of %zd bytes.\n",
           sizeof(double));
    printf("Type long double has a size of %zd bytes.\n",
           sizeof(long double));
    return 0;
}
输出：
Type int has a size of 4 bytes.
Type char has a size of 1 bytes.
Type long has a size of 8 bytes.
Type long long has a size of 8 bytes.
Type double has a size of 8 bytes.
Type long double has a size of 16 bytes.
```



###3.5 使用数据类型 63 
###3.6 参数和陷阱 63 
###3.7 转义序列示例 64 
####3.7.1 程序运行情况 65 
####3.7.2 刷新输出 65 
###3.8 关键概念 66 
###3.9 本章小结 66 
###3.10 复习题 67 
###3.11 编程练习 68 
##第4章　字符串和格式化输入/输出 71 
###4.1 前导程序 71 
###4.2 字符串简介 72 
####4.2.1 char类型数组和null字符 72 
####4.2.2 使用字符串 73 
####4.2.3 strlen()函数 74 

strlen()函数给出字符串中的字符长度。C99和C11提供％zd转换说明匹配strlen()的返回类型。一些不支持C99和C11的编译器可用％u或％lu代替％zd。

```C
/* praise2.c */
// try the %u or %lu specifiers if your implementation
// does not recognize the %zd specifier
#include <stdio.h>
#include <string.h>      /* provides strlen() prototype */
#define PRAISE "You are an extraordinary being."
int main(void)
{
    char name[40];
    
    printf("What's your name? ");
    scanf("%s", name);
    printf("Hello, %s. %s\n", name, PRAISE);
    printf("Your name of %zd letters occupies %zd memory cells.\n",
           strlen(name), sizeof name);
    printf("The phrase of praise has %zd letters ",
           strlen(PRAISE));
    printf("and occupies %zd memory cells.\n", sizeof PRAISE);
    
    return 0;
}
输出：
What's your name? su
Hello, su. You are an extraordinary being.
Your name of 2 letters occupies 40 memory cells.
The phrase of praise has 31 letters and occupies 32 memory cells.
```



###4.3 常量和C预处理器 76 
####4.3.1 const限定符 78 
####4.3.2 明示常量 78 
###4.4 printf()和scanf() 80 
####4.4.1 printf()函数 80 
####4.4.2 使用printf() 81 
####4.4.3 printf()的转换说明修饰符 83 
####4.4.4 转换说明的意义 87 
####4.4.5 使用scanf() 92 
####4.4.6 printf()和scanf()的*修饰符 95 
####4.4.7 printf()的用法提示 97 
###4.5 关键概念 98 
###4.6 本章小结 98 
###4.7 复习题 99 
###4.8 编程练习 100 
##第5章　运算符、表达式和语句 103 
###5.1 循环简介 103 
###5.2 基本运算符 105 
####5.2.1 赋值运算符：= 105 
####5.2.2 加法运算符：+ 107 
####5.2.3 减法运算符：- 107 
####5.2.4 符号运算符：-和+ 107 
####5.2.5 乘法运算符：* 108 
####5.2.6 除法运算符：/ 110 
####5.2.7 运算符优先级 110 
####5.2.8 优先级和求值顺序 112 
###5.3 其他运算符 113 
####5.3.1 sizeof运算符和size_t类型 113 
####5.3.2 求模运算符：% 114 
####5.3.3 递增运算符：++ 115 
####5.3.4 递减运算符：-- 118 
####5.3.5 优先级 118 
####5.3.6 不要自作聪明 119 
###5.4 表达式和语句 120 
####5.4.1 表达式 120 
####5.4.2 语句 120 
####5.4.3 复合语句（块） 123 
###5.5 类型转换 124 
###5.6 带参数的函数 127 
###5.7 示例程序 129 
###5.8 关键概念 130 
###5.9 本章小结 130 
###5.10 复习题 131 
###5.11 编程练习 134 
##第6章　C控制语句：循环 137 
###6.1 再探while循环 137 
####6.1.1 程序注释 138 
####6.1.2 C风格读取循环 139 
###6.2 while语句 140 
####6.2.1 终止while循环 140 
####6.2.2 何时终止循环 141 
####6.2.3 while：入口条件循环 141 
####6.2.4 语法要点 141 
###6.3 用关系运算符和表达式比较大小 143 
####6.3.1 什么是真 144 
####6.3.2 其他真值 145 
####6.3.3 真值的问题 146 
####6.3.4 新的_Bool类型 147 
####6.3.5 优先级和关系运算符 148 
###6.4 不确定循环和计数循环 150 
###6.5 for循环 151 
###6.6 其他赋值运算符：+=、-=、*=、/=、%= 155 
###6.7 逗号运算符 156 
###6.8 出口条件循环：do while 159 
###6.9 如何选择循环 161 
###6.10 嵌套循环 162 
####6.10.1 程序分析 163 
####6.10.2 嵌套变式 163 
###6.11 数组简介 164 
###6.12 使用函数返回值的循环示例 166 
####6.12.1 程序分析 168 
####6.12.2 使用带返回值的函数 169 
###6.13 关键概念 169 
###6.14 本章小结 170 
###6.15 复习题 170 
###6.16 编程练习 174 
##第7章　C控制语句：分支和跳转 177 
###7.1 if语句 177 
###7.2 if else语句 179 
####7.2.1 另一个示例：介绍getchar()和putchar() 180 
####7.2.2 ctype.h系列的字符函数 182 
####7.2.3 多重选择else if 184 
####7.2.4 else与if配对 186 
####7.2.5 多层嵌套的if语句 187 
###7.3 逻辑运算符 190 
####7.3.1 备选拼写：iso646.h头文件 191 
####7.3.2 优先级 192 
####7.3.3 求值顺序 192 
####7.3.4 范围 193 
###7.4 一个统计单词的程序 194 
###7.5 条件运算符：?： 196 
###7.6 循环辅助：continue和break 198 
####7.6.1 continue语句 198 
####7.6.2 break语句 200 
###7.7 多重选择：switch和break 202 
####7.7.1 switch语句 204 
####7.7.2 只读每行的首字符 205 
####7.7.3 多重标签 206 
####7.7.4 switch和if else 208 
###7.8 goto语句 208 
###7.9 关键概念 211 
###7.10 本章小结 211 
###7.11 复习题 212 
###7.12 编程练习 214 
##第8章　字符输入/输出和输入验证 217 
###8.1 单字符I/O：getchar()和putchar() 217 
###8.2 缓冲区 218 
###8.3 结束键盘输入 219 
####8.3.1 文件、流和键盘输入 219 
####8.3.2 文件结尾 220 
###8.4 重定向和文件 222 
###8.5 创建更友好的用户界面 226 
####8.5.1 使用缓冲输入 226 
####8.5.2 混合数值和字符输入 228 
###8.6 输入验证 230 
####8.6.1 分析程序 234 
####8.6.2 输入流和数字 234 
###8.7 菜单浏览 235 
####8.7.1 任务 235 
####8.7.2 使执行更顺利 235 
####8.7.3 混合字符和数值输入 237 
###8.8 关键概念 240 
###8.9 本章小结 240 
###8.10 复习题 241 
###8.11 编程练习 241 
##第9章　函数 243 
###9.1 复习函数 243 
####9.1.1 创建并使用简单函数 244 
####9.1.2 分析程序 245 
####9.1.3 函数参数 247 
####9.1.4 定义带形式参数的函数 248 
####9.1.5 声明带形式参数函数的原型 249 
####9.1.6 调用带实际参数的函数 249 
####9.1.7 黑盒视角 250 
####9.1.8 使用return从函数中返回值 250 
####9.1.9 函数类型 252 
###9.2 ANSI C函数原型 253 
####9.2.1 问题所在 253 
####9.2.2 ANSI的解决方案 254 
####9.2.3 无参数和未指定参数 255 
####9.2.4 函数原型的优点 256 
###9.3 递归 256 
####9.3.1 演示递归 256 
####9.3.2 递归的基本原理 258 
####9.3.3 尾递归 258 
####9.3.4 递归和倒序计算 260 
####9.3.5 递归的优缺点 262 
###9.4 编译多源代码文件的程序 262 
####9.4.1 UNIX 263 
####9.4.2 Linux 263 
####9.4.3 DOS命令行编译器 263 
####9.4.4 Windows和苹果的IDE编译器 263 
####9.4.5 使用头文件 263 
###9.5 查找地址：&运算符 267 

​	一元   `&` 运算符给出变量的存储地址。如果 Pooh 是变量名，那么 &Pooh 是变量的地址。可以把地址看作是变量在内存中的位置。假设有下面的语句：
```c
pooh = 24;
```
假设 pooh 的存储地址是 0B76 （PC地址通常用十六进制形式表示）。那么，下面的语句:
```c
printf("%d %p\n", pooh, &pooh);
```
将输出如下内容（％p是输出地址的转换说明）:
```
24 0B76
```
###9.6 更改主调函数中的变量 268 
###9.7 指针简介 269 

​	指针是一个值为内存地址的变量。

​	假设一个指针变量名是 ptr ，可以编写如下语句：
```c
ptr = &pooh; // 把 pooh 的地址赋给 ptr
```
​	对于这条语句，我们说 ptr “指向” pooh。ptr 和 &pooh 的区别是 ptr 是变量，而 &pooh 是常量。或者，ptr 是可修改的左值，而 &pooh 是右值。还可以把 ptr 指向别处：
```c
ptr = &bah; // 把 ptr 指向 bah，而不是 pooh
```
​	现在 ptr 的值是 bah 的地址。

####9.7.1 间接运算符：* 270 

​	假设已知 ptr 指向 bah，如下所示：
```c
ptr = &bah;
```
​	然后使用间接运算符 * 找出储存在 bah 中的值，该运算符有时也称为解引用运算符。
```c
val = *ptr; // 找出 ptr 指向的值
```
​	语句 `ptr = &bah;` 和 `val = *ptr;` 放在一起相当于下面的语句：
```c
val = bah;
```
由此可见，使用地址和间接运算符可以间接完成上面这条语句的功能，这也是“间接运算符”名称的由来。

> ##### 小结：与指针相关的运算符
>
> ###### 	地址运算符：&
>
> ​	一般注解：
>
> ​	后跟一个变量名时，`&` 给出该变量的地址。
>
> ​	示例：
>
> ​	&nurse表示变量nurse的地址。
>
> ###### 	地址运算符：*
>
> ​	一般注解：
>
> ​	后跟一个指针名或地址时，`*` 给出储存在指针指向地址上的值。 
>
> ​	示例：
>
> ```c
> nurse = 22;
> ptr = &nurse; // 指向 nurse 的指针
> val = *ptr; // 把 ptr 指向的地址上的值域给val
> ```
> ​	执行以上 3 条语句的最终结果是把 22 赋给 val 。

####9.7.2 声明指针 270 

​	因为声明指针变量时必须指定指针所指向变量的类型，因为不同的变量类型占用不同的存储空间，一些指针操作要求知道操作对象的大小。另外，程序必须知道储存在指定地址上的数据类型。long 和 float 可能占用相同的存储空间，但是它们储存数字却大相径庭。下面是一些指针的声明示例:
```c
int * pi;			// pi是指向int类型变量的指针
char * pc;			// pc是指向char类型变量的指针
float * pf, * pg;	// pf、pg都是指向float类型变量的指针
```
​	类型说明符表明了指针所指向对象的类型，星号 `*` 表明声明的变量是一个指针。`int * pi;` 声明的意思是 `pi` 是一个指针，`*pi` 是 int 类型。

​	`*` 和指针名之间的空格可有可无。通常，程序员在声明时使用空格，在解引用变量时省略空格。

​	ANSI C 专门为指针提供了`％p` 格式的转换说明。

####9.7.3 使用指针在函数间通信 271 
###9.8 关键概念 274 
###9.9 本章小结 275 
###9.10　复习题 275 
###9.11 编程练习 276 
##第10章　数组和指针 277 
###10.1 数组 277 
####10.1.1 初始化数组 277 

```C
/* day_mon2.c -- letting the compiler count elements */
#include <stdio.h>
int main(void)
{
    const int days[] = {31,28,31,30,31,30,31,31,30,31};
    int index;
    
    for (index = 0; index < sizeof days / sizeof days[0]; index++)
        printf("Month %2d has %d days.\n", index +1,
               days[index]);

    return 0;
}
```

在day_mon2.c中，要注意以下两点。

- 如果初始化数组时省略方括号中的数字，编译器会根据初始化列表中的项数来确定数组的大小。
- 注意 for 循环中的测试条件。由于人工计算容易出错，所以让计算机来汁算数组的大小。sizeof 运算符给出它的运算对象的大小（以字节为单位）。所以 `sizeof days` 是整个数组的大小（以字节为单位），`sizeof day [0]` 是数组中一个元素的大小（以字节为单位）。整个数组的大小除以单个元素的大小就是数组元素的个数。

####10.1.2 指定初始化器（C99） 281 
####10.1.3 给数组元素赋值 282 
####10.1.4 数组边界 282 
####10.1.5 指定数组的大小 284 
###10.2 多维数组 284 
####10.2.1 初始化二维数组 287 
####10.2.2 其他多维数组 288 
###10.3 指针和数组 288 
###10.4 函数、数组和指针 290 

> ##### 注意声明数组形参
>
> ​	因为数组名是该数组首元素的地址，作为实际参数的数组名要求形式参数是一个与之匹配的指针, 只有在这种情况下，C 才会把 `int ar[]` 和 `int * ar` 解释成一样。也就是说，ar 是指向 int 的指 针。由于函数原型可以省略参数名，所以下面4种原型都是等价的：
>
> ```c
> int sum(int *ar, int n); 
> int sum(int *, int);
> int sum (int ar[], int n); 
> int sum(int [], int);
> ```
>
> ​	但是，在函数定义中不能省略参数名。下面两种形式的函数定义等价：
>
> ```c
> int sum(int *ar, int n)
> {
> 	//其他代码已省略
> }
>
> int sum(int ar[], int n);
> {
> 	//其他代码已省略
> }
> ```
>
> ​	可以使用以上提到的任意一种函数原型和函数定义。

####10.4.1 使用指针形参 293 
####10.4.2 指针表示法和数组表示法 294 
###10.5 指针操作 295 
###10.6 保护数组中的数据 298 
####10.6.1 对形式参数使用const 299 

```c
int sum(const int ar[],int n);/* 函数原型 */
int sum(const int ar[],int n)/* 函数定义 */
{
  int i;
  int total = 0;
  for(i = 0; i < n; i++)
    total += ar[i];
  return total;
}
```

这样使用 const 并不是要求原数组是常量，而是该函数在处理数组是将其视为常量，不可更改。

指向 const 的指针通常用于函数形参中，表明该函数不会使用指针改变数据。

####10.6.2　const的其他内容 300 

示例：

```C
#include <stdio.h>

int main(void) {
    /**
    常量指针与指针常量
    写法一共有六种，如下：
    ①const int p;
    ②const int* p;
    ③int const* p;
    ④int * const p;
    ⑤const int * const p;
    ⑥int const * const p;
    第一种是常量整数，没什么好说的。
    后面五种是指针，有一个简便的办法记忆。
    从右往左读，遇到p就替换成“p is a ”，遇到*就替换成“point to”。
    比如说②，读作：p is a point to int const.
    p是一个指向整型常量的指针。
    ③读作：p is a point to const int.
    意思跟②相同。
    ④读作：p is a const point to int.
    p是一个常量指针，指向整型。
    ⑤读作：p is a const point to int const.
    ⑥读作：p is a const point to const int.
    ⑤和⑥的意思相同，p都是常量指针，指向整型常量。
    这种方法来源于《c primer plus》，这里也向c初学者推荐此书。
    */

    /** 普通数组 */
    int datas[3] = {1, 2, 3};

    /** 常量数组 */
    const int cdatas[3] = {11, 12, 13};

    /** 普通指针 */
    int *p_int;

    /** c_int_p 是一个指向整型常量的指针 */
    const int *c_int_p = datas;

    /** 不能修改 const 关键字保护数组 */
    printf("\n不能修改 const 关键字保护数组\n");
    datas[0] = 4;//允许，因为 datas 未被 const 限定
    printf("%d\n", datas[0]);//4
//    cdatas[0] = 14;//不允许 'const int[3]' is read-only pointer
    datas[0] = 1;

    /** 指向 const 的指针不能用于改变值 */
    printf("\n指向 const 的指针不能用于改变值\n");
    printf("%d\n", *c_int_p);//1
//    *c_int_p = 4;//不允许 'const int *' is read-only pointer
//    c_int_p[2] = 4;//不允许 'const int *' is read-only pointer
    datas[0] = 4;//允许，因为 datas 未被 const 限定
    printf("%d\n", *c_int_p);//4
    datas[0] = 1;

    /** 让 c_int_p 指向别处没问题 */
    printf("\n让 c_int_p 指向别处没问题\n");
    c_int_p++;// 让 c_int_p 指向 datas[1] 没问题
    printf("%d\n", *c_int_p);//2

    /**把 const 数据或非 const 数据的地址初始化为指向 const 的指针或为其赋值是合法的*/
    printf("\n把 const 数据或非 const 数据的地址初始化为指向 const 的指针或为其赋值是合法的\n");
    c_int_p = datas;// 让 c_int_p 指向 datas 没问题
    printf("%d\n", *c_int_p);//1

    c_int_p = cdatas;// 让 c_int_p 指向 cdatas 没问题
    printf("%d\n", *c_int_p);//11

    c_int_p = &datas[2];//有效
    printf("%d\n", *c_int_p);//3

    c_int_p = &cdatas[2];//有效
    printf("%d\n", *c_int_p);//13

    /** 只能把非 const 数据的地址赋给普通指针 */
    printf("\n只能把非 const 数据的地址赋给普通指针\n");
    p_int = datas;//有效
    *p_int = 4;
    printf("%d\n", *p_int);//4
    p_int = cdatas;//无效，编译器报警告
//    *p_int = 14;//无效，运行时报错
    printf("%d\n", *p_int);//11
    p_int = (int *) cdatas;//强转
//    *p_int = 14;//无效，运行时报错
    printf("%d\n", *p_int);//11
    p_int = &datas[1];//有效
    printf("%d\n", *p_int);//2

    /** 常量指针 */
    printf("\n常量指针\n");
    /** int_p_c 是一个常量指针，指向整型 */
    int *const int_p_c = &datas[1];
    printf("%d\n", datas[1]);//2
    printf("%d\n", *int_p_c);//2
//    int_p_c = &datas[2];//不允许，因为该指针不能指向别处

    *int_p_c = 4;//没问题，更改datas[1]的值
    printf("%d\n", *int_p_c);//4
    printf("%d\n", datas[1]);//4

    /** 常量指针，指向整型常量 */
    printf("\n常量指针，指向整型常量\n");
    /** c_int_p_c 是一个常量指针，指向整型常量 */
    const int *const c_int_p_c = &datas[2];
    printf("%d\n", *c_int_p_c);//3
    printf("%d\n", datas[2]);//3
//    c_int_p_c = &datas[3];//不允许
//    *c_int_p_c = 4;//不允许

    return 0;
}
```

###10.7 指针和多维数组 302 

示例：

```C
/* zippo1.c --  zippo info */
#include <stdio.h>

int main(void) {
    int zippo[4][2] = {{2, 4},
                       {6, 8},
                       {1, 3},
                       {5, 7}};

    printf("   zippo = %p,    zippo + 1 = %p\n",
           zippo, zippo + 1);
    printf("zippo[0] = %p, zippo[0] + 1 = %p\n",
           zippo[0], zippo[0] + 1);
    printf("  *zippo = %p,   *zippo + 1 = %p\n",
           *zippo, *zippo + 1);
    printf("zippo[0][0] = %d\n", zippo[0][0]);
    printf("  *zippo[0] = %d\n", *zippo[0]);
    printf("    **zippo = %d\n", **zippo);
    printf("      zippo[2][1] = %d\n", zippo[2][1]);
    printf("*(*(zippo+2) + 1) = %d\n", *(*(zippo + 2) + 1));

    return 0;
}

输出：
   zippo = 0x7fff5903b520,    zippo + 1 = 0x7fff5903b528
zippo[0] = 0x7fff5903b520, zippo[0] + 1 = 0x7fff5903b524
  *zippo = 0x7fff5903b520,   *zippo + 1 = 0x7fff5903b524
zippo[0][0] = 2
  *zippo[0] = 2
    **zippo = 2
      zippo[2][1] = 3
*(*(zippo+2) + 1) = 3
```
####10.7.1 指向多维数组的指针 304 

`int (* pz)[2];` pz 指向一个内含两个 int 类型值的数组

`int * pax[2];` pax 是一个内含两个指针元素的数组，每个元素都指向 int 的指针

可以用数组表示法或指针表示法来表示一个数组元素，即可以使用数组名，也可以使用指针名：`zippo[m][n] == *(*(zippo + m) + n)`

示例：
```C
/* zippo2.c --  zippo info via a pointer variable */
#include <stdio.h>
int main(void)
{
    int zippo[4][2] = { {2,4}, {6,8}, {1,3}, {5, 7} };
    int (*pz)[2];
    pz = zippo;
    
    printf("   pz = %p,    pz + 1 = %p\n",
           pz,         pz + 1);
    printf("pz[0] = %p, pz[0] + 1 = %p\n",
           pz[0],      pz[0] + 1);
    printf("  *pz = %p,   *pz + 1 = %p\n",
           *pz,        *pz + 1);
    printf("pz[0][0] = %d\n", pz[0][0]);
    printf("  *pz[0] = %d\n", *pz[0]);
    printf("    **pz = %d\n", **pz);
    printf("      pz[2][1] = %d\n", pz[2][1]);
    printf("*(*(pz+2) + 1) = %d\n", *(*(pz+2) + 1));
    
    return 0;
}

输出：
   pz = 0x7fff5bada520,    pz + 1 = 0x7fff5bada528
pz[0] = 0x7fff5bada520, pz[0] + 1 = 0x7fff5bada524
  *pz = 0x7fff5bada520,   *pz + 1 = 0x7fff5bada524
pz[0][0] = 2
  *pz[0] = 2
    **pz = 2
      pz[2][1] = 3
*(*(pz+2) + 1) = 3
```

####10.7.2 指针的兼容性 305 

指针之间的赋值比数组类型之间的赋值要严格。例如，不用类型转换就可以把 int 类型的值赋给 double 类型的变量，但是两个类型的指针不能这样做。

```C
int n = 5;
double x;
int * p1 = &n;
double * pd = &x;
x = n;				// 隐式类型转换
pd = p1;			// 编译时错误
```

更复杂的类型也是如此。假设有如下声明：

```C
int * pt;
int (*pa)[3];
int ar1[2][3];
int ar2[3][2];
int **p2;			// 一个指向指针的指针
// 有如下的语句：
pt = &ar1[0][0];	// 都是指向 int 的指针
pt = ar1[0];		// 都是指向 int 的指针
pt = ar1;			// 无效
pa = ar1;			// 都是指向内含 3 个 int 类型元素数组的指针
pa = ar2;			// 无效
p2 = &pt;			// 都是指向 int 指针的指针
*p2 = ar2[0];		// 都是指向 int 的指针
p2 = ar2;			// 无效
```

一般而言，多重解引用让人费解。例如，考虑下面的代码：

```c
int x = 20;
const int y = 23;
int * p1 = &x;
const int * p2 = &y;
const int ** pp2;
p1 = p2;			// 不安全 -- 把 const 指针赋给非 const 指针
p2 = p1;			// 有效 -- 把非 const 指针赋给 const 指针
pp2 = &p1;			// 不安全 -- 嵌套指针类型赋值
pp2 = &p2;			// 有效
```

####10.7.3 函数和多维数组 306 

```C
int junk[ROWS][COLS] = {{2,4,6,8},{3,5,7,9},{12,10,8,6}};
```

junk是一个指向数组（内含 4 个 int 类型值）的指针。

可以这样声明函数的形参：

```C
void somefunction(int (* pt)[4]);
```

另外，如果当且仅当 pt 是一个函数的形式参数时，可以这样声明：

```C
void somefunction(int pt[][4]);
```

第1个方括号是空的。空的方括号表明 pt 是一个指针。

示例：

```C
// array2d.c -- functions for 2d arrays
#include <stdio.h>
#define ROWS 3
#define COLS 4
void sum_rows(int ar[][COLS], int rows);
void sum_cols(int [][COLS], int );    // ok to omit names
int sum2d(int (*ar)[COLS], int rows); // another syntax
int sum2d2(int ar[ROWS][COLS]); // another syntax
int main(void)
{
    int junk[ROWS][COLS] = {
        {2,4,6,8},
        {3,5,7,9},
        {12,10,8,6}
    };

    sum_rows(junk, ROWS);
    sum_cols(junk, ROWS);
    printf("Sum of all elements = %d\n", sum2d(junk, ROWS));
    printf("Sum of all elements = %d\n", sum2d2(junk));

    return 0;
}

void sum_rows(int ar[][COLS], int rows)
{
    int r;
    int c;
    int tot;

    for (r = 0; r < rows; r++)
    {
        tot = 0;
        for (c = 0; c < COLS; c++)
            tot += ar[r][c];
        printf("row %d: sum = %d\n", r, tot);
    }
}

void sum_cols(int ar[][COLS], int rows)
{
    int r;
    int c;
    int tot;

    for (c = 0; c < COLS; c++)
    {
        tot = 0;
        for (r = 0; r < rows; r++)
            tot += ar[r][c];
        printf("col %d: sum = %d\n", c, tot);
    }
}

int sum2d(int (*ar)[COLS], int rows)
{
    int r;
    int c;
    int tot = 0;

    for (r = 0; r < rows; r++)
        for (c = 0; c < COLS; c++)
            tot += ar[r][c];

    return tot;
}

int sum2d2(int ar[ROWS][COLS])
{
    int r;
    int c;
    int tot = 0;

    for (r = 0; r < ROWS; r++)
        for (c = 0; c < COLS; c++)
            tot += ar[r][c];

    return tot;
}
```

```C
int sum(int ar[][], int rows);		// 错误的声明
int sum(int ar[][4], int rows);		// 有效声明
int sum(int ar[3][4], int rows);	// 有效声明，但是3将被忽略
```

与使用 typedef 相比，这种形式方便得多：

```C
typedef int arr4[4];				// arr4 是一个内含 4 个 int 的数组
typedef arr4 arr3x4[3];				// arr3x4 是一个内含 3 个 arr4 的数组
int sum(arr3x4 ar, int rows);		// 与下面的声明相同
int sum(int ar[3][4], int rows);	// 与下面的声明相同
int sum(int ar[][4], int rows);		// 标准形式
```

一般而言，声明一个指向N维数组的指针时，只能省略最左边方括号中的值：

```C
int sum4d(int ar[][12][20][30], int rows);
int sum4d(int (*ar)[12][20][30], int rows);
```
###10.8 变长数组（VLA） 309 

示例：

```C
//vararr2d.c -- functions using VLAs
#include <stdio.h>
#define ROWS 3
#define COLS 4
int sum2d(int rows, int cols, int ar[rows][cols]);
int main(void)
{
    int i, j;
    int rs = 3;
    int cs = 10;
    int junk[ROWS][COLS] = {
        {2,4,6,8},
        {3,5,7,9},
        {12,10,8,6}
    };
    
    int morejunk[ROWS-1][COLS+2] = {
        {20,30,40,50,60,70},
        {5,6,7,8,9,10}
    };
    
    int varr[rs][cs];  // VLA
    
    for (i = 0; i < rs; i++)
        for (j = 0; j < cs; j++)
            varr[i][j] = i * j + j;
    
    printf("3x5 array\n");
    printf("Sum of all elements = %d\n",
           sum2d(ROWS, COLS, junk));
    
    printf("2x6 array\n");
    printf("Sum of all elements = %d\n",
           sum2d(ROWS-1, COLS+2, morejunk));
    
    printf("3x10 VLA\n");
    printf("Sum of all elements = %d\n",
           sum2d(rs, cs, varr));
    
    return 0;
}

// function with a VLA parameter
int sum2d(int rows, int cols, int ar[rows][cols])
{
    int r;
    int c;
    int tot = 0;
    
    for (r = 0; r < rows; r++)
        for (c = 0; c < cols; c++)
            tot += ar[r][c];
    
    return tot;
}
```
###10.9 复合字面量 312 

C99 新增了复合字面量。

字面量是除符号常量外的常量。例如，5 是 int 类型字面量。

对于数组，复合字面量类似数组初始化列表，前面是用括号括起来的类型名。例如，下面是一个普通的数组声明：

```C
int diva[2] = {10, 20};
```

下面的复合字面量创建了一个和 diva 数组相同的匿名数组，也有两个 int 类型的值：

```C
(int [2]){10, 20}		// 复合字面量
(int []){50, 20, 90}	// 内含 3 个元素的复合字面量
```

因为复合字面量是匿名的，所以不能先创建然后再使用它，必须在创建的同时使用它。使用指针记录地址就是一种用法。

```C
int * pt1;
pt1 = (int [2]){10, 20};
```

可以把复合字面量作为实际参数传递给带有匹配形式参数的函数：

```C
int sum(const int ar[], int n);
...
int total3;
total3 = sum((int []){4,4,4,5,5,5},6)
```

用于二维数组或多维数组：

```C
int (*pt2)[4];		// 声明一个指向二维数组的指针，该数组内含 2 个数组元素，每个元素是内含 4 个 int 类型值的数组
pt2 = (int [2][4]){1,2,3,-9}, {4,5,6,-8};
```
示例：
```C
// flc.c -- funny-looking constants
#include <stdio.h>
#define COLS 4
int sum2d(const int ar[][COLS], int rows);
int sum(const int ar[], int n);
int main(void)
{
    int total1, total2, total3;
    int * pt1;
    int (*pt2)[COLS];
    
    pt1 = (int [2]) {10, 20};
    pt2 = (int [2][COLS]) { {1,2,3,-9}, {4,5,6,-8} };
    
    total1 = sum(pt1, 2);
    total2 = sum2d(pt2, 2);
    total3 = sum((int []){4,4,4,5,5,5}, 6);
    printf("total1 = %d\n", total1);
    printf("total2 = %d\n", total2);
    printf("total3 = %d\n", total3);
    
    return 0;
}

int sum(const int ar[], int n)
{
    int i;
    int total = 0;
    
    for( i = 0; i < n; i++)
        total += ar[i];
    
    return total;
}

int sum2d(const int ar[][COLS], int rows)
{
    int r;
    int c;
    int tot = 0;
    
    for (r = 0; r < rows; r++)
        for (c = 0; c < COLS; c++)
            tot += ar[r][c];
    
    return tot;
}
```

###10.10 关键概念 314 
###10.11 本章小结 315 
###10.12 复习题 316 

4. 在下面的代码中，`*ptr` 和 `*(ptr + 2)` 的值分别是什么？

   a.

   ```C
   int *ptr;
   int torf[2][2] = {12,14,16};
   ptr = torf[0];
   ```

   b.

   ```C
   int *ptr;
   int fort[2][2] = {{12},{14,16}};
   ptr = fort[0];
   ```
   答案：

   ptr 指向第 1 个元素，ptr + 2 指向第 3 个元素（即第 2 行的第 1 个元素）。

   a. 12 和 16。

   b. 12 和 14。

5. 在下面的代码中，`**ptr` 和 `**(ptr + 1) `的值分别是什么？

   a.

   ```C
   int (*ptr)[2];
   int torf[2][2] = {12,14,16};
   ptr = torf;
   ```

   b.

   ```C
   int (*ptr)[2];
   int fort[2][2] = {{12},{14,16}};
   ptr = fort;
   ```
   答案：

   ptr 指向第 1 行，ptr + 1 指向第 2 行。`*ptr` 指向第 1 行的第 1 个元素，而`*(ptr + 1)` 指向第 2 行的第 1 个元素。

   a. 12 和 16。

   b. 12 和 14。


###10.13 编程练习 317 
##第11章　字符串和字符串函数 321 
###11.1 表示字符串和字符串I/O 321 
####11.1.1 在程序中定义字符串 322 
####11.1.2 指针和字符串 328 
###11.2 字符串输入 329 
####11.2.1 分配空间 329 
####11.2.2 不幸的gets()函数 330 
####11.2.3 gets()的替代品 331 
####11.2.4 scanf()函数 336 
###11.3 字符串输出 337 
####11.3.1 puts()函数 338 
####11.3.2 fputs()函数 339 
####11.3.3 printf()函数 339 
###11.4 自定义输入/输出函数 340 
###11.5 字符串函数 342 
####11.5.1 strlen()函数 342 
####11.5.2 strcat()函数 343 
####11.5.3 strncat()函数 345 
####11.5.4 strcmp()函数 346 
####11.5.5 strcpy()和strncpy()函数 351 
####11.5.6 sprintf()函数 356 
####11.5.7 其他字符串函数 357 
###11.6 字符串示例：字符串排序 359 
####11.6.1 排序指针而非字符串 360 
####11.6.2 选择排序算法 361 
###11.7 ctype.h字符函数和字符串 362 
###11.8 命令行参数 363 
####11.8.1 集成环境中的命令行参数 365 
####11.8.2 Macintosh中的命令行参数 365 
###11.9 把字符串转换为数字 365 
###11.10 关键概念 368 
###11.11 本章小结 368 
###11.12 复习题 369 
###11.13 编程练习 371 
##第12章　存储类别、链接和内存管理 373 
###12.1 存储类别 373 
####12.1.1 作用域 374 
####12.1.2 链接 376 
####12.1.3 存储期 376 
####12.1.4 自动变量 377 
####12.1.5 寄存器变量 380 
####12.1.6 块作用域的静态变量 381 
####12.1.7 外部链接的静态变量 382 
####12.1.8 内部链接的静态变量 386 
####12.1.9 多文件 386 
####12.1.10 存储类别说明符 387 
####12.1.11 存储类别和函数 389 
####12.1.12 存储类别的选择 389 
###12.2 随机数函数和静态变量 390 
###12.3 掷骰子 393 
###12.4 分配内存：malloc()和free() 396 

​	malloc ( ) 函数接受 —个参数：所需的内存字节数。函数会找到合适的空闲内存块，这样的内存是匿名的。也就是说， malloc ( ) 分配内存，但是不会为其赋名。然而，它确实返回动态分配内存块的首字节地址。因此，可以把该地址赋给一个指针变量，并使用指针访问这块内存。因为 char 表示 1 字节，malloc ( ) 的返回类型通常被定义为指向 char 的指针。然而，从 ANSI C 标准开始，C 使用一个新的类型：指向 void 的指针。该类型相当于一个“通用指针”。malloc ( ) 函数可用于返回指向数组的指针、指向结构的指针等，所以通常该函数的返回值会被强制转换为匹配的类型。在 ANSI C 中，应该坚持使用强制类型转换，提高代码的可读性。 然而，把指向 void 的指针赋给任意类型的指针完全不用考虑类型匹配的问题。如果 malloc ( ) 分配内存失败，将返回空指针。

​	我们试着用 malloc ( ) 创建一个数组。除了用 malloc ( ) 在程序运行时请求一块内存，还需要一个指针记录这块内存的位置。例如，考虑下面的代码：
```c
double * ptd;
ptd = (double *) malloc (30 * sizeof(double));
```
​	以上代码为 30 个 double 类型的值请求内存空间，并设置 ptd 指向该位置。注意，指针 ptd 被声明为指向一个 double 类型，而不是指向内含 30 个 double 类型值的块。回忆一下，数组名是该数组首元素的地址。因此，如果让 ptd 指向这个块的首元素，便可像使用数组名一样使用它。也就是说，可以使用表达式 ptd[0] 访问该块的首元素，ptd[1] 访问第 2 个元素，以此类推。根据前面所学的知识，可以使用数组名来表示指针，也可以用指针来表示数组。

​	现在，我们有3种创建数组的方法。

- 声明数组时，用常量表达式表示数组的维度，用数组名访问数组的元素。可以用静态内存或自动内存创建这种数组。
- 声明变长数组（C99新增的特性）时，用变量表达式表示数组的维度，用数组名访问数组的元素。具有这种特性的数组只能在自动内存中创建。
- 声明一个指针，调用 malloc ( ) ，将其返回值赋给指针，使用指针访问数组的元素。该指针可以是静态的或自动的。

####12.4.1 free()的重要性 399 
####12.4.2 calloc()函数 400 
####12.4.3 动态内存分配和变长数组 400 
####12.4.4 存储类别和动态内存分配 401 
###12.5 ANSI C 类型限定符 402 
####12.5.1 const 类型限定符 403 

1. 在指针和形参声明中使用 const
2. 对全局数据使用 const

####12.5.2 volatile 类型限定符 404 

volatile 限定符告知计算机，代理（而不是变量所在的程序）可以改变改变量的值。通常，它被用于硬件地址以及在其他程序或同时运行的线程中共享数据。

####12.5.3 restrict 类型限定符 405 

restrict 关键字允许编译器优化某部分代码以更好地支持计算。它只能用于指针，表明该指针是访问数据对象的唯一且初始的方式。

restrict 限定符还可用于函数形参中的指针。这意味着编译器可以假定在函数体内其他标识符不会修改该指针指向的数据，而且编译器可以尝试对其优化，使其不做别的用途。

restrict 关键字有两个读者。 一个是编译器，该关键字告知编译器可以自由假定一些优化方案。另一个读者是用户 ，该关键字告知用户要使用满足 restrict 要求的参数 。

####12.5.4 _Atomic类型限定符（C11） 406 

用于多线程。

####12.5.5 旧关键字的新位置 406 

C99 允许把类型限定符和存储类别说明符 static 放在函数原型和函数头的形式参数的初始方括号中。对于类型限定符而言，这样做为现有功能提供了一个替代的语法。例如，下面是旧式语法的声明：
```c
void ofmouth(int * const al, int * restrict a2, int n);// 以前的风格
```

该声明表明 a1 是一个指向 int 的 const 指针，这意味着不能更改指针本身，可以更改指针指向的数据。除此之外，还 表明 a2 是一个 restrict 指针，如上一节所述。新的等价语法如下：
```c
void ofmouth(int al [const], int a2 [restrict], int n);// C99 允许
```

根据新标准，在声明函数形参时，指针表示法和数组表示法都可以使用这两个限定符。

static 的情况不同，因为新标准为 static 引入了一种与以前用法不相关的新用法。现在，static 除了表明静态存储类别变量的作用域或链接外，新的用法告知编译器如何使用形式参数。例如，考虑下面的原型：
```c
double stick(double ar[static 20]);
```
static 的这种用法表明，函数调用中的实际参数应该是一个指向数组首元素的指针，且该数组至少有 20 个元素。这种用法的目的是让编译器使用这些信息优化函数的编码。为何给 static 新增一个完全不同的用法？C 标准委员会不愿意创建新的关键字，因为这样会让以前用新关键字作为标识符的程序无效。所以，他们会尽量利用现有的关键 字，尽量不添加新的关键字。

###12.6　关键概念 407 

​	C 提供多种管理内存的模型。除了熟悉这些模型外，还要学会如何选择不同的类別。大多数情况下， 最好选择自动变量。如果要使用其他类别，应该有充分的理由。通常，使用自动变量、函数形参和返冋值进行函数间的通信比使用全局变量安全。但是，保持不变的数据适合用全局变量。

​	应该尽量理解静态内存、自动内存和动态分配内存的属性。尤其要注意：静态内存的数量在编译时确定；静态数据在载入程序时被载入内存。在程序运行时，自动变量被分配或释放，所以自动变量占用的内存数量随着程序的运行会不断变化。可以把自动内存看作是可重复利用的工作区。动态分配的内存也会增加和减少，但是这个过程由函数调用控制，不是自动进行的。

###12.7 本章小结 407 

​	内存用于存储程序中的数据，由存储期、作用域和链接表征。存储期可以是静态的、自动的或动态分配的。如果是静态存储期，在程序幵始执行时分配内存，并在程序运行时都存在。如果是自动存储期，在程序进入变量定义所在块时分配变量的内存，在程序离幵块时释放内存。如果是动态分配存储期，在调用 malloc ( ) （或相关函数）时分配内存，在调用 free ( ) 函数时释放内存。

​	作用域决定程序的哪些部分可以访问某数据。定义在所有函数之外的变量具有文件作用域，对位于该变量声 明之的所有函数可见。定义在块或作为函数形参内的变量具有块作用域，只对该块以及它包含的嵌套块可见。

​	链接描述定义在程序某翻译单元中的变量可被链接的程度。具有块作用域的变量是局部变量，无链接。 具有文件作用域的变量可以是内部链接或外部链接。内部链接意味着只有其定义所在的文件才能使用该变 量。外部链接意味着其他文件使用也可以使用该变量。

​	下面是 C 的5种存储类別（不包括线程的概念）。

- **自动**——在块中不带存储类别说明符或带 auto 存储类别说明符声明的变量（或作为函数头中的形参）属于自动存储类别，具有自动存储期、块作用域、无链接。如果未初始化自动变量，它的值是未定义的。
- **寄存器**——在块中带 register 存储类别说明符声明的变量（或作为函数头中的形参）属于寄存器存储类别，具有自动存储期、块作用域、无链接，且无法获取其地址。把一个变量声明为寄存器变量即请求编译器将其储存到访问速度最快的区域。如果未初始化寄存器变量，它的值是未定义的。
- **静态、无链接**——在块中带 static 存储类别说明符声明的变量属于“静态、无链接”存储类别，具有静态存储期、块作用域、无链接。只在编译时被初始化一次。如果未显式初始化，它的字节都被设置为 0 。
- **静态、外部链接**——在所有函数外部且没有使用 static 存储类別说明符声明的变量属于“静态、外部链接”存储类别，具有静态存储期、文件作用域、外部链接。只能在编译器被初始化一次。如果未显式初始化，它的字节都被设置为 0 。
- **静态、内部链接**——在所有函数外部且使用了 static 存储类别说明符声明的变量厲于“静态、内部链接”存储类别，具有静态存储期、文件作用域、内部链接。只能在编译器被初始化一次。如果未显式初始化，它的字节都被设置为 0 。

  ​动态分配的内存由 malloc ( ) （或相关）函数分配，该函数返回一个指向指定字节数内存块的指针。这块内存被 free ( ) 函数释放后便可重复使用，free ( ) 函数以该内存块的地址作为参数。

  ​类型限定符 const、volatile、restrict 和 _Atomic 。const 限定符限定数据在程序运行时不能改变。对指针使用 const 时，可限定指针本身不能改变或指针指向的数据不能改变，这取决于 const 在指针声明中的位置。volatile 限定符表明，限定的数据除了被当前程序修改外还可以被其他进程修改。该限定符的目的是警告编译器不要进行假定的优化。restrict 限定符也是为了方便编译器设置优化方案。restrict 限定的指针是访问它所指向数据的唯一途径。

###12.8 复习题 408 
###12.9 编程练习 409 
##第13章　文件输入/输出 413 
###13.1 与文件进行通信 413 
####13.1.1 文件是什么 413 

​	文件（file）通常是在磁盘或固态硬盘上的一段已命名的存储区。

​	C 把文件看作是一系列连续的字节，每个字节都能被单独读取。这与 UNIX 环境中（C的发源地）的文件结构相对应。由于其他环境中可能无法完全对应这个模型，C 提供两种文件模式：==文本模式==和==二进制模式==。

####13.1.2 文本模式和二进制模式 413 

​	所有文件的内容都以二进制形式（0或1）储存。但是，如果文件最初使用二进制编码的字符（例如，ASCII或Unicode）表示文本（就像 C 字符串那样），该文件就是==文本文件==，其中包含==文本内容==。如果文件中的二进制值代表机器语言代码或数值数据（使用相同的内部表示，假设，用于 long 或 double 类别的值）或图片或音乐编码，该文件就是==二进制文件==，其中包含==二进制内容==。

####13.1.3 I/O 的级别 415 

​	底层 I/O（low-level I/O）使用操作系统提供的基本 I/O 服务。标准高级 I/O（standard high-level I/O）使用 C 库的标准包和 stdio.h 头文件定义。

####13.1.4 标准文件 415 

​	C 程序会自动打开 3 个文件，它们被称为标准输入（standard input）、标准输出（standard output）和标 准错误输出（standard error output）。

###13.2 标准 I/O 415 

​	与底层 I/O 相比，标准 I/O 包除了可移植以外还有两个好处。第一，标准 I/O 有许多专门的函数简化了处理不同 I/O 的问题。第二，输入和输出都是缓冲的。

####13.2.1 检查命令行参数 416 

​	字符串 argv[0] 是该程序的名称。

​	exit ( ) 函数关闭所有打开的文件并结束程序。exit ( ) 的参数被传递给一些操作系统，包括 UNIX、Linux、Windows 和 MS-DOS，以供其他程序使用。0 或宏 EXIT_SUCCESS 用于表明成功结束程序，宏 EXIT_FAILURE 用于表明结束程序失败，是非零值。

####13.2.2 fopen ( ) 函数 416 

​	使用 fopen ( ) 函数打开文件。该函数声明在stdio.h中。它的第 1 个参数是待打开文件的名称，更确切地说是一个包含该文件名的字符串地址。第 2 个参数是一个字符串，指定待打开文件的模式。下表列出了 C 库提供的一些模式。

| 模式字符串                                   | 含义                                       |
| --------------------------------------- | ---------------------------------------- |
| "r"                                     | 以读模式打开文件                                 |
| "w"                                     | 以写模式打开文件，把现有文件的长度截为0，如果文件不存在，则创建一个新文件    |
| "a"                                     | 以写模式打开文件，在现有文件末尾添加内容，如果文件不存在，则创建一个新文件    |
| "r+"                                    | 以更新模式打开文件（即可以读写文件）                       |
| "w+"                                    | 以更新模式打开文件（即，读和写），如果文件存在，则将其长度截为0；如果文件不存在，则创建一个新文件 |
| "a+"                                    | 以更新模式打开文件（即，读和写），在现有文件的末尾添加内容，如果文件不存在则创建一个新文件；可以读整个文件，但是只能从末尾添加内容 |
| "rb"、"wb"、"ab"、"ab+"、 "a+b"、"wb+"、"w+b" | 与上一个模式类似，但是以二进制模式而不是文本模式打开文件             |
| "wx"、"wbx"、"w+x"、"wb+x"或"w+bx"          | (C11 )类似非x模式，但是如果文件已存在或以独占模式打开文件，则打开文件失败 |

####13.2.3 getc ( ) 和 putc ( ) 函数 417 

下面这条语句的意思是“从标准输入中获取一个字符”：

`ch = getchar();`

然而，下面这条语句的意思是“从 fp 指定的文件中获取一个字符”:

`ch = getc(fp);`

与此类似，下面语句的意思是“把字符 ch 放入 FILE 指针 fpout 指定的文件中”：

`putc(ch, fpout);`

在 putc ( ) 函数的参数列表中，第1个参数是待写入的字符，第2个参数是文件指针。

####13.2.4 文件结尾 418 

如果 `getc ( )` 函数在读取一个字符时发现是文件结尾，它将返回一个特殊值 `EOF`。

```c
//设计范例
int ch;
FILE * fp;
fp = fopen("wacky.txt", "r"); 
while ((ch = getc(fp)) != EOF)
{
	putchar(ch);    //处理输入
}
```

####13.2.5 fclose ( ) 函数 419 

​	`fclose (fp)` 函数关闭 fp 指定的文件，必要时刷新缓冲区。对于较正式的程序，应该检查是否成功关闭文件。如果成功关闭，`fclose ( )` 函数返回 0 ，否则返回 `EOF` 。

####13.2.6 指向标准文件的指针 419 

​	stdio.h头文件把3个文件指针与3个标准文件相关联，C程序会自动打开这3个标准文件。如表所示:

| 标准文件 | 文件指针   | 通常使用的设备 |
| ---- | ------ | ------- |
| 标准输入 | stdin  | 键盘      |
| 标准输出 | stdout | 显示器     |
| 标准错误 | stderr | 显示器     |
​	这些文件指针都是指向 FILE 的指针，所以它们可用作标准 I/O 函数的参数。
###13.3 一个简单的文件压缩程序 419 

```c
// reducto.c -- reduces your files by two-thirds!
#include <stdio.h>
#include <stdlib.h>    // for exit()
#include <string.h>    // for strcpy(), strcat()
#define LEN 40

int main(int argc, char *argv[])
{
    FILE  *in, *out;   // declare two FILE pointers
    int ch;
    char name[LEN];    // storage for output filename
    int count = 0;
    
    // check for command-line arguments
    if (argc < 2)
    {
        fprintf(stderr, "Usage: %s filename\n", argv[0]);
        exit(EXIT_FAILURE);
    }
    // set up input
    if ((in = fopen(argv[1], "r")) == NULL)
    {
        fprintf(stderr, "I couldn't open the file \"%s\"\n",
                argv[1]);
        exit(EXIT_FAILURE);
    }
    // set up output
    strncpy(name,argv[1], LEN - 5); // copy filename
    name[LEN - 5] = '\0';
    strcat(name,".red");            // append .red
    if ((out = fopen(name, "w")) == NULL)
    {                       // open file for writing
        fprintf(stderr,"Can't create output file.\n");
        exit(3);
    }
    // copy data
    while ((ch = getc(in)) != EOF)
        if (count++ % 3 == 0)
            putc(ch, out);  // print every 3rd char
    // clean up
    if (fclose(in) != 0 || fclose(out) != 0)
        fprintf(stderr,"Error in closing files\n");
    
    return 0;
}
```



###13.4 文件I/O：fprintf ( ) 、fscanf ( ) 、fgets ( ) 和 fputs ( )  421 
####13.4.1 fprintf ( ) 和 fscanf ( ) 函数 421 

```c
fscanf(stdin,"%40s", words);
fprintf(stdout,"Can't open \"wordy\" file.\n");
rewind(fp);           /* 返回到文件开始处 */
```

示例：

```c
/* addaword.c -- uses fprintf(), fscanf(), and rewind() */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 41

int main(void) {
    FILE *fp;
    char words[MAX];

    if ((fp = fopen("wordy", "a+")) == NULL) {
        fprintf(stdout, "Can't open \"wordy\" file.\n");
        exit(EXIT_FAILURE);
    }

    puts("Enter words to add to the file; press the #");
    puts("key at the beginning of a line to terminate.");
    while ((fscanf(stdin, "%40s", words) == 1) && (words[0] != '#'))
        fprintf(fp, "%s\n", words);

    puts("File contents:");
    rewind(fp);           /* go back to beginning of file */
    while (fscanf(fp, "%s", words) == 1)
        puts(words);
    puts("Done!");
    if (fclose(fp) != 0)
        fprintf(stderr, "Error closing file\n");

    return 0;
}
```



####13.4.2 fgets ( ) 和 fputs ( ) 函数 422 

​	`fgets (buf, STLEN, fp);` buf 是 char 类型数组的名称，STLEN 是字符串的大小，fp 是指向 FILE 的指针。 fgets ( ) 函数读取输入直到第1个换行符的后面，或读到文件结尾，或者读取STLEN-1个字符。

​	`fputs(buf, fp);` buf 是字符串的地址，fp 用于指定目标文件。fputs ( ) 在打印字符串时不会在其末尾添加换行符。

###13.5 随机访问：fseek ( ) 和 ftell ( )  423 
####13.5.1 fseek ( ) 和 ftell ( ) 的工作原理 424 

​	fseek ( ) 的第 1 个参数是 FILE 指针，指向待査找的文件，fopen ( ) 应该已打开该文件。

​	fseek ( ) 的第 2 个参数是偏移量该参数表示从起始点开始要移动的距离（参见下表列出的起始点模式）。该参数必须是一个 long 类型的值，可以为正（前移）、负（后移）或 0 （保持不动）。

​	fseek ( ) 的第 3 个参数是模式，该参数确定起始点。根据 ANSI 标准，在 stdio.h 头文件中规定了几 个表示模式的明示常量。如下表：

| 模式       | 偏移量的起始点 |
| -------- | ------- |
| SEEK_SET | 文件开始处   |
| SEEK_CUR | 当前位置    |
| SEEK_END | 文件末尾    |
​	下面是调用 fseek ( ) 函数的一些示例，fp 是一个文件指针：
```c
fseek(fp, 0L, SEEK_SET);	//定位至文件开始处

fseek(fp, 10L, SEEK_SET);	//定位至文件中的第10个字节 

fseek(fp, 2L, SEEK CUR);	//从文件当前位置前移2个字节

fseek(fp, 0L, SEEK_END);	// 定位至文件结尾 

fseek(fp, -10L, SEEK_END);	//从文件结尾处回退10个字节
```
​	ftell ( ) 函数的返回类型是long，它返回的是当前的位置。
####13.5.2 二进制模式和文本模式 425 

​	许多 MS-DOS 编辑器都用   `Ctrl+Z` 标记文本文件的结尾。

​	MS-DOS 用   `\r\n` 组合表示文本文件换行。

####13.5.3 可移植性 425 

​	理论上，fseek ( ) 和 ftell ( ) 应该符合 UNIX 模型。但是，不同系统存在着差异，有时确实无法做到与 UNIX 模型一致。因此，ANSI 对这些函数降低了要求。下面是一些限制。

- 在二进制模式中，实现不必支持 SEEK_END 模式。移植性更高的方法是逐字节读取整个文件直到文件末尾。C预处理器的条件编译指令提供了一种系统方法来处理这种情况。
- 在文本模式中，只有以下调用能保证其相应的行为。

| 函数调用                              | 效果                                       |
| --------------------------------- | ---------------------------------------- |
| fseek(file, 0L, SEEK_SET)         | 定位至文件开始处                                 |
| fseek(file, 0L, SEEK_CUR)         | 保持当前位置不动                                 |
| fseek(file, 0L, SEEK_END)         | 定位至文件结尾                                  |
| fseek (file, ftell-pos, SEEK_SET) | 到距文件开始处 ftell-pos 的位置， ftell-pos 是 ftell ( ) 的返回值 |

####13.5.4 fgetpos ( ) 和 fsetpos ( ) 函数 426 

​	两个处理较大文件的新定位函数：fgetpos ( ) 和 fsetpos ( ) 。这两个函数不使用 long 类型的值表示位置，它们使用一种新类型：fpos_t （代表 file position type，文件定位类型）。fpos_t 类型不是基本类型，它根据其他类型来定义。fpos_t 类型的变量或数据对象可以在文件中指定一个位置，它不能是数组类型，除此之外，没有其他限制。实现可以提供一个满足特殊平台要求的类型，例如，fpos_t 可以实现为结构。

​	ANSI C 定义了如何使用 fpos_t 类型。fgetpos ( ) 函数的原型如下：

  ```c
int fgetpos(FILE * restrict stream, fpos_t * restrict pos);
  ```
​	调用该函数时，它把 fpos_t 类型的值放在 pos 指向的位置上，该值描述了文件中的一个位置。如果成功，fgetpos ( ) 函数返回0；如果失败，返冋非0。

​	fsetpos ( ) 函数的原型如下:
```c
int fsetpos(FILE * stream, const fpos_t * pos);
```
​	调用该函数时，使用 pos 指向位置上的 fpos_t 类型值来设置文件指针指向该值指定的位置。如果成功，fsetpos ( ) 函数返回 0 ；如果失败，则返回非 0 。fpos_t 类型的值应通过之前调用 fgetpos ( ) 获得。

###13.6 标准 I/O 的机理 426 

​	我们在前面学习了标准 I/O 包的特性，本节研究一个典型的概念模型，分析标准 I/O 的工作原理。

​	通常，使用标准 I/O 的第 1 步是调用 fopen ( ) 打开文件（前面介绍过，C 程序会自动打开 3 种标准文件）。fopen ( ) 函数不仅打开一个文件，还创建了一个缓冲区（在读写模式下会创建两个缓冲区）以及一个包含文件和缓冲区数据的结构。另外，fopen ( ) 返回一个指向该结构的指针，以便其他函数知道如何找到该结构。假设把该指针赋给一个指针变量 fp，我们说 fopen ( ) 函数“打开一个流”。如果以文本模式打开该文件，就获得一个文本流；如果以二进制模式打开该文件，就获得一个二进制流。

​	这个结构通常包含一个指定流中当前位置的文件位置指示器。除此之外，它还包含错误和文件结尾的指示器、一个指向缓冲区开始处的指针、一个文件标识符和一个计数（统计实际拷贝进缓冲区的字节数）。

​	我们主要考虑文件输入。通常，使用标准 I/O 的第 2 步是调用一个定义在 stdio.h 中的输入函数，如 fscanf ( ) 、getc ( ) 或 fgets ( ) 。一调用这些函数，文件中的数据块就被拷贝到缓冲区中。缓冲区的大小因实现而异，一般是 512 字节或是它的倍数，如 4096 或 16384（随着计算机硬盘界量越来越人，缓冲区的大小也越来越大）。最初调用函数，除了填充缓冲区外，还要设置 fp 所指向的结构中的值。尤其要设置流中的当前位置和拷贝进缓冲区的字节数。通常，当前位置从字节 0 开始。

​	在初始化结构和缓冲区后，输入函数按要求从缓冲区中读取数据。在它读取数据时，文件位置指示器被设置为指向刚读取字符的下一个字符。由于 stdio.h 系列的所有输入函数都使用相同的缓冲区，所以调用任何一个函数都将从上—次函数停止调用的位置开始。

​	当输入函数发现己读完缓冲区中的所有字符时，会请求把下—个缓冲大小的数据块从文件拷贝到该缓冲区中。以这种方式，输入函数可以读取文件中的所有内容，直到文件结尾。函数在读取缓冲区中的最后一个字符后，把结尾指示器设置为真。于是，下一次被调用的输入函数将返回 EOF 。

​	输出函数以类似的方式把数据写入缓冲区。当缓冲区被填满时，数据将被拷贝至文件中。

###13.7 其他标准 I/O 函数 427 
####13.7.1 int ungetc (int c， FILE *fp) 函数 427 

​	`int ungetc ( )` 函数把 c 指定的字符放回输入流中。

####13.7.2 int fflush ( ) 函数 428 

​	fflush ( ) 函数的原型如下：
```c
int fflush(FILE *fp);
```
​	调用 fflush ( ) 函数引起输出缓冲区中所有的未写入数据被发送到 fp 指定的输出文件。这个过程称为刷新缓冲区。如果 fp 是空指针，所有输出缓冲区都被刷新。在输入流中使用 fflush ( ) 函数的效果是未定义的。

####13.7.3 int setvbuf ( ) 函数 428 

​	setvbuf ( ) 函数的原型是：
```c
int setvbuf(FILE * restrict fp, char * restrict buf, int mode, size_t size);
```
​	setvbuf ( ) 函数创建了一个供标准 I/O 函数替换使用的缓冲i。在打开文件后且未对流进行其他操作之前，调用该函数。指针 fp 识别待处理的流，buf 指向待使用的存储区。如果 buf 的值不是 NULL，则必须创建一个缓冲区。例如，声明一个内含 1024 个字符的数组，并传递该数组的地址。然而，如果把 NULL 作为 buf 的值，该函数会为自己分配一个缓冲区。变量 size 告诉 setvbuf ( ) 数组的大小。mode 的选择如下：`_IOFBF` 表示完全缓冲(在缓冲区满时刷新）；`_IOLBF` 表示行缓冲（在缓冲区满时或写入一个换行符时）；`_IONBF`表示无缓冲。如果操作成功，函数返回 0，否则返回一个非零值。

####13.7.4 二进制 I/O：fread ( ) 和 fwrite ( )  428 

​	如果以程序所用的表示法把数据储存在文件中，则称以二进制形式储存数据。

​	所有的数据都是以二进制形式储存的，甚至连字符都以字符码的二进制表示来储存。如果文件中的所有数据都被解释成字符码，则称该文件包含文本数据。如果部分或所有的数据都被解释成二进制形式的数值数据，则称该文件包含二进制数据。

####13.7.5 size_t fwrite ( ) 函数 429 

​	fwrite ( ) 函数的原型如下：
```c
size t fwrite (const void * restrict ptr, size_t size, size_t nmemb, FILE * restrict fp);
```
​	fwrite ( ) 函数把二进制数据写入文件。size_t 是根据标准 C 类型定义的类型，它是 sizeof 运算符返回的类型，通常是 unsigned int，但是实现可以选择使用其他类型。指针 ptr 是待写入数据块的地址。size 表示待写入数据块的大小（以字节为单位），nmemb 表示待写入数据块的数量。和其他函数一样，fp 指定待写入的文件。例如，要保存一个大小为256字节的数据对象（如数组），可以这样做：
```c
char buffer[256];
fwrite(buffer, 256, 1, fp);
```

​	以上调用把一块 256 字节的数据从 buffer 写入文件。另举一例，要保存一个内含 10 个 double 类型值的数组，可以这样做：
```c
double earnings[10];
fwrite(earnings, sizeof(double), 10, fp);
```

​	以上调用把 earnings 数组中的数据写入文件，数据被分成10块，每块都是 double 的大小。

​	注意 fwrite ( ) 原型中的`const void * restrict ptr` 声明。fwrite ( ) 的—个问题是，它的第 1 个参数不是固定的类型。例如，第 1 个例子中使用 buffer，其类型是指向 char 的指针；而第 2 个例子中使用 earnings，其类型是指向 double 的指针。在 ANSI C 函数原型中，这些实际参数都被转换成指向 void 的指针类型，这种指针可作为一种通用类型指针（在 ANSI C 之前，这些参数使用 `char *` 类型，需要把实参强制转换成 `char *` 类型）。

​	fwrite ( ) 函数返回成功写入项的数量。正常情况下，该返回值就是 nmemb，但如果出现写入错误，返回值会比 nmemb 小。

####13.7.6 size_t fread ( ) 函数 430 

​	size_t fread ( ) 函数的原型如下：
```c
size_t fread(void * restrict ptr, size_t size, size_t nmemb, FILE * restrict fp);
```
​	fread ( ) 函数接受的参数和 fwrite ( ) 函数相同。在 fread ( ) 函数中，ptr 是待读取文件数据在内存中的地址，fp 指定待读取的文件。该函数用于读取被 fwrite ( ) 写入文件的数据。例如，要恢复上例中保存的内含 10 个 double 类型值的数组，可以这样做：
```c
double earnings [10];
fread(earnings, sizeof (double), 10, fp);
```
​	该调用把 10 个 double 大小的值拷贝进 earnings 数组中。

​	fread ( ) 函数返回成功读取项的数量。正常情况下，该返冋值就是 nmemb，但如果出现读取错误或读到文件结尾，该返回值就会比 nmemb 小。

####13.7.7 int feof (FILE *fp) 和 int ferror (FILE *fp) 函数 430 

​	如果标准输入函数返回 EOF ，则通常表明函数己到达文件结尾。然而，出现读取错误时，确数也会返回EOF。feof ( ) 和 ferror ( ) 函数用于区分这两种情况。当上一次输入调用检测到文件结尾时，feof ( ) 函数返回一个非零值，否则返回 0 。当读或写出现错误，ferror ( ) 函数返回—个非零值，否则返冋 0 。

####13.7.8 一个程序示例 430 

```c
/* append.c -- appends files to a file */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define BUFSIZE 4096
#define SLEN 81
void append(FILE *source, FILE *dest);
char * s_gets(char * st, int n);

int main(void)
{
    FILE *fa, *fs;	// fa for append file, fs for source file
    int files = 0;  // number of files appended
    char file_app[SLEN];  // name of append file
    char file_src[SLEN];  // name of source file
    int ch;
    
    puts("Enter name of destination file:");
    s_gets(file_app, SLEN);
    if ((fa = fopen(file_app, "a+")) == NULL)
    {
        fprintf(stderr, "Can't open %s\n", file_app);
        exit(EXIT_FAILURE);
    }
    if (setvbuf(fa, NULL, _IOFBF, BUFSIZE) != 0)
    {
        fputs("Can't create output buffer\n", stderr);
        exit(EXIT_FAILURE);
    }
    puts("Enter name of first source file (empty line to quit):");
    while (s_gets(file_src, SLEN) && file_src[0] != '\0')
    {
        if (strcmp(file_src, file_app) == 0)
            fputs("Can't append file to itself\n",stderr);
        else if ((fs = fopen(file_src, "r")) == NULL)
            fprintf(stderr, "Can't open %s\n", file_src);
        else
        {
            if (setvbuf(fs, NULL, _IOFBF, BUFSIZE) != 0)
            {
                fputs("Can't create input buffer\n",stderr);
                continue;
            }
            append(fs, fa);
            if (ferror(fs) != 0)
                fprintf(stderr,"Error in reading file %s.\n",
                        file_src);
            if (ferror(fa) != 0)
                fprintf(stderr,"Error in writing file %s.\n",
                        file_app);
            fclose(fs);
            files++;
            printf("File %s appended.\n", file_src);
            puts("Next file (empty line to quit):");
        }
    }
    printf("Done appending. %d files appended.\n", files);
    rewind(fa);
    printf("%s contents:\n", file_app);
    while ((ch = getc(fa)) != EOF)
        putchar(ch);
    puts("Done displaying.");
    fclose(fa);
    
    return 0;
}

void append(FILE *source, FILE *dest)
{
    size_t bytes;
    static char temp[BUFSIZE]; // allocate once
    
    while ((bytes = fread(temp,sizeof(char),BUFSIZE,source)) > 0)
        fwrite(temp, sizeof (char), bytes, dest);
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;
    }
    return ret_val;
}
```



####13.7.9 用二进制 I/O 进行随机访问 433 

```c
/* randbin.c -- random access, binary i/o */
#include <stdio.h>
#include <stdlib.h>
#define ARSIZE 1000

int main()
{
    double numbers[ARSIZE];
    double value;
    const char * file = "numbers.dat";
    int i;
    long pos;
    FILE *iofile;
    
    // create a set of double values
    for(i = 0; i < ARSIZE; i++)
        numbers[i] = 100.0 * i + 1.0 / (i + 1);
    // attempt to open file
    if ((iofile = fopen(file, "wb")) == NULL)
    {
        fprintf(stderr, "Could not open %s for output.\n", file);
        exit(EXIT_FAILURE);
    }
    // write array in binary format to file
    fwrite(numbers, sizeof (double), ARSIZE, iofile);
    fclose(iofile);
    if ((iofile = fopen(file, "rb")) == NULL)
    {
        fprintf(stderr,
                "Could not open %s for random access.\n", file);
        exit(EXIT_FAILURE);
    }
    // read selected items from file
    printf("Enter an index in the range 0-%d.\n", ARSIZE - 1);
    while (scanf("%d", &i) == 1 && i >= 0 && i < ARSIZE)
    {
        pos = (long) i * sizeof(double); // calculate offset
        fseek(iofile, pos, SEEK_SET);    // go there
        fread(&value, sizeof (double), 1, iofile);
        printf("The value there is %f.\n", value);
        printf("Next index (out of range to quit):\n");
    }
    // finish up
    fclose(iofile);
    puts("Bye!");
    
    return 0;
}
```



###13.8 关键概念 435 

​	C 程序把输入看作是字节流，输入流来源于文件、输入设备（如键盘），或者甚至是另一个程序的输出。类似地，C 程序把输出也看作是字节流，输出流的目的地可以是文件、视频显示等。

​	C 如何解释输入流或输出流取决于所使用的输入/输出函数。程序可以不做任何改动地读取和存储字节，或者把字节依次解释成字符，随后可以把这些字符解释成普通文本以用文本表示数字。类似地，对于输出，所使用的函数决定了二进制值是被原样转移，还是被转换成文本或以文本表示数字。如果要在不损失精度的前提下保存或恢复数值数据，请使用二进制模式以及 fread ( ) 和 fwrite ( ) 函数。如果打算保存文本信息并创建能在普通文本编辑器查看的文本，请使用文本模式和函数（如 getc ( ) 和 fprintf ( ) ）。

​	要访问文件，必须创建文件指针（类型是 FILE* ）并把指针与特定文件名相关联。随后的代码就可以使用这个指针（而不是文件名）来处理该文件。

​	要重点理解 C 如何处理文件结尾。通常，用于读取文件的程序使用一个循环读取输入，直至到达文件结尾。C 输入函数在读过文件结尾后才会检测到文件结尾，这意味着应该在尝试读取之后立即判断是否是文件结尾。可以使用 13.2.4 节中“设计范例”中的双文件输入模式。

###13.9 本章小结 435 

​	对于大多数 C 程序而言，写入文件和读取文件必不可少。为此，绝大多数 C 实现都提供底层 I/O 和标准高级 I/O 。因为 ANSI C 库考虑到可移植性，包含了标准 I/O 包，但是未提供底层 I/O。

​	标准 I/O 包自动创建输入和输出缓冲区以加快数据传输。fopen ( ) 函数为标准 I/O 打开一个文件，并创建一个用于存储文件和缓冲区信息的结构。fopen ( ) 函数返回指向该结构的指针，其他函数可以使用该指针指定待处理的文件。feof ( ) 和 ferror ( ) 函数报告 I/O 操作失败的原因。

​	C 把输入视为字节流。如果使用 fread ( ) 函数，C 把输入看作是二进制值并将其储存在指定存储位置。 如果使用 fscanf ( ) 、getc ( ) 、fgets ( ) 或其他相关函数，C 则将每个字节看作是字符码。然后 fscanf ( ) 和 scanf ( ) 函数尝试把字符码翻译成转换说明指定的其他类型。例如，输入一个值 23，%f 转换说明会把 23 翻译成一个浮点值，％d 转换说明会把 23 翻译成一个整数值，％s 转换说明则会把 23 储存为字符牢。getc ( ) 和 fgetc ( ) 系列函数把输入作为字符码储存，将其作为单独的字符保存在字符变量中或作为字符串储存在字符数组中。类似地，fwrite ( ) 将二进制数椐直接放入输出流，而其他输出函数把非字符数倨转换成用字符表示后才将其放入输出流。

​	ANSI C 提供两种文件打开模式：二进制和文本。以二进制模式打开文件时，可以逐字节读取文件；以文本模式打开文件时，会把文件内容从文本的系统表示法映射为 C 表示法。对于 UNIX 和 Linux 系统，这两种模式完全相同。

​	通常，输入函数 getc ( ) 、fgets ( ) 、fscanf ( ) 和 fread ( ) 都从文件开始处按顺序读取文件。然而 fseek ( ) 和 ftell ( ) 函数让程序可以随机访问文件中的任意位置。fgetpos ( ) 和 fsetpos ( ) 把类似的功能扩展至更大的文件。与文本模式相比，二进制模式更容易进行随机访问。

###13.10 复习题 435 
###13.11 编程练习 437 
##第14章　结构和其他数据形式 439 
###14.1 示例问题：创建图书目录 439 

```c
//* book.c -- one-book inventory */
#include <stdio.h>
#include <string.h>

char *s_gets(char *st, int n);

#define MAXTITL  41      /* maximum length of title + 1         */
#define MAXAUTL  31      /* maximum length of author's name + 1 */

struct book {            /* structure template: tag is book     */
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};                       /* end of structure template           */

int main(void) {
    struct book library; /* declare library as a book variable  */

    printf("Please enter the book title.\n");
    s_gets(library.title, MAXTITL); /* access to the title portion         */
    printf("Now enter the author.\n");
    s_gets(library.author, MAXAUTL);
    printf("Now enter the value.\n");
    scanf("%f", &library.value);
    printf("%s by %s: $%.2f\n", library.title,
           library.author, library.value);
    printf("%s: \"%s\" ($%.2f)\n", library.author,
           library.title, library.value);
    printf("Done.\n");

    return 0;
}

char *s_gets(char *st, int n) {
    char *ret_val;
    char *find;

    ret_val = fgets(st, n, stdin);
    if (ret_val) {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```

###14.2 建立结构声明 441 

​	结构声明（structure declaration）描述了一个结构的组织布局。声明类似下面这样：
```c
struct book {
  char title[MAXTITL];
  char author[MAXAUTL]; 
  float value;
};
```
​	该声明描述了一个由两个字符数组和一个 float 类型变量组成的结构。该声明并未创建实际的数据对象，只描述了该对象由什么组成。首先是关键字 struct，它表明跟在其后的是一个结构，后面是一个可选的标记（该例中是book），稍后程序中可以使用该标记引用该结构。所以，我们在后面的程序中可以这样声明：
```c
struct book library;
```
​	这把 library 声明为一个使用 book 结构布局的结构变量。
###14.3 定义结构变量 441 

​	结构有两层含义。一层含义是“结构布局”，刚才已经讨论过了。结构布局告诉编译器如何表示数据，但是它并未让编译器为数据分配空间。下一步是创建一个结构变量，即是结构的另一层含义。程序中创建结构变量的一行是：
```c
struct book library;
```
​	编译器执行这行代码便创建了一个结构变量 library。编译器使用 book 模板为该变量分配空间：一个内含MAXTITL 个元素的 char 数组、一个内含 MAXAUTL 个元素的 char 数组和一个 float 类型的变量。这些存储空间都与一个名称 library 结合在一起。

​	在结构变量的声明中，`struct book` 所起的作用相当于一般声明中的 int 或 float 。例如，可以定义两个 `struct book` 类型的变量，或者甚至是指向 `struct book` 类型结构的指针：
```c
struct book doyle, panshin, * ptbook;
```
​	结构变量 doyle 和 panshin 中都包含 title、author 和 value 部分。指针 ptbook 可以指向 doyle、panshin 或任何其他 book 类型的结构变量。从本质上看，book 结构声明创建了一个名为 `struct book` 的新类型。

​	就计算机而言，下面的声明：
```c
struct book library;
```
​	是以下声明的简化：
```c
struct book {
  char title[MAXTITL]; 
  char author[AXAUTL]; 
  float value;
} library; /*声明的右花括号后跟变量名*/
```
​	换言之，声明结构的过程和定义结构变量的过程可以组合成一个步骤。如下所示，组合后的结构声明和结构变量定义不需要使用结构标记：
```c
struct {/*无结构标记*/
  char title[MAXTITL];
  char author[MAXAUTL]; 
  float value;
} library;
```
​	然而，如果打算多次使用结构模板，就要使用带标记的形式；或者，使用本章后面介绍的 typedef。

​	这是定义结构变量的一个方面，在这个例子中，并未初始化结构变量。

####14.3.1 初始化结构 442 

​	初始化一个结构变量（ANSI 之前，不能用自动变量初始化结构；ANSI 之后可以用任意存储类别）与初始化数组的语法类似：
```c
struct book library = {
  "The Pious Pirate and the Devious Damsel",
  "Renee Vivotte",
  1.95
};
```
>#####注意   初始化结构和类别储存期
>
>​	第 12 章中提到过，如果初始化静态存储期的变量（如，静态外部链接、静态内部链接或静态无链接），必须使用常量值。这同样适用于结构。如果初始化一个静态存储期的结构，初始化列表中的值必须是常量表达式。如果是自动存储期，初始化列表中的值可以不是常量。
####14.3.2 访问结构成员 443 

​	使用结构成员运算符——点 `.` 访问结构中的成员。例如，`library.value` 即访问 `library` 的 `value` 

部分。可以像使用任何 `float` 类型变量那样使用 `library.value` 。

####14.3.3 结构的初始化器 443 

​	C99 和 C11 为结构提供了指定初始化器，其语法与数组的指定初始化器类似。但是，结构的指定初始化器使用点运算符和成员名（而不是方括号和下标）标识特定的元素。例如，只初始化 book 结构的 value 成员，可以这样做：
```c
struct book surprise = {.value = 10.99};
```
​	可以按照任意顺序使用指定初始化器：
```c
struct book gift = {
  .value = 25.99,
  .author = "James Broadfool",
  .title = "Rue for the Toad"
};
```
​	与数组类似，在指定初始化器后面的普通初始化器，为指定成员后面的成员提供初始值。另外，对特定成员的最后一次赋值才是它实际获得的值。例如，考虑下面的代码：
```c
struct book gift = {
  .value = 18.90,
  .author = "Philionna Pestle",
  0.25
};
```
​	赋给 value 的值是 0.25 ，因为它在结构声明中紧跟在 author 成员之后。新值 0.25 取代了之前的 18.9 。
###14.4 结构数组 444 

> #####结构和内存
>
> ​	manybook.c 程序创建了一个内含 100 个结构变量的数组。由于该数组是自动存储类别的对象，其中的信息被储存在栈（stack）中。如此大的数组需要很大一块内存，这可能会导致一些问题。如果在运行时出现错误，可能抱怨栈大小或栈溢出，你的编译器可能使用了一个默认大小的栈，这个栈对于该例而言太小。要修正这个问题，可以使用编译器选项设置栈大小为10000，以容纳这个结构数组；或者可以创建静态或外部数组（这样，编译器就不会把数组放在栈中）；或者可以减小数组大小为 16。为何不一开始就使用较小的数组？这是为了让读者意识到栈大小的潜在问题，以便今后再遇到类似的问题，可以自己处理好。

```c
/* manybook.c -- multiple book inventory */
#include <stdio.h>
#include <string.h>
char * s_gets(char * st, int n);
#define MAXTITL   40
#define MAXAUTL   40
#define MAXBKS   100              /* maximum number of books  */

struct book {                     /* set up book template     */
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};

int main(void)
{
    struct book library[MAXBKS]; /* array of book structures */
    int count = 0;
    int index;
    
    printf("Please enter the book title.\n");
    printf("Press [enter] at the start of a line to stop.\n");
    while (count < MAXBKS && s_gets(library[count].title, MAXTITL) != NULL
           && library[count].title[0] != '\0')
    {
        printf("Now enter the author.\n");
        s_gets(library[count].author, MAXAUTL);
        printf("Now enter the value.\n");
        scanf("%f", &library[count++].value);
        while (getchar() != '\n')
            continue;          /* clear input line         */
        if (count < MAXBKS)
            printf("Enter the next title.\n");
    }
    
    if (count > 0)
    {
        printf("Here is the list of your books:\n");
        for (index = 0; index < count; index++)
            printf("%s by %s: $%.2f\n", library[index].title,
                   library[index].author, library[index].value);
    }
    else
    	printf("No books? Too bad.\n");
    
    return 0;
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```

####14.4.1 声明结构数组 446 

​	声明结构数组和声明其他类型的数组类似。下面是一个声明结构数组的例子：

```c
struct book library[MAXBKS];
```

​	以上代码把 library 声明为一个内含 MAXBKS 个元素的数组。数组的每个元素都是一个 book 类型的数组。因此，`library[0]` 是第 1 个 book 类型的结构变量，`library[1]` 是第 2 个 book 类型的结构变量，以此类推。数组名 library 本身不是结构名，它是一个数组名，该数组中的每个元素都是 `struct book` 类型的结构变量。

####14.4.2 标识结构数组的成员 447 

​	为了标识结构数组中的成员，可以采用访问单独结构的规则：在结构名后面加一个点运算符，再在点运算符后面写上成员名。如下所示：

```c
library[0].value /*第1个数组元素与value相关联*/ 
library[4].title /*第5个数组元素与title相关联*/
```

​	注意，数组下标紧跟在 library 后面，不是成员名后面：

```c
library.value[2]	// 错误
library[2].value	// 正确
```

​	使用 `library[2].value` 的原因是：`library[2]` 是结构变量名，正如 `library[1]` 是另一个变量名。

​	顺带一提，下面的表达式代表什么?
```c
library[2].title[4]
```
​	这是 library 数组第 3 个结构变量（library[2]部分）中书名的第5个字符（title[4]部分）。 该例指出，点运算符右侧的下标作用于各个成员，点运算符左侧的下标作用于结构数组。

​	最后，总结一下：
```c
library				// 一个 book 结构的数组
library[2]			// 一个数组元素，该元素是 book 结构
library[2].title	// 一个 char 教组（library[2] 的 title 成员）
library[2].title[4]	// 数组中 library[2] 元素的 title 成员的一个字符
```


####14.4.3 程序讨论 447 
###14.5 嵌套结构 448 

```c
// friend.c -- example of a nested structure
#include <stdio.h>
#define LEN 20
const char * msgs[5] =
{
    "    Thank you for the wonderful evening, ",
    "You certainly prove that a ",
    "is a special kind of guy. We must get together",
    "over a delicious ",
    " and have a few laughs"
};

struct names {                     // first structure
    char first[LEN];
    char last[LEN];
};

struct guy {                       // second structure
    struct names handle;           // nested structure
    char favfood[LEN];
    char job[LEN];
    float income;
};

int main(void)
{
    struct guy fellow = {   // initialize a variable
        { "Ewen", "Villard" },
        "grilled salmon",
        "personality coach",
        68112.00
    };
    
    printf("Dear %s, \n\n", fellow.handle.first);
    printf("%s%s.\n", msgs[0], fellow.handle.first);
    printf("%s%s\n", msgs[1], fellow.job);
    printf("%s\n", msgs[2]);
    printf("%s%s%s", msgs[3], fellow.favfood, msgs[4]);
    if (fellow.income > 150000.0)
        puts("!!");
    else if (fellow.income > 75000.0)
        puts("!");
    else
        puts(".");
    printf("\n%40s%s\n", " ", "See you soon,");
    printf("%40s%s\n", " ", "Shalala");
    
    return 0;
}
```

​	首先，注意如何在结构声明中创建嵌套结构。和声明 int 类型变量一样，进行简单的声明：

```c
struct names handle;
```

​	该声明表明 handle 是一个 struct name 类型的变量。当然，文件中也应包含结构 names 的声明。

​	其次，注意如何访问嵌套结构的成员，这需要使用两次点运算符：

```c
printf("Hello, %s!\n", fellow.handle.first);
```

​	从左往右解释 `fellow.handle.first` ：

```c
(fellow.handle).first
```

​	也就是说，找到 fellow，然后找到 fellow 的 handle 的成员，再找到 handle 的 first 成员。

###14.6 指向结构的指针 449 

​	至少有 4 个理由可以解释为何要使用指向结构的指针。第一，就像指向数组的指针比数组本身更容易操控（如，排序问题）一样，指向结构的指针通常比结构本身更容易操控。第二，在一些早期的 C 实现中，结构不能作为参数传递给函数，但是可以传递指向结构的指针。第三，即使能传递一个结构，传递指针通常更有效率。第四，一些用于表示数据的结构中包含指向其他结构的指针。

```c
/* friends.c -- uses pointer to a structure */
#include <stdio.h>
#define LEN 20

struct names {
    char first[LEN];
    char last[LEN];
};

struct guy {
    struct names handle;
    char favfood[LEN];
    char job[LEN];
    float income;
};

int main(void)
{
    struct guy fellow[2] = {
        {{ "Ewen", "Villard"},
            "grilled salmon",
            "personality coach",
            68112.00
        },
        {{"Rodney", "Swillbelly"},
            "tripe",
            "tabloid editor",
            432400.00
        }
    };
    struct guy * him;    /* here is a pointer to a structure */
    
    printf("address #1: %p #2: %p\n", &fellow[0], &fellow[1]);
    him = &fellow[0];    /* tell the pointer where to point  */
    printf("pointer #1: %p #2: %p\n", him, him + 1);
    printf("him->income is $%.2f: (*him).income is $%.2f\n",
           him->income, (*him).income);
    him++;               /* point to the next structure      */
    printf("him->favfood is %s:  him->handle.last is %s\n",
           him->favfood, him->handle.last);
    
    return 0;
}
```

####14.6.1 声明和初始化结构指针 450 

​	声明结构指针很简单：

```c
struct guy * him;
```

​	首先是关键字 struct ，其次是结构标记 guy ，然后是一个星号 `*` ，其后跟着指针名。这个语法和其他指针声明一样。

​	该声明并未创建一个新的结构，但是指针 him 现在可以指向任意现有的 guy 类型的结构。例如，如果  barney 是一个 guy 类型的结构，可以这样写：

```c
him = &barney;
```

​	和数组不同的是，结构名并不是结构的地址，因此要在结构名前面加上 & 运算符。

​	在有些系统中，一个结构的大小可能大于它各成员大小之和。这是因为系统对数据进行校准的过程中产生了一些“缝隙”。例如，有些系统必须把每个成员都放在偶数地址上，或 4 的倍数的地址上。在这种系统中，结构的内部就存在未使用的“缝隙”。

####14.6.2 用指针访问成员 451 

​	第 1 种方法也是最常用的方法：使用 `->` 运算符。该运算符由一个连接号 `-` 后跟一个大于号 `>` 组成。我们有下面的关系：

> 如果 him == &barney，那么 him->income 即是 barney.income
>
> 如果 him == &fellow [0]，那么 him->income 即是 fellow[0].income

​	换句话说，`->` 运算符后面的结构指针和 `.` 运算符后面的结构名工作方式相同（不能写成 `him.incone` , 因为him不是结构名）。

​	这里要着重理解 him 是一个指针，但是 `him->income` 是该指针所指向结构的一个成员。所以在该例中，`him->income` 是一个 float 类型的变量。

​	第 2 种方法是，以这样的顺序指定结构成员的值：如果 `him == &fellow[0]` ，那么`*him == fellow[O]` ，因为 `&` 和 `*` 是一对互逆运算符。因此，可以做以下替代：

```c
fellow[0].income == (*him).income
```

​	必须要使用圆括号，因为 `.` 运算符比 `*` 运算符的优先级高。

​	总之，如果 him 是指向 guy 类型结构 barney 的指针，下面的关系恒成立：

```c
barney.income == (*him).income == him->income // 假设 him == &barney
```

###14.7 向函数传递结构的信息 451 
####14.7.1 传递结构成员 451 

```c
/* funds1.c -- passing structure members as arguments */
#include <stdio.h>
#define FUNDLEN 50

struct funds {
    char   bank[FUNDLEN];
    double bankfund;
    char   save[FUNDLEN];
    double savefund;
};

double sum(double, double);

int main(void)
{
    struct funds stan = {
        "Garlic-Melon Bank",
        4032.27,
        "Lucky's Savings and Loan",
        8543.94
    };
    
    printf("Stan has a total of $%.2f.\n",
           sum(stan.bankfund, stan.savefund) );
    return 0;
}

/* adds two double numbers */
double sum(double x, double y)
{
    return(x + y);
}
```

####14.7.2 传递结构的地址 452 

```c
/* funds2.c -- passing a pointer to a structure */
#include <stdio.h>
#define FUNDLEN 50

struct funds {
    char   bank[FUNDLEN];
    double bankfund;
    char   save[FUNDLEN];
    double savefund;
};

double sum(const struct funds *);  /* argument is a pointer */

int main(void)
{
    struct funds stan = {
        "Garlic-Melon Bank",
        4032.27,
        "Lucky's Savings and Loan",
        8543.94
    };
    
    printf("Stan has a total of $%.2f.\n", sum(&stan));
    
    return 0;
}

double sum(const struct funds * money)
{
    return(money->bankfund + money->savefund);
}
```

####14.7.3 传递结构 453 

```c
/* funds3.c -- passing a structure */
#include <stdio.h>
#define FUNDLEN 50

struct funds {
    char   bank[FUNDLEN];
    double bankfund;
    char   save[FUNDLEN];
    double savefund;
};

double sum(struct funds moolah);  /* argument is a structure */

int main(void)
{
    struct funds stan = {
        "Garlic-Melon Bank",
        4032.27,
        "Lucky's Savings and Loan",
        8543.94
    };
    
    printf("Stan has a total of $%.2f.\n", sum(stan));
    
    return 0;
}

double sum(struct funds moolah)
{
    return(moolah.bankfund + moolah.savefund);
}
```



####14.7.4 其他结构特性 454 

​	传递指针的方式处理结构

```c
/* names1.c -- uses pointers to a structure */
#include <stdio.h>
#include <string.h>

#define NLEN 30
struct namect {
    char fname[NLEN];
    char lname[NLEN];
    int letters;
};

void getinfo(struct namect *);
void makeinfo(struct namect *);
void showinfo(const struct namect *);
char * s_gets(char * st, int n);

int main(void)
{
    struct namect person;
    
    getinfo(&person);
    makeinfo(&person);
    showinfo(&person);
    return 0;
}

void getinfo (struct namect * pst)
{
    printf("Please enter your first name.\n");
    s_gets(pst->fname, NLEN);
    printf("Please enter your last name.\n");
    s_gets(pst->lname, NLEN);
}

void makeinfo (struct namect * pst)
{
    pst->letters = strlen(pst->fname) +
    strlen(pst->lname);
}

void showinfo (const struct namect * pst)
{
    printf("%s %s, your name contains %d letters.\n",
           pst->fname, pst->lname, pst->letters);
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```



​	传递结构和返回结构

```c
/* names2.c -- passes and returns structures */
#include <stdio.h>
#include <string.h>

#define NLEN 30
struct namect {
    char fname[NLEN];
    char lname[NLEN];
    int letters;
};

struct namect getinfo(void);
struct namect makeinfo(struct namect);
void showinfo(struct namect);
char * s_gets(char * st, int n);

int main(void)
{
    struct namect person;
    
    person = getinfo();
    person = makeinfo(person);
    showinfo(person);
    
    return 0;
}

struct namect getinfo(void)
{
    struct namect temp;
    printf("Please enter your first name.\n");
    s_gets(temp.fname, NLEN);
    printf("Please enter your last name.\n");
    s_gets(temp.lname, NLEN);
    
    return temp;
}

struct namect makeinfo(struct namect info)
{
    info.letters = strlen(info.fname) + strlen(info.lname);
    
    return info;
}

void showinfo(struct namect info)
{
    printf("%s %s, your name contains %d letters.\n",
           info.fname, info.lname, info.letters);
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```



####14.7.5 结构和结构指针的选择 458 

​	通常，程序员为了追求效率会使用结构指针作为函数参数，如需防止原始数据被意外修改，使用 const 限定符。按值传递结构是处理小型结构最常用的方法。

####14.7.6 结构中的字符数组和字符指针 458 
####14.7.7 结构、指针和malloc() 459 

​	如果使用malloc ( ) 分配内存并使用指针储存该地址，那么在结构中使用指针处理字符串就比较合理。

```c
// names3.c -- use pointers and malloc()
#include <stdio.h>
#include <string.h>   // for strcpy(), strlen()
#include <stdlib.h>   // for malloc(), free()
#define SLEN 81
struct namect {
    char * fname;  // using pointers
    char * lname;
    int letters;
};

void getinfo(struct namect *);        // allocates memory
void makeinfo(struct namect *);
void showinfo(const struct namect *);
void cleanup(struct namect *);        // free memory when done
char * s_gets(char * st, int n);

int main(void)
{
    struct namect person;
    
    getinfo(&person);
    makeinfo(&person);
    showinfo(&person);
    cleanup(&person);
    
    return 0;
}

void getinfo (struct namect * pst)
{
    char temp[SLEN];
    printf("Please enter your first name.\n");
    s_gets(temp, SLEN);
    // allocate memory to hold name
    pst->fname = (char *) malloc(strlen(temp) + 1);
    // copy name to allocated memory
    strcpy(pst->fname, temp);
    printf("Please enter your last name.\n");
    s_gets(temp, SLEN);
    pst->lname = (char *) malloc(strlen(temp) + 1);
    strcpy(pst->lname, temp);
}

void makeinfo (struct namect * pst)
{
    pst->letters = strlen(pst->fname) +
    strlen(pst->lname);
}

void showinfo (const struct namect * pst)
{
    printf("%s %s, your name contains %d letters.\n",
           pst->fname, pst->lname, pst->letters);
}

void cleanup(struct namect * pst)
{
    free(pst->fname);
    free(pst->lname);
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```



####14.7.8 复合字面量和结构（C99） 462 

​	下面是 `struct book` 类型的复合字面量：

```c
(struct book) {"The Idiot", "Fyodor Dostoyevsky", 6.99}
```

​	示例：

```c
/* complit.c -- compound literals */
#include <stdio.h>
#define MAXTITL  41
#define MAXAUTL  31

struct book {          // structure template: tag is book
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};

int main(void)
{
    struct book readfirst;
    int score;
    
    printf("Enter test score: ");
    scanf("%d",&score);
    
    if(score >= 84)
        readfirst = (struct book) {"Crime and Punishment",
            "Fyodor Dostoyevsky",
            11.25};
    else
        readfirst = (struct book) {"Mr. Bouncy's Nice Hat",
            "Fred Winsome",
            5.99};
    printf("Your assigned reading:\n");
    printf("%s by %s: $%.2f\n",readfirst.title,
           readfirst.author, readfirst.value);
    
    return 0;
}
```

​	还可以把复合字而量作为函数的参数。如果函数接受一个结构，可以把复合字面量作为实际参数传递：

```c
struct rect {double x; double y;};
double rect_area(struct rect r) {return r.x * r.y; }
...
double area;
area = rect_area( (struct rect) {10.5, 20.0});
```

​	值 210 被赋给 area 。

​	如果函数接受一个地址，可以传递复合字面量的地址：

```c
struct rect {double x; double y;};
double rect_areap(struct rect * rp){return rp->x * rp->y;}
...
double area;
area = rect_areap( &(struct rect) {10.5, 20.0});
```

​	值 210 被赋给 area 。

​	复合字面量在所有函数的外部，具有静态存储期；如果复合字面量在块中，则具有自动存储期。复合字面量和普通初始化列表的语法规则相冋。这意味着，可以在复合字面量中使用指定初始化器。

####14.7.9 伸缩型数组成员（C99） 463 

​	C99新增了一个特性：**伸缩型数组成员**，利用这项特性声明的结构，其最后一个数组成员具有一些特性。第 1 个特性是，该数组不会立即存在。第 2 个特性是，使用这个伸缩型数组成员可以编写合适的代码，就好像它确实存在并具有所需数目的元素一样。

​	首先，声明一个伸缩型数组成员有如下规则：

- 伸缩型数绀成员必须是结构的最后一个成员；
- 结构中必须至少有一个成员：
- 伸缩数组的声明类似于普通数组，只是它的方括号中是空的。

下面用一个示例来解释以上几点：

```c
struct flex {
  int count; 
  double average;
  double scores [];    //伸缩型教组成员
};
```

​	声明一个 `struct flex` 类型的结构变量时，不能用 scores 做任何事，因为没有给这个数组预留存储空间。实际上，C99 的意图并不是让你声明 `struct flex` 类型的变量，而是希望你声明一个指向 `struct flex` 类型的指针，然后用 malloc ( ) 来分配足够的空间，以储存 `struct flex` 类型结构的常规内容和伸缩型数组成员所需的额外空间。例如，假设用 scores 表示一个内含5个 double 类型值的数组，可以这样做：

```c
struct flex * pf; // 声明一个指针 
//请求为一个结构和一个数组分配存储空间
pf = malloc(sizeof(struct flex) + 5 * sizeof(double));
```

​	现在有足够的存储空间储存 count、average 和一个内含 5 个 double 类型值的数组。可以用指针 pf 访问这些成员：

```c
pf->count = 5;			// 设置 count 成员
pf->scores[2] = 18.5;	// 访问数组成员的一个元素
```

​	下面的程序进一步扩展了这个例子，让伸缩型数组成员在第 1 种情况下表示 5 个值，在第 2 种情况下代表 9 个值。该程序也演示了如何编写一个函数处理带伸缩型数组元素的结构。

```c
// flexmemb.c -- flexible array member (C99 feature)
#include <stdio.h>
#include <stdlib.h>

struct flex
{
    size_t count;
    double average;
    double scores[];   // flexible array member
};

void showFlex(const struct flex * p);

int main(void)
{
    struct flex * pf1, *pf2;
    int n = 5;
    int i;
    int tot = 0;
    
    // allocate space for structure plus array
    pf1 = malloc(sizeof(struct flex) + n * sizeof(double));
    pf1->count = n;
    for (i = 0; i < n; i++)
    {
        pf1->scores[i] = 20.0 - i;
        tot += pf1->scores[i];
    }
    pf1->average = tot / n;
    showFlex(pf1);
    
    n = 9;
    tot = 0;
    pf2 = malloc(sizeof(struct flex) + n * sizeof(double));
    pf2->count = n;
    for (i = 0; i < n; i++)
    {
        pf2->scores[i] = 20.0 - i/2.0;
        tot += pf2->scores[i];
    }
    pf2->average = tot / n;
    showFlex(pf2);
    free(pf1);
    free(pf2);
    
    return 0;
}

void showFlex(const struct flex * p)
{
    int i;
    printf("Scores : ");
    for (i = 0; i < p->count; i++)
        printf("%g ", p->scores[i]);
    printf("\nAverage: %g\n", p->average);
}
```

​	带伸缩型数组成员的结构确实有一些特殊的处理要求。第一，不能用结构进行赋值或拷贝:

```c
struct flex * pf1 pf2;	// *pf1 和 pf2 都是结构
...
*pf2 = *pfl;			//不要这样做
```

​	这样做只能拷贝除伸缩型数组成员以外的其他成员。确实要进行拷贝，应使用 memcpy ( ) 函数（第 16 章中介绍）。

​	第二，不要以按值方式把这种结构传递给结构。原因相同，按值传递一个参数与赋值类似。要把结构的地址传递给函数。

​	第三，不要使用带伸缩型数组成员的结构作为数组成员或另一个结构的成员。

​	这种类似于在结构中最后一个成员是伸缩型数组的情况，称为 struct hack。除了伸缩型数组成员在声明时用空的方括号外，struct hack 特指大小为0的数组。然而，struct hack 是针对特殊编译器（GCC）的，不属于 C 标准。这种伸缩型数组成员方法是标准认可的编程技巧。

####14.7.10 匿名结构（C11） 465 

​	匿名结构是一个没有名称的结构成员。为了理解它的工作原理，我们先考虑如何创建嵌套结构：

```c
struct names {
  char first[20];
  char last[20];
};
struct person {
  int id;
  struct names name;// 嵌套结构成员
};
struct person ted = {8483, {"Ted", "Grass"}};
```

​	这里，name 成员是一个嵌套结构，可以通过类似 `ted.name. first` 的表达式访问 "ted"：

```c
puts(ted.name.first);
```

​	在 C11 中，可以用嵌套的匿名成员结构定义 person：

```c
struct person {
  int id;
  struct {char first[20]; char last [20];};// 匿名结构
};
```

​	初始化 ted 的方式相同:

```c
struct person ted = {8483, {"Ted", "Grass"}};
```

​	但是，在访问 ted 时简化了步骤，只需把 first 看作是 person 的成员那样使用它：

```c
puts(ted.first);
```

​	当然，也可以把 first 和 last 直接作为 person 的成员，删除嵌套循环。匿名特性在嵌套联合中更加有用，我们在本章后面介绍。

####14.7.11 使用结构数组的函数 466 

​	假设一个函数要处理一个结构数组。由于数组名就是该数组的地址，所以可以把它传递给函数。另外, 该函数还需访问结构模板。

```c
/* funds4.c -- passing an array of structures to a function */
#include <stdio.h>
#define FUNDLEN 50
#define N 2

struct funds {
    char   bank[FUNDLEN];
    double bankfund;
    char   save[FUNDLEN];
    double savefund;
};

double sum(const struct funds money[], int n);

int main(void)
{
    struct funds jones[N] = {
        {
            "Garlic-Melon Bank",
            4032.27,
            "Lucky's Savings and Loan",
            8543.94

        },
        {
            "Honest Jack's Bank",
            3620.88,
            "Party Time Savings",
            3802.91
        }
    };
    
    printf("The Joneses have a total of $%.2f.\n",
           sum(jones,N));
    
    return 0;
}

double sum(const struct funds money[], int n)
{
    double total;
    int i;
    
    for (i = 0, total = 0; i < n; i++)
        total += money[i].bankfund + money[i].savefund;
    
    return(total);
}
```

​	程序中数组名 jones 是该数组的地址，即该数组首元素（jones[0]）的地址。因此，指针 money 的初始值相当于通过下面的表达式获得：

```c
money = &jones[0];
```

​	因为 money 指向 jones 数组的首元素，所以 money[0] 是该数组的另一个名称。与此类似，money[1] 是第2 个元素。每个元素都是一个 funds 类型的结构，所以都可以使用点运算符 `.` 来访问 funds 类型结构的成员。

​	下面是几个要点。

- 可以把数组名作为数组中第 1 个结构的地址传递给函数。

- 然后可以用数组表示法访问数组中的其他结构。注意下面的函数调用与使用数组名效果相同：

  ```c
  sum(&jones[0], N)
  ```

  因为 jones 和 &jones[0] 的地址相同，使用数组名是传递结构地址的一种间接的方法。

- 由于 sum ( ) 函数不能改变原始数据，所以该函数使用了 ANSI C 的限定符 const 。

###14.8 把结构内容保存到文件中 467 

​	使用 fprintf()

```c
fprintf(pbooks, "%s %s %.2f\n", primer.title, primer.author, primer.value);
```

​	对于一些结构（如，有30个成员的结构），这个方法用起来很不方便。另外，在检索时还存在问题，因为程序要知道一个字段结束和另一个字段开始的位置。虽然用固定字段宽度的格式可以解决这个问题（例 如，"％39s%39s%8.2f"），但是这个方法仍然很笨拙。

​	更好的方案是使用 fread ( ) 和 fwrite ( ) 函数读写结构大小的单元。

```c
fwrite(&primer, sizeof(struct book), 1, pbooks);
```

​	定位到 primer 结构变量开始的位置，并把结构中所有的字节都拷贝到与 pbooks 相关的文件中。 `sizeof (struct book)` 告诉函数待拷贝的一块数据的大小，1 表明一次拷贝一块数据。带相同参数的 fread ( ) 函数从文件中拷贝一块结构大小的数据到 &primer 指向的位置。简而言之，这两个函数一次读写整个记录，而不是一个字段。

​	以二进制表示法储存数据的缺点是，不同的系统可能使用不同的二进制表示法，所以数据文件可能不具可移植性。甚至同一个系统，不同编译器设置也可能导致不同的二进制布局。

####14.8.1 保存结构的程序示例 468 

```c
/* booksave.c -- saves structure contents in a file */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAXTITL  40
#define MAXAUTL  40
#define MAXBKS   10             /* maximum number of books */
char * s_gets(char * st, int n);
struct book {                   /* set up book template    */
    char title[MAXTITL];
    char author[MAXAUTL];
    float value;
};

int main(void)
{
    struct book library[MAXBKS]; /* array of structures     */
    int count = 0;
    int index, filecount;
    FILE * pbooks;
    int size = sizeof (struct book);
    
    if ((pbooks = fopen("book.dat", "a+b")) == NULL)
    {
        fputs("Can't open book.dat file\n",stderr);
        exit(1);
    }
    
    rewind(pbooks);            /* go to start of file     */
    while (count < MAXBKS &&  fread(&library[count], size,
                                    1, pbooks) == 1)
    {
        if (count == 0)
            puts("Current contents of book.dat:");
        printf("%s by %s: $%.2f\n",library[count].title,
               library[count].author, library[count].value);
        count++;
    }
    filecount = count;
    if (count == MAXBKS)
    {
        fputs("The book.dat file is full.", stderr);
        exit(2);
    }
    
    puts("Please add new book titles.");
    puts("Press [enter] at the start of a line to stop.");
    while (count < MAXBKS && s_gets(library[count].title, MAXTITL) != NULL
           && library[count].title[0] != '\0')
    {
        puts("Now enter the author.");
        s_gets(library[count].author, MAXAUTL);
        puts("Now enter the value.");
        scanf("%f", &library[count++].value);
        while (getchar() != '\n')
            continue;                /* clear input line  */
        if (count < MAXBKS)
            puts("Enter the next title.");
    }
    
    if (count > 0)
    {
        puts("Here is the list of your books:");
        for (index = 0; index < count; index++)
            printf("%s by %s: $%.2f\n",library[index].title,
                   library[index].author, library[index].value);
        fwrite(&library[filecount], size, count - filecount,
               pbooks);
    }
    else
    	puts("No books? Too bad.\n");
    
    puts("Bye.\n");
    fclose(pbooks);
    
    return 0;
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```



####14.8.2 程序要点 470 



###14.9 链式结构 471 



###14.10 联合简介 472 

​	联合（union），也称共用体，是一种数据类型，它能在同一个内存空间中储存不同的数据类型（不是同时储存）。其典型的用法是，设计一种表以储存既无规律、事先也不知道顺序的混合类型。使用联合类型的数组，其中的联合都大小相等，每个联合可以储存各种数据类型。

​	创建联合和创建结构的方式相同，需要一个联合模板和联合变量。可以用一个步骤定义联合，也可以用联合标记分两步定义。下面是一个带标记的联合模板：

```c
union hold { 
  int digit; 
  double bigfl; 
  char letter;
};
```

​	根据以上形式声明的结构可以储存一个 int 类型、一个 double 类型和 char 类型的值。然而，声明的联合只能储存一个 int 类型的值或一个 double 类型的值或 char 类型的值。

下面定义了 3 个与 hold 类型相关的变量：

```c
union hold fit;			// hold类型的联合变量
union hold save [10];	// 内含10个联合变量的教组
union hold * pu;		// 指向hold类型联合变量的指针
```

​	第 1 个声明创建了一个单独的联合变量 fit。编译器分配足够的空间以便它能储存联合声明中占用最大字节的类型。在本例中，占用空间最大的是 double 类型的数据。在我们的系统中，double 类型占 64 位，即 8 字节。第 2 个声明创建了一个数组 save，内含 10 个元素，每个元素都是 8 字节。第 3 个声明创建了一个指针，该指针变量储存 hold 类型联合变量的地址。

​	可以初始化联合。需要注意的是，联合只能储存一个值，这与结构不同。有 3 种初始化的方法：把一个联合初始化为另一个同类型的联合；初始化联合的第1个元素；或者根据C99标准，使用指定初始化器:

```c
union hold valA; 
valA.letter = 'R' ;
union hold valB = valA;				// 用另一个联合来初始化
union hold valC = {88};				// 初始化联合的 digit 成员
union hold valD = {.bigfl = 118.2};	// 指定初始化器
```



####14.10.1 使用联合 472 

​	下面是联合的一些用法：

```c
fit.digit = 23;		// 把 23 储存在 fit，占 2 字节
fit.bigfl = 2.0;	// 清除 23，储存 2.0，占 8 字节
fit.letter = 'h';	// 清除 2.0，储存 h，占 1 字节
```

​	点运算符表示正在使用哪种数据类型。在联合中，一次只储存一个值。即使有足够的空间，也不能同时储存一个char类型值和一个int类型值。编写代码时要注意当前储存在联合中的数据类型。

​	和用指针访问结构使用 `->` 运算符一样，用指针访问联合时也要使用 `->` 运算符：

```c
pu = &fit;
x = pu->digit;	// 相当于 x = fit. digit
```

​	不要像下面的语句序列这样：

```c
fit.letter = 'A';
flnum = 3.02*fit.bigfl;	// 错误
```

​	以上语句序列是错误的，因为储存在 fit 中的是 char 类型，但是下一行却假定 fit 中的内容是 double 类型。

​	不过，用一个成员把值储存在一个联合中，然后用另一个成员査看内容，这种做法有时很有用。下一章的程序清单 15.4 就给出了一个这样的例子。

​	联合的另一种用法是，在结构中储存与其成员有从属关系的信息。例如，假设用一个结构表示一辆汽车。如果汽车属于驾驶者，就要用一个结构成员来描述这个所有者。如果汽车被租赁，那么需要一个成员来描述其租赁公司。可以用下面的代码来完成：

```c
struct owner {
  char socsecurity[12];
  ...
};

struct leasecompany { 
  char name[40]; 
  char headquarters[40];
  ...
};

union data {
  struct owner owncar;
  struct leasecompany leasecar;
};

struct car_data { 
  char make[15];
  int status; /* 私有为 0，租赁为 1 */ 
  union data ownerinfo;
  ...
};
```

​	假设 flits 是 car_data 类型的结构变量，如果 flits.status 为 0，程序将使用 flits.ownerinfo.owncar. socsecurity，如果 flits.status 为 1，程序则使用 flits.ownerinfo.leasecar.name。

####14.10.2 匿名联合（C11） 473 

​	匿名联合和匿名结构的工作原理相同，即匿名联合是一个结构或联合的无名联合成员。例如，我们重新定义car_data 结构如下：

```c
struct owner {
  char socsecurity[12];
  ...
};

struct leasecompany { 
  char name[40]; 
  char headquarters[40];
  ...
};

struct car_data { 
  char make[15];
  int status; /* 私有为 0，租赁为 1 */ 
  union {
    struct owner owncar;
    struct leasecompany leasecar;
  };
  ...
};
```

​	现在，如果 flits 是 car_data 类型的结构变量，可以用 flits.owncar.socsecurity 代替 flits.ownerinfo.owncar.socsecurity。



> ###### 总结：结构和联合运算符
>
> 成员运算符：`.`
>
> 一般注释：
>
> 该运算符与结构或联合名一起使用，指定结构或联合的一个成员。如果 name 是一个结构的名称，member 是该结构模版指定的一个成员名，下面标识了该结构的这个成员：
>
> name.member
>
> name.member 的类型就是 member 的类型。联合使用成员运算符的方式与结构相同。
>
> 示例：
>
> ```c
> struct {
>   int code; 
>   float cost;
> } item;
> item.code = 1265;
> ```
>
> 间接成员运算符：`->`
>
> 一般注释：
>
> 该运算符和指向结构或联合的指针一起使用，标识结构或联合的一个成员。假设 ptrstr 是指向结构的指针，member 是该结构模版指定的一个成员，那么：
>
> ptrstr->member
>
> 标识了指向结构的成员。联合使用间接成员运算符的方式与结构相同 
>
> 示例：
>
> ```c
> struct {
>   int code; 
>   float cost;
> } item, * ptrst;
> ptrst = &item; 
> ptrst->code = 3451;
> ```
>
> 最后一条语句把一个 int 类型的值赋给 item 的 code 成员。如下 3 个表达式是等价的：
>
> ptrst->code    item.code    (*ptrst).code

###14.11 枚举类型 474 

​	可以用枚举类型（enumerated type）声明符号名称来表示整型常量。使用 enum 关键字，可以创建一个新“类型”并指定它可具有的值（实际上，enum 常量是 int 类型，因此，只要能使用 int 类型的地方就可以使用枚举类型）。枚举类型的目的是提高程序的可读性。它的语法与结构的语法相同。例如，可以这样声明：

```c
enum spectrum {red, orange, yellow, green, blue, violet}; 
enum spectrum color;
```

​	第 1 个声明创建了 spetrum 作为标记名，允许把 enum spetrum 作为一个类型名使用。第 2 个声明使 color 作为该类型的变量。第 1 个声明中花括号内的标识符枚举了 spectrum 变量可能有的值。因此，color 可能的值是red、orange、yellow 等。这些符号常量被称为枚举符（enumerator）。然后，便可这样用：

```c
int c;
color = blue;
if (color == yellow)
	...;
for (color = red; color <= violet; color++)
	...;
```

​	虽然枚举符（如 red 和 blue）是 int 类型，但是枚举变量可以是任意整数类型，前提是该整数类型可以储存枚举常量。例如，spectrum 的枚举符范围是 0〜5，所以编译器可以用 unsigned char 来表示 color 变量。

​	顺带一提，C 枚举的一些特性并不适用于 C++。例如，C 允许枚举变量使用运算符，但是 C++ 标准不允许。所以，如果编写的代码将来会并入 C++ 程序，那么必须把上面例子中的 color 声明为 int 类型, 才能 C 和 C++ 都兼容。

####14.11.1 enum常量 475 

​	blue 和 red 到底是什么？从技术层面看，它们是 int 类型的常量。例如，假定有前面的枚举声明， 可以这样写：

```c
printf ("red = %d, orange = %d\n", red, orange);
```

其输出如下：

red = 0, orange = 1

​	red 成为一个有名称的常量，代表整数 0。类似地，其他标识符都是有名称的常量，分别代表 1〜5。 只要是能使用整型常量的地方就可以使用枚举常量。例如，在声明数组时，可以用枚举常量表示数组的大小；在 switch 语句中，可以把枚举常量作为标签。

####14.11.2 默认值 475 

​	默认情况下，枚举列表中的常量都被赋予 0、1、2 等。因此，下面的声明中 nina 的值是 3：

```c
enum kids {nippy, slats, skippy, nina, liz};
```

####14.11.3 赋值 475 

​	在枚举声明中，可以为枚举常量指定整数值：

```c
enum levels {low = 100, medium = 500, high = 2000};
```

​	如果只给一个枚举常量赋值，没有对后面的枚举常量赋值，那么后面的常量会被赋予后续的值。例如, 假设有如下的声明：

```c
enum feline {cat, lynx = 10, puma, tiger};
```

​	那么，cat的值是 0（默认），lynx、puma 和 tiger 的值分别是10、11、12。

####14.11.4 enum的用法 476 

​	程序清单 14.15 enum.c 程序

```c
/* enum.c -- uses enumerated values */
#include <stdio.h>
#include <string.h>    // for strcmp(), strchr()
#include <stdbool.h>   // C99 feature
char * s_gets(char * st, int n);

enum spectrum {red, orange, yellow, green, blue, violet};
const char * colors[] = {"red", "orange", "yellow",
    "green", "blue", "violet"};
#define LEN 30

int main(void)
{
    char choice[LEN];
    enum spectrum color;
    bool color_is_found = false;
    
    puts("Enter a color (empty line to quit):");
    while (s_gets(choice, LEN) != NULL && choice[0] != '\0')
    {
        for (color = red; color <= violet; color++)
        {
            if (strcmp(choice, colors[color]) == 0)
            {
                color_is_found = true;
                break;
            }
        }
        if (color_is_found)
            switch(color)
        {
            case red    : puts("Roses are red.");
                break;
            case orange : puts("Poppies are orange.");
                break;
            case yellow : puts("Sunflowers are yellow.");
                break;
            case green  : puts("Grass is green.");
                break;
            case blue   : puts("Bluebells are blue.");
                break;
            case violet : puts("Violets are violet.");
                break;
        }
        else
            printf("I don't know about the color %s.\n", choice);
        color_is_found = false;
        puts("Next color, please (empty line to quit):");
    }
    puts("Goodbye!");
    
    return 0;
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;
    
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```



####14.11.5 共享名称空间 477 

​	C 语言使用名称空间（namespace）标识程序中的各部分，即通过名称来识别。作用域是名称空间概念的一部分：两个不同作用域的同名变量不冲突；两个相同作用域的同名变量冲突。名称空间是分类别的。在特定作用域中的结构标记、联合标记和枚举标记都共享相同的名称空间，该名称空间与普通变量使用的空间不同。这意味着在相同作用域中变量和标记的名称可以相同，不会引起冲突，但是不能在相同作用域中声明两个同名标签或同名变量。例如，在 C 中，下面的代码不会产生冲突：

```c
struct rect { double x; double y; }; 
int rect; // 在 C 中不会产生冲突
```

​	尽管如此，以两种不同的方式使用相同的标识符会造成混乱。另外，C++ 不允许这样做，因为它把标记名和变量名放在相同的名称空间中。

###14.12 typedef简介 478 

​	typedef 工具是一个高级数据特性，利用 typedef 可以为某一类型自定义名称。这方面与 #define 类似，但是两者有 3 处不同：

- 与 #define 不同，typedef 创建的符号名只受限于类型，不能用于值。

- typedef 由编译器解释，不是预处理器。

- 在其受限范围内，typedef 比 #define 更灵活。

  ​下面介绍 typedef 的工作原理。假设要用 BYTE 表示 1 字节的数组。只需像定义个 char 类型变量一样定义BYTE，然后在定义前面加上关键字 typedef 即可：

```c
typedef unsigned char BYTE;
```

​	随后，便可使用 BYTE 来定义变量：

```c
BYTE x, y[10], * z;
```

​	该定义的作用域取决于 typedef 定义所在的位置。如果定义在函数中，就具有局部作用域，受限于定义所在的函数。如果定义在函数外面，就具有文件作用域。

​	通常，typedef 定义中用大写字母表示被定义的名称，以提醒用户这个类型名实际上是一个符号缩写。 当然，也可以用小写：

```c
typedef unsigned char byte;
```

​	typedef 中使用的名称遵循变量的命名规则。

​	为现有类型创建一个名称，看上去真是多此一举，但是它有时的确很有用。在前面的示例中，用 BYTE 代替unsigned char 表明你打算用 BYTE 类型的变量表示数字，而不是字符码。使用 typedef 还能提高程序的可移植性。例如，我们之前提到的 sizeof 运算符的返回类型：size_t 类型，以及 time ( ) 函数的返回类型：time_t 类型。C 标准规定 sizeof 和 time ( ) 返回整数类型，但是让实现来决定具体是什么整数类型。其原因是，C 标准委员会认为没有哪个类型对于所有的计算机平台都是最优选择。所以，标准委员会决定建立一个新的类型名（如，time_t），并让实现使用 typedef 来设置它的具体类型。以这样的 方式，C标准提供以下通用原型：

```c
time_t time(time_t *);
```

​	time_t 在一个系统中是 unsigned long ，在另一个系统中可以是 unsigned long long 。只要包含 time.h 头文件，程序就能访问合适的定义，你也可以在代码中声明类型的变量。

​	typedef 的一些特性与 #define 的功能重合。例如：

```c
#define BYTE unsigned char
```

​	这使预处理器用 BYTE 替换 unsigned char。但是也有 #define 没有的功能：

```c
typedef char * STRING;
```

​	没有 typedef 关键字，编译器将把 STRING 识别为一个指向 char 的指针变量。有了 typedef 关键字，编译器则把 STRING 解释成一个类型的标识符，该类型是指向 char 的指针。因此：

```c
STRING name, sign;
```

​	相当于：

```c
char * name, * sign;
```

​	但是，如果这样假设：

```c
#define STRING char *
```

​	然后，下面的声明：

```c
STRING name, sign;
```

​	将被翻译成：

```c
char * name, sign;
```

​	这导致只有 name 才是指针。

​	还可以把 typedef 用于结构：

```c
typedef struct complex { 
  float real; 
  float imag;
} COMPLEX;
```

​	然后便可使用 COMPLEX 类型代替 complex 结构来表示复数。使用 typedef 的第 1 个原因是：为经常出现的类型创建一个方便、易识别的类型名。例如，前面的例子中，许多人更倾向于使用 STRING 或与其等价的标记。

​	用 typedef 来命名一个结构类型时，可以省略该结构的标签：

```c
typedef struct {double x; double y;} rect;
```

​	假设这样使用 typedef 定义的类型名：

```c
rect rl = {3.0, 6.0}; 
rect r2;
```

​	以上代码将被翻译成：

```c
struct {double x; double y;} r1= {3.0, 6.0}; 
struct {double x; double y;} r2; 
r2 = rl;
```

​	这两个结构在声明时都没有标记，它们的成员完全相同（成员名及其类型都匹配），C 认为这两个结构的类型相同，所以 r1 和 r2 间的赋值是有效操作。

​	使用 typedef 的第 2 个原因是：typedef 常用于给复杂的类型命名。例如，下面的声明：

```c
typedef char (* FRPTC ()) [5];
```

​	把 FRPTC 声明为一个函数类型，该函数返回一个指针，该指针指向内含 5 个 char 类型元素的数组（参见下一节的讨论）。

​	使用 typedef 时要记住，typedef 并没有创建任何新类型，它只是为某个已存在的类型增加了一个方便使用的标签。以前面的 STRING 为例，这意味着我们创建的 STRING 类型变量可以作为实参传递给以指向 char 指针作为形参的函数。

​	通过结构、联合和 typedef，C 提供了有效处理数据的工具和处理可移植数据的工具。

###14.13 其他复杂的声明 479 

​	C 允许用户自定义数据形式。虽然我们常用的是一些简单的形式，但是根据需要有时还会用到一些复杂的形式。在一些复杂的声明中，常包含下面的符号，如表 14.1 所示：

> 表14.1声明时可使用的符号

| 符号   | 含义       |
| ---- | -------- |
| *    | 表示一个指针 * |
| ( )  | 表示—个函数   |
| [ ]  | 表示一个数组   |

​	下面是一些较复杂的声明示例:

```c
int board[8][8];	//声明一个内含 int 数组的数组
int ** ptr;			//声明一个指向指针的指针，被指向的指针指向 int
int * risks[10];	//声明一个内含 10 个元素的数组，每个元素都是一个指向 int 的指针
int (* rusks)[10];	//声明一个指向数组的指针，该数组内含 10 个 int 类型的值
int * oof[3][4];	//声明一个 3 × 4 的二维教组，每个元素都是指向 int 的指针
int (* oof)[3][4];	//声明一个指向 3 × 4 二维数组的指针，该数组中内含 int 类型值
int (* oof[3])[4];	//声明一个内含 3 个指针元素的数组，其中每个指针都指向一个内含 4 个 int 类型元素的数组
```

​	要看懂以上声明，关键要理解 `*` 、 `()` 和 `[]` 的优先级。记住下面几条规则。

1. 数组名后面的 `[]` 和函数名后面的 `()` 具有相同的优先级。它们比 `*` （解引用运算符）的优先级高。因此下面声明的 risk 是一个指针数组，不是指向数组的指针：

```c
int * risks[10];
```

2. `[]` 和 `()` 的优先级相同，由于都是从左往右结合，所以下面的声明中，在应用方括号之前，`*` 先与 rusks  结合。因此 rusks 是一个指向数组的指针，该数组内含 10 个 int 类型的元素：
```c
int (* rusks)[10];
```
3. `[]` 和 `()` 都是从左往右结合。因此下面声明的 goods 是一个由 12 个内含 50 个 int 类型值的数组组成的二维数组，不是一个有50个内含12个int类型值的数组组成的二维数组：

```c
int goods[12][50];
```

​	把以上规则应用于下面的声明：

```c
int * oof[3][4];
```

​		`[3]` 比 `*` 的优先级高，由于从左往右结合，所以 `[3]` 先与 oof 结合。因此，oof 首先是一个内含 3 个元素的数组。然后再与 [4] 结合，所以 oof 的每个元素都是内含 4 个元素的数组。`*` 说明这些元素都是指针。 最后，int 表明了这 4 个元素都是指向 int 的指针。因此，这条声明要表达的是：oof 是一个内含 3 个元素的数组，其中每个元素是由 4 个指向 int 的指针组成的数组。简而言之，oof 是一个 3 × 4 的二维数组，每个元素都是指向 int 的指针。编译器要为 12 个指针预留存储空间。

​	现在来看下面的声明：
```c
int (* uuf)[3][4];
```
​	圆括号使得 `*` 先与 uuf 结合，说明 uuf 是一个指针，所以 uuf 是一个指向 3  × 4 的 int 类型二维数组的指针。编译器要为一个指针预留存储空间。

​	根据这些规则，还可以声明：
```c
char * fump(int);		// 返回字符指针的函数
char (* frump)(int);	// 指向函数的指针，该函数的返回类型为char
char (* flump[3])(int);	// 内含3个指针的数组，每个指针都指向返回类型为char的函数
```
​	这 3 个函数都接受 int 类型的参数。

​	可以使用 typedef 建立一系列相关类型：
```c
typedef int arr5[5]; 
typedef arr5 * p_arr5;
typedef p_arr5 arrplO[10];
arr5 togs;	// togs 是一个内含 5 个 int 类型值的数组
p_arr5 p2;	// p2 是一个指向数组的指针，该数组内含 5 个 int 类型的值
arrplO ap;	// ap 是一个内含 10 个指针的教组，每个指针都指向一个内含 5 个 int 类型值的数组
```
如果把这些放入结构中，声明会更复杂。至于应用，我们就不再进一步讨论了。

###14.14 函数和指针 481 

​	通过上一节的学习可知，可以声明一个指向函数的指针。这个复杂的玩意儿到底有何用处？通常，函数指针常用作另一个函数的参数，告诉该函数要使用哪一个函数。例如，排序数组涉及比较两个元素，以确定先后。如果元素是数字，可以使用 > 运算符；如果元素是字符串或结构，就要调用函数进行比较。C 库中的 qsort ( ) 函数可以处理任意类型的数组，但是要告诉 qsort ( ) 使用哪个函数来比较元素。为此，qsort ( ) 函数的参数列表中，有一个参数接受指向函数的指针。然后，qsort ( ) 函数使用该函数提供的方案进行排序，无论这个数组中的元素是整数、字符串还是结构。

​	我们来进一步研究函数指针。首先，什么是函数指针？假设有一个指向 int 类型变量的指针，该指针储存着这个 int 类型变量储存在内存位置的地址。同样，函数也有地址，因为函数的机器语言实现由载入内存的代码组成。指向函数的指针中储存着函数代码的起始处的地址。

​	其次，声明一个数据指针时，必须声明指针所指向的数据类型。声明一个函数指针时，必须声明指针指向的函数类型。为了指明函数类型，要指明函数签名，即函数的返回类型和形参类型。例如，考虑下面的函数原型：

```c
void ToUpper(char *);	// 把字符串中的字符转换成大写字符
```

​	ToUpper ( ) 函数的类型是“带 char * 类型参数、返回类型是 void 的函数”。下面声明了一个指针 pf 指向该函数类型：

```c
void (*pf)(char *);		// pf是一个指向函数的指针
```

​	从该声明可以看出，第 1 对圆括号把 `*` 和 pf 括起来，表明 pf 是一个指向函数的指针。因此，`(*pf)` 是一个参数列表为(`char *`)、返回类型为 void 的函数。注意，把函数名 ToUpper 替换为表达式 `(*pf)` 是创建指向函数指针最简单的方式。所以，==如果想声明一个指向某类型函数的指针，可以写出该函数的原型后把函数名替换成`(*pf)` 形式的表达式，创建函数指针声明。==前面提到过，由于运算符优先级的规则，在声明函数指针时必须把`*` 和指针名括起来。如果省略第 1 个圆括号会导致完全不同的情况：

```c
void *pf(char *);		// pf是一个返回字符指针的函数
```

> #####提示
>
> ​	要声明一个指向特定类型函数的指针，可以先声明一个该类型的函数，然后把函数名替换成 `(*pf)`  形式的表达式。然后，pf 就成为指向该类型函数的指针。

​	声明了函数指针后，可以把类型匹配的函数地址赋给它。在这种上下文中，==函数名可以用于表示函数的地址==：

```c
void ToUpper(char *);
void ToLower(char *;
int round(double);        
void (*pf)(char *);        
pf = ToUpper;		// 有效，ToUpper 是该类型函数的地址
pf = ToLower;		// 有效，ToLower 是该类型函数的地址
pf = round;			// 无效，round 与指针类型不匹配
pf = ToLower();		// 无效，ToLower ( ) 不是地址
```


​	最后一条语句是无效的，不仅因为 ToLower ( ) 不是地址，而且 ToLower ( ) 的返回类型是 void，它没有返回值，不能在赋值语句中进行赋值。注意，指针 pf 可以指向其他带 char * 类型参数、返回类型是 void 的函数，不能指向其他类型的函数。

​	既然可以用数据指针访问数据，也可以用函数指针访问函数。奇怪的是，有两种逻辑上不一致的语法可以这样做，下面解释：

```c
void ToUpper(char *); 
void ToLower(char *); 
void (pf)(char *);
char mis[] = "Nina Metier"; 
pf = ToUpper;
(*pf)(mis);		// 把 ToUpper 作用于（语法 1 ）
pf = ToLower;
pf(mis);		// 把 ToLower 作用于（语法 2）
```

​	这两种方法看上去都合情合理。先分析第 1 种方法：由于 pf 指向 ToUpper 函数，那么 `*pf` 就相当于  ToUpper 函数，所以表达式 `(*pf) (mis)` 和 `ToUpper(mis)` 相同。从 ToUpper 函数和 pf 的声明就能看出， ToUpper 和 `(*pf)` 是等价的。第 2 种方法：由于函数名是指针，那么指针和函数名可以互换使用，所以 `pf (mis)` 和 `ToUpper(mis)` 相同。从 pf 的赋值表达式语句就能看出 ToUpper 和 pf 是等价的。由于历史的原因，贝尔实验室的 C 和 UNIX 的开发者采用第 1 种形式，而伯克利的 UNIX 推广者却采用第 2 种形式。K&R C 不允许第 2 种形式。但是，为了与现有代码兼容，ANSI C 认为这两种形式（本例中是 `(*pf)(mis)` 和 `pf(mis)` ）等价。后续的标准也延续了这种矛盾的和谐。

​	作为函数的参数是数据指针最常见的用法之一，函数指针亦如此。例如，考虑下面的函数原型：

```c
void show (void (* fp)(char *) ,char * str);
```

​	这看上去让人头晕。它声明了两个形参：fp 和 str。fp 形参是一个函数指针，str 是一个数据指针。更具体地说，fp 指向的函数接受 char * 类型的参数，其返回类型为 void；str 指向一个 char 类型的值。因此，假设有上面的声明，可以这样调用函数：

```c
show(ToLower, mis);		/* show ( ) 使用 ToLower ( ) 函数：fp = ToLower */
show(pf, mis);			/* show ( ) 使用 pf 指向的函数：fp = pf */
```
​	show ( ) 如何使用传入的函数指针？是用 fp( ) 语法还是 (*fp)( ) 语法调用函数：
```c
void show (void (* fp)(char *), char * str)
{
  (*fp)(str);	/* 把所选函数作用于str */
  fp(str);		/* 也可以这样调用 */
  puts(str);	/* 显示结果 */
}
```

​	例如，这里的 show( ) 首先用 fp 指向的函数转换 str，然后显示转换后的字符串。

​	顺带一提，把带返回值的函数作为参数传递给另一个函数有两种不同的方法。例如，考虑下面的语句：

```c
function1(sqrt);		/* 传递 sqrt() 函数的地址*/
function2(sqrt(4.0));	/* 传递 sqrt() 函教的返回值 */
```

​	第 1 条语句传递的是 sqrt( ) 函数的地址，假设 function1( ) 在其代码中会使用该函数。第 2 条语句先调用 sqrt( ) 函数，然后求值，并把返回值（该例中是 2.0）传递给 function2( ) 。

​	程序清单 14.16 中的程序通过 show( ) 函数来演示这些要点，该函数以各种转换函数作为参数。该程序也演示了一些处理菜单的有用技巧。

> 程序清单14.16 func_ptr.c 程序

```c
// func_ptr.c -- uses function pointers
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define LEN 81
char * s_gets(char * st, int n);
char showmenu(void);
void eatline(void);     // read through end of line
void show(void (* fp)(char *), char * str);
void ToUpper(char *);   // convert string to uppercase
void ToLower(char *);   // convert string to uppercase
void Transpose(char *); // transpose cases
void Dummy(char *);     // leave string unaltered

int main(void)
{
    char line[LEN];
    char copy[LEN];
    char choice;
    void (*pfun)(char *); // points a function having a
    // char * argument and no
    // return value
    puts("Enter a string (empty line to quit):");
    while (s_gets(line, LEN) != NULL && line[0] != '\0')
    {
        while ((choice = showmenu()) != 'n')
        {
            switch (choice)  // switch sets pointer
            {
                case 'u' : pfun = ToUpper;   break;
                case 'l' : pfun = ToLower;   break;
                case 't' : pfun = Transpose; break;
                case 'o' : pfun = Dummy;     break;
            }
            strcpy(copy, line);// make copy for show()
            show(pfun, copy);  // use selected function
        }
        puts("Enter a string (empty line to quit):");
    }
    puts("Bye!");

    return 0;
}

char showmenu(void)
{
    char ans;
    puts("Enter menu choice:");
    puts("u) uppercase       l) lowercase");
    puts("t) transposed case o) original case");
    puts("n) next string");
    ans = getchar();    // get response
    ans = tolower(ans); // convert to lowercase
    eatline();          // dispose of rest of line
    while (strchr("ulton", ans) == NULL)
    {
        puts("Please enter a u, l, t, o, or n:");
        ans = tolower(getchar());
        eatline();
    }

    return ans;
}

void eatline(void)
{
    while (getchar() != '\n')
        continue;
}

void ToUpper(char * str)
{
    while (*str)
    {
        *str = toupper(*str);
        str++;
    }
}

void ToLower(char * str)
{
    while (*str)
    {
        *str = tolower(*str);
        str++;
    }
}
void Transpose(char * str)
{
    while (*str)
    {
        if (islower(*str))
            *str = toupper(*str);
        else if (isupper(*str))
            *str = tolower(*str);
        str++;
    }
}

void Dummy(char * str)
{
    // leaves string unchanged
}

void show(void (* fp)(char *), char * str)
{
    (*fp)(str); // apply chosen function to str
//    fp(str);
    puts(str);  // display result
}

char * s_gets(char * st, int n)
{
    char * ret_val;
    char * find;

    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        find = strchr(st, '\n');   // look for newline
        if (find)                  // if the address is not NULL,
            *find = '\0';          // place a null character there
        else
            while (getchar() != '\n')
                continue;          // dispose of rest of line
    }
    return ret_val;
}
```

​	注意，ToUpper( ) 、ToLower( ) 、Transpose( ) 和 Dummy( ) 函数的类型都相同，所以这 4 个函数都可以赋给 pfun 指针。该程序把 pfun 作为 show( ) 的参数，但是也可以直接把这 4 个函数中的任一个函数名作为参数，如 `show(Transpose, copy) ` 。

​	这种情况下，可以使用 typedef。例如，该程序中可以这样写：

```c
typedef void (*V_FP_CHARP)(char *); 
void show(V_FP_CHARP fp, char *);
V_FP_CHARP pfun;
```

​	如果还想更复杂一些，可以声明并初始化一个函数指针的数组：

```c
V_FP_CHARP arpf[4] = {ToUpper, ToLower, Transpose, Dummy};
```

​	然后把showmenu( ) 函数的返回类型改为 int ，如果用户输入 u，则返回 0；如果用户输入 1，则返回 2；如果用户输入 t，则返回 2，以此类推。可以把程序中的 switch 语句替换成下面的 while 循环：

```c
index = showmenu();
while (index >= 0 && index <= 3)
{
  strcpy (copy, line);			/* 为 show( ) 拷贝一份 */
  show (arpf[index], copy);		/* 使用选定的函数 */
  index = showmenu();
}
```

​	==虽然没有函数数组，但是可以有函数指针数组。==

​	以上介绍了使用函数名的4种方法：定义函数、声明函数、调用函数和作为指针。下表进行了总结：

|               函数名 | 代码                            |
| ----------------: | :---------------------------- |
|         函数原型中的函数名 | `int comp(int x, int y);`     |
|         函数调用中的函数名 | `status = comp(q, r);`        |
|         函数定义中的函数名 | `int comp(int x, int y){...}` |
| 在赋值表达式语句中作为指针的函数名 | `pfunct = comp`               |
|        作为指针参数的函数名 | `slowsort(arr, n, comp);`     |



###14.15 关键概念 487 

​	我们在编程中要表示的信息通常不只是一个数字或一些列数字。程序可能要处理具有多种属性的实体。 例如，通过姓名、地址、电话号码和其他信息表示一名客户；或者，通过电影名、发行人、播放时长、售价等表示一部电影 DVD。C 结构可以把这些信息都放在一个单元内。在组织程序时这很重要，因为这样可以把相关的信息都储存在一处，而不是分散储存在多个变量中。

​	设计结构时，开发一个与之配套的函数包通常很有用。例如，写一个以结构（或结构的地址）为参数的函数打印结构内容，比用一堆 printf( ) 语句强得多。因为只需要一个参数就能打印结构中的所有信息。如果把信息放到零散的变量中，每个部分都需要一个参数。另外，如果要在结构中增加一个成员，只需重写函数，不必改写函数调用。这在修改结构时很方便。

​	联合声明与结构声明类似。但是，联合的成员共享相同的存储空间，而且在联合中同一时间内只能有一个成员。实质上，可以在联合变量中储存一个类型不唯一的值。

​	enum 工具提供一种定义符号常量的方法，typedef 工具提供一种为基本或派生类型创建新标识符的方法。

​	指向函数的指针提供一种告诉函数应使用哪一个函数的方法。

###14.16 本章小结 487 

​	C 结构提供在相同的数据对象中储存多个不同类型数据项的方法。可以使用标记来标识一个具体的结构模板，并声明该类型的变量。通过成员点运算符（.）可以使用结构模版中的标签来访问结构的各个成员。

​	如果有一个指向结构的指针，可以用该指针和间接成员运算符（->）代替结构名和点运算符来访问结构的各成员。和数组不同，结构名不是结构的地址，要在结构名前使用 & 运算符才能获得结构的地址。

​	一贯以来，与结构相关的函数都使用指向结构的指针作为参数。现在的 C 允许把结构作为参数传递，作为返回值和同类型结构之间赋值。然而，传递结构的地址通常更有效。

​	联合使用与结构相同的语法。然而，联合的成员共享一个共同的存储空间。联合同一时间内只能储存一个单独的数据项，不像结构那样同时储存多种数据类型。也就是说，结构可以同时储存一个 int 类型数据、一个 double 类型数据和一个 char 类型数据，而相应的联合只能保存一个 int 类型数据，或者一个 double 类型数据，或者一个 char 类型数据。

​	通过枚举可以创建一系列代表整型常量（枚举常量）的符号和定义相关联的枚举类型。 typedef 工具可用于建立 C 标准类型的别名或缩写。

​	函数名代表函数的地址，可以把函数的地址作为参数传递给其他函数，然后这些函数就可以使用被指向的函数。如果把特定函数的地址赋给一个名为 pf 的函数指针，可以通过以下两种方式调用该函数：

```c
#include <math.h> /* 提供 sin() 函教的原型：double sin(double) */
double (*pdf)(double);
double x;
pdf = sin;
x = (*pdf)(1.2);	// 调用 sin(1.2)
x = pdf(1.2);		// 同样调用 sin(1.2)
```

###14.17 复习题 488 
###14.18 编程练习 490 
##第15章　位操作 493 
###15.1 二进制数、位和字节 493 
####15.1.1 二进制整数 494 
####15.1.2 有符号整数 494 
####15.1.3 二进制浮点数 495 
###15.2 其他进制数 495 
####15.2.1 八进制 495 
####15.2.2 十六进制 496 
###15.3 C按位运算符 496 
####15.3.1 按位逻辑运算符 497 
####15.3.2 用法：掩码 498 
####15.3.3 用法：打开位（设置位） 498 
####15.3.4 用法：关闭位（清空位） 499 
####15.3.5 用法：切换位 499 
####15.3.6 用法：检查位的值 500 
####15.3.7 移位运算符 500 
####15.3.8 编程示例 501 
####15.3.9 另一个例子 503 
###15.4 位字段 505 
####15.4.1 位字段示例 506 
####15.4.2 位字段和按位运算符 509 
###15.5 对齐特性（C11） 515 

​	C11 的对齐特性比用位填充字节更自然，它们还代表了 C 在处理硬件相关问题上的能力。在这种上下文中，对齐指的是如何安排对象在内存中的位置。例如，为了效率最大化，系统可能要把一个 double 类型的值储存在 4 字节内存地址上，但却允许把 char 储存在任意地址。大部分程序员都对对齐不以为然。但是，有些情况又受益于对齐控制。例如，把数据从一个硬件位置转移到另一个位置，或者调用指令同时操作多个数据项。

​	`_Alignof` 运算符给出一个类型的对齐要求，在关键字 `_Alignof` 后面的圆括号中写上类型名即可：

```c
size_t d_align = _Alignof(float);
```

​	假设 d_align 的值是 4 ，意思是 float 类型对象的对齐要求是 4。也就是说，4 是储存该类型值相邻地址的字节数。一般而言，对齐值都应该是 2 的非负整数次幕。较大的对齐值被称为 stricter 或 stronger，较小的对齐值被称为 weaker。

​	可以使 `_Alignas` 说明符指定一个变量或类型的对齐值。但是，不应该要求该值小于基本对齐值。例如，如果 float 类型的对齐要求是 4 ，不要请求其对齐值是 1 或 2 。该说明符用作声明的一部分，说明符后面的圆括号内包含对齐值或类型：

```c
_Alignas(double) char c1;
_Alignas(8) char c2;
unsigned char _Alignas(long double) c_arr[sizeof(long double)];
```

> #####注意
>
> ​	撰写本书时，Clang（ 3.2版本）要求 `_Alignas(type)` 说明符在类型说明符后面，如上面第 3 行代码所示。但是，无论 `_Alignas(type)` 说明符在类型说明符的前面还是后面，GCC 4.7.3 都能识别，后来 Clang 3.3 版本也支持了这两种顺序。

​	程序清单 15.5 中的程序演示了 `_Alignas` 和 `_Alignof` 的用法。

> 程序清单15.5 align.c 程序

```c
//  align.c -- using _Alignof and _Alignas  (C11)

#include <stdio.h>
int main(void)
{
    double dx;
    char ca;
    char cx;
    double dz;
    char cb;
    char _Alignas(double)  cz;
   
    printf("char alignment:   %zd\n", _Alignof(char));
    printf("double alignment: %zd\n", _Alignof(double));
    printf("&dx: %p\n", &dx);
    printf("&ca: %p\n", &ca);
    printf("&cx: %p\n", &cx);
    printf("&dz: %p\n", &dz);
    printf("&cb: %p\n", &cb);
    printf("&cz: %p\n", &cz);
    
    return 0;
}
```

该程序的输出如下：

```C
char alignment:   1
double alignment: 8
&dx: 0x7ffee18964e0
&ca: 0x7ffee18964df
&cx: 0x7ffee18964de
&dz: 0x7ffee18964d0
&cb: 0x7ffee18964cf
&cz: 0x7ffee18964c8
```

​	在我们的系统中，double 的对齐值是 8，这意味着地址的类型对齐可以被 8 整除。以 0 或 8 结尾的十六进制地址可被 8 整除。这就是地址常用两个 double 类型的变量和 char 类型的变量 cz（该变量是 double 对齐值）。因为 char 的对齐值是 1，对于普通的 char 类型变量，编译器可以使用任何地址。

​	在程序中包含 stdalign.h 头文件后，就可以把 alignas 和 alignof 分别作为 _Alignas 和 _Alignof 的别名。这样做可以与 C++ 关键字匹配。

​	C11 在 stdlib.h 库还添加了一个新的内存分配函数，用于对齐动态分配的内存。该函数的原型如下：

```c
void *aligned_alloc(size_t alignment, size_t size);
```

​	第 1 个参数代表指定的对齐，第 2 个参数是所需的字节数，其值应是第 1 个参数的倍数。与其他内存分配函数一样，要使用 free( ) 函数释放之前分配的内存。

###15.6 关键概念 516 

​	C 区别于许多高级语言的特性之一是访问整数中单独位的能力。该特性通常是与硬件设备和操作系统交互的关键。

​	C 有两种访问位的方法。一种方法是通过按位运算符，另一种方法是在结构中创建位字段。

​	C11 新增了检查内存对齐要求的功能，而且可以指定比基本对齐值更大的对齐值。

​	通常（但不总是），使用这些特性的程序仅限于特定的硬件平台或操作系统，而且设计为不可移植的。

###15.7 本章小结 516 

​	计算硬件与二进制记数系统密不可分，因为二进制数的 1 和 0 可用于表示计算机内存和寄存器中位的开闭状态。虽然 C 不允许以二进制形式书写数字，但是它识别与二进制相关的八进制和十六进制记数法。正如每个二进制数字表示 1 位一样，每个八进制位代表 3 位，每个十六进制位代表 4 位。这种关系使得二进制转为八进制或十六进制较为简单。

​	C 提供多种按位运算符，之所以称为按位是因为它们单独操作一个值中的每个位。`〜` 运算符将其运算对象的每一位`取反`，将 1 转为 0 ，0 转为 1 。按位`与`运算符 `&` 通过两个运算对象形成一个值。如果两运算对象中相同号位都为 1 ，那么该值中对应的位为 1；否则，该位为 0 。按位`或`运算符 `|` 同样通过两个运算对象形成一个值。如果两运算对象中相同号位有一个为 1 或都为 1 ，那么该值中对应的位为 1；否则，该位为 0 。按位`异或`运算符 `^` 也有类似的操作，只有两运算对象中相同号位有一个为 1 时，结果值中对应的位才为 1 。

​	C 还有左移（<<）和右移（>>）运算符。这两个运算符使位组合中的所有位都向左或向右移动指定数量的位，以形成一个新值。对于左移运算符，空出的位置设为 0。对于右移运算符，如果是无符号类型的值，空出的位设为 0；如果是有符号类型的值，右移运算符的行为取决于实现。

​	可以在结构中使用位字段操控一个值中的单独位或多组位。具体细节因实现而异。

​	可以使用 _Alignas 强制执行数据存储区上的对齐要求。

​	这些位工具帮助 C 程序处理硬件问题，因此它们通常用于依赖实现的场合中。

###15.8 复习题 517 
###15.9 编程练习 518 
##第16章　C预处理器和C库 521 
###16.1 翻译程序的第一步 521 
###16.2 明示常量：#define 522 
####16.2.1 记号 525 
####16.2.2 重定义常量 525 
###16.3 在#define中使用参数 525 
####16.3.1 用宏参数创建字符串：#运算符 527 
####16.3.2 预处理器黏合剂：##运算符 528 
####16.3.3 变参宏：...和_ _VA_ARGS_ _ 529 
###16.4 宏和函数的选择 530 
###16.5 文件包含：#include 531 
####16.5.1 头文件示例 531 
####16.5.2 使用头文件 533 
###16.6 其他指令 534 
####16.6.1 #undef指令 534 
####16.6.2 从C预处理器角度看已定义 534 
####16.6.3 条件编译 535 
####16.6.4 预定义宏 539 
####16.6.5 #line和#error 540 
####16.6.6 #pragma 540 
####16.6.7 泛型选择（C11） 541 
###16.7 内联函数（C99） 542 
###16.8 _Noreturn函数（C11） 544 
###16.9 C库 544 
####16.9.1 访问C库 544 
####16.9.2 使用库描述 545 
###16.10 数学库 546 
####16.10.1 三角问题 547 
####16.10.2 类型变体 548 
####16.10.3 tgmath.h库（C99） 550 
###16.11 通用工具库 550 
####16.11.1 exit()和atexit()函数 550 
####16.11.2 qsort()函数 552 
###16.12 断言库 556 
####16.12.1 assert的用法 556 
####16.12.2 _Static_assert（C11） 557 
###16.13 string.h库中的memcpy()和memmove() 558 
###16.14 可变参数：stdarg.h 560 
###16.15 关键概念 562 
###16.16 本章小结 562 
###16.17 复习题 562 
###16.18 编程练习 563 
##第17章　高级数据表示 567 
###17.1 研究数据表示 567 
###17.2 从数组到链表 570 
####17.2.1 使用链表 572 
####17.2.2 反思 576 
###17.3 抽象数据类型（ADT） 576 
####17.3.1 建立抽象 577 
####17.3.2 建立接口 578 
####17.3.3 使用接口 581 
####17.3.4 实现接口 583 
###17.4 队列ADT 589 
####17.4.1 定义队列抽象数据类型 590 
####17.4.2 定义一个接口 590 
####17.4.3 实现接口数据表示 591 
####17.4.4 测试队列 598 
###17.5 用队列进行模拟 600 
###17.6 链表和数组 605 
###17.7 二叉查找树 608 
####17.7.1 二叉树ADT 608 
####17.7.2 二叉查找树接口 609 
####17.7.3 二叉树的实现 611 
####17.7.4 使用二叉树 624 
####17.7.5 树的思想 628 
###17.8 其他说明 629 
###17.9 关键概念 630 
###17.10 本章小结 630 
###17.11 复习题 630 
###17.12 编程练习 631 
##附录A　复习题答案 633
##附录B　参考资料 665
##B.1 参考资料I：补充阅读 665
##B.2 参考资料II：C运算符 667
##B.3 参考资料III：基本类型和存储类别 671
##B.4 参考资料IV：表达式、语句和程序流 675
##B.5 参考资料V：新增C99和C11的ANSI C库 679
##B.6 参考资料VI：扩展的整数类型 714
##B.7 参考资料VII：扩展字符支持 716
##B.8 参考资料VIII：C99/C11数值计算增强 720
##B.9 参考资料IX：C和C++的区别 726
