#C Primer Plus Sixth Edition
http://catalogue.pearsoned.co.uk/educator/product/C-Primer-Plus-6E/9780321928429.page

##源码
https://github.com/szaydel/c-primer-plus-book-6ed

##习题答案
http://dlcenter.gotop.com.tw/SampleFiles/ACL040100/%E7%BF%92%E9%A1%8C%E8%A7%A3%E7%AD%94/9780321928429_ProgrammingExerciseAnswers_Selected.pdf

##用Mac终端编写、编译C程序的实例
步骤：创建C文件、用Vim编写C程序、编译C程序文件、执行编译后生成的.out文件。

说明：`$:`表示Mac终端

1. `$:`touch Hello.c                                          //创建一个Hello.c文件（本目录下）
2. `$:`vim Hello.c                                              //用vim编辑Hello.c文件

> i                                                                          //打开vim后先输入i进入编辑状态

以下为vim中输入的程序


```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```
> ESC键                                                                  //按ESC键退出编辑状态

> :wq                                                                      //先输入“:”，再输入“w”表示保存，最后输入“q”表示退出
3. `$:`gcc Hello.c 或 gcc Hello.c -o xxx            //编译Hello.c文件，会生成可执行文件"a.out"或"xxx"
4. `$:`./a.out 或 ./xxx                                         //执行a.out或xxx

### Mac中的一些编译器指令 

> cc 
```Bash
cc Hello.c
```

> gcc 
```Bash
gcc Hello.c
```

> clang 
```Bash
clang Hello.c
```

> llvm-gcc
```Bash
llvm-gcc Hello.c
```
