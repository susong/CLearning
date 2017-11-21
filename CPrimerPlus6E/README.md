#C Primer Plus, 6th Edition

[C Primer Plus, 6th Edition](http://www.informit.com/store/c-primer-plus-9780321928429)
[C Primer Plus, 6th Edition_code](http://www.informit.com/content/images/9780321928429/downloads/9780321928429_CPrimerPlus6E_code.zip)
[C Primer Plus, 6th Edition ProgrammingExerciseAnswers](http://www.informit.com/content/images/9780321928429/downloads/9780321928429_ProgrammingExerciseAnswers_Selected.pdf)



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
