# shell
```shell
~ home目录
. 当前目录
.. 上一层目录
- 上一个目录(非上一层目录)
cd sys 访问内核

pipe： a|b  取a侧的输出作为b侧的输入

mv path1(old path) path2( new path) 重命名或移动文件
cp path1(old path) path2( new path) 复制文件
rm path 删除文件    不能删除目录
rmdir   删除目录( 只能删除空目录)
mkdir "Name"    创建名为Name的目录

man name    显示name的说明书
ctrl l terminal光标到顶部
clear 清空terminal，光标回到顶部

> fileName 输入流重定向到fileName文件中
< fileName fileName作为输入流( 默认的输入流为键盘)
> 为覆写，>>为追加
echo "characters" 在输出流输出characters
cat fileName 打印fileName的内容到输出流
cat fileName -n 打印fileName的内容到输出流并在前面加上行号
tee fileName 取输入流的东西覆盖放到fileName并输出到屏幕上

# xxx 整条语句都用root执行

xdg-open fileName 使用合适的软件打开fileName

sudo su 以super user身份运行下面的指令
exit 退出super user的模式



```