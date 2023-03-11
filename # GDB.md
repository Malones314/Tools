# 基本使用

1. 编译程序时添加-g参数，以便生成调试信息。
```
gcc -g -o prog prog.c
```
2. 启动gdb并加载要调试的程序
```
gdb prog
```
3. 设置断点
```
(gdb) break main
```
```
(gdb) break 文件名:行号
break main.cpp:6  //在main.cpp的第六行打断点
```
4. 使用条件断点
```
break main.cpp:20 if count == 10  //在程序执行到main.cpp文件的第20行时停止，但仅当count的值等于10时才停止
```
5. 运行程序
```
run
```
6. 当程序在断点处停止执行时，使用命令print可以查看变量的值
```
(gdb) print x
```
7. 查看内存
```
x/4x 0x1234 //查看内存地址0x1234中的4个字节的值
```
8. 修改变量的值
```
set [变量名]=[新值]
set count=10
```
9. 使用命令step可以单步执行程序
```
(gdb) step
```
10. 使用命令continue可以继续执行程序直到下一个断点
```
(gdb) continue
```
11. 使用命令backtrace可以查看函数调用栈
```
(gdb) backtrace
```
12. quit可以退出gdb
```
(gdb) quit
```
