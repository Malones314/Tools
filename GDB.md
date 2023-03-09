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
4. 运行程序
```
run
```
5. 当程序在断点处停止执行时，使用命令print可以查看变量的值
```
(gdb) print x
```
6. 使用命令step可以单步执行程序
```
(gdb) step
```
7. 使用命令continue可以继续执行程序直到下一个断点
```
(gdb) continue
```
8. 使用命令backtrace可以查看函数调用栈
```
(gdb) backtrace
```
9. quit可以退出gdb
```
(gdb) quit
```
