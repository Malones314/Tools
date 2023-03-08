# 常用gcc/g++ 命令
```makefile
-ansi: 只支持 ANSI 标准的 C 语法

-E : 只激活预处理,这个不生成文件，需要把它重定向到一个输出文件里面

-S : 只激活预处理和编译，把文件编译成为汇编代码,编辑器打开就都是汇编指令

-C ：只激活预处理,编译,和汇编，不做连接

-o file：制定输出文件为file  

-Wall： 输出所有编译警告
-w : 不生成任何警告信息。
-Wextra
-pedantic 打开更多警告。

-shared：生成一个共享库文件 
    g++ -shared -o libtest.so test.o  

-fPIC：生成位置无关目标代码，适用于动态连接。

-g：产生调试信息  

-O0 、-O1 、-O2 、-O3：优化级别，-O0 没有优化, -O1 为默认值，-O3 优化级别最高

-static : 禁止使用动态库

-share : 尽量使用动态库，所以生成文件比较小，但是需要系统由动态库。

-traditional : 让编译器支持传统的C语言特性

-M：生成文件关联的信息 gcc -M codename.c

```
# makefile编写规则

```makefile
targets : prerequisites ; command
    command
如果command和“targets : prerequisites”一行，则必须用;间隔开，如果不在一行，则
必须用Tab键开头，如果命令太长可以用\作为换行符
```

main.c调用test1.c和test2.c的函数
```makefile

test: main.o test1.o test2.o 
    gcc test1.o test2.o -o test

main.o : main.c
    gcc main.c -c -g -Wall -o main.o
test1.o: test1.c
    gcc test1.c -c -g -Wall -o test1.o
test2.0: test2.c
    gcc test1.c -c -g -Wall -o test2.o

clean:
    rm *.o test -rf

```

```makefile
OBJS = main.o test1.o test2.o
CC = gcc    #CC默认就是gcc，也可以改成别的编译器
CFLAGS += -c -g -Wall  # += : 在原来的基础上再加上

test : $(OBJS)
    $(CC) $(OBJS) -o test
main.o : main.c
    $(CC) main.c $(CFLAGS) -o main.o
test1.o: test1.c
    $(CC) test1.c $(CFLAGS) -o test1.o
test2.0: test2.c
    $(CC) test1.c $(CFLAGS) -o test2.o
clean:
    RM *.o test -r  #RM 默认为 rm - f
```
```makefile
OBJS = main.o test1.o test2.o
CC = gcc    #CC默认就是gcc，也可以改成别的编译器
CFLAGS += -c -g -Wall  # += : 在原来的基础上再加上

test : $(OBJS)
    $(CC) $^ -o $@    
        # ^:在上一句依赖关系中被依赖的所有的文件 @: 生成上一句中的目标文件
main.o : main.c
    $(CC) $^ $(CFLAGS) -o $@
test1.o: test1.c
    $(CC) $^ $(CFLAGS) -o $@
test2.0: test2.c
    $(CC) $^ $(CFLAGS) -o $@
clean:
    RM *.o test -r  #RM 默认为 rm - f
```

```makefile
OBJS = main.o test1.o test2.o
CC = gcc    #CC默认就是gcc，也可以改成别的编译器
CFLAGS += -c -g -Wall  # += : 在原来的基础上再加上

%.o:%.c     # %：通配符
    $(CC) $^ $(CFLAGS) -o $@

clean:
    RM *.o test -r  #RM 默认为 rm - f
```
**设置路径**
```makefile
VPATH = XXX 给出指定目录，如果不给定VPATH,make只会在当前目录搜索寻找依赖关系，
给定了后会去给定目录寻找依赖关系。

另一种设置文件搜索方式：vpath 关键字, <pattern>需要包含 % 字符
vpath <pattern> <directories>
为符合模式<pattern>的文件指定搜索目录<directories>。
vpath <pattern>
清除符合模式<pattern>的文件的搜索目录。
vpath
清除所有已被设置好了的文件搜索目录。
```
**伪目标**
```makefile
里面可以包含‘伪目标’(例如clean)通过make name调用伪目标,伪目标不能与目标文件同名,
“.PHONY”来显式地指明一个目标是“伪目标”，向make说明，不管是否有这个文件，这个目标
就是“伪目标”。‘伪目标’和‘目标’都可以成为依赖

eg:
.PHONY : clean
clean :
    ...........
```

# 杂记
```makefile
Makefile 和 makefile都可以存在，如果使用 make 时默认优先调用的是 makefile

缩进用的是tab键而不能用两个空格缩进

make会根据时间戳来判断是否需要重新编译

Makefile 中的变量其实就是 C/C++ 中的宏

```
