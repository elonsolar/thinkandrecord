## <center>gdb调试golang</center>

### 1 前言

> 先前学习用gdb和ddd(gdb高级可视化）调试C 语言，今天偶然看到，gdb 可以调试golang 编译后的可执行文件，下面记录下初步的学习知识

### 2 使用方法

> 先学习命令行的方式，
>
> 1. 一是因为ddd 比较难安装（有点阴影了，先前花费了很长时间没搞定，最后是看了篇博客，基本上是照着操作了一遍，才安装好，博客地址记录以下（<https://blog.csdn.net/tong_xin2010/article/details/38641893>）
>
> 2. 二是需要gdb调试的程序，编译的时候需要加一些额外的参数，比如编译C 需要 -g（生成符号表。）而go 也要加一些参数，这些都必须是命令行完成的
>
>    

1. 进入到编译的目录  go build -gcflags “-N -l”   ***禁止编译的时候进行优化*** （但是生产环境不知道是否合适）
2. gdb xx(xx 为编译后的可执行程序）
3. l(list) 查看程序，方便进行打断点
4. b 18 ## 在18 行打断点
5. info breakpoints 查看所有断点 
6. d n (删除断点，n是指 第几个断点，可以通过 上面的指令查看序号)
7. run  ,运行程序，会停留在第一个断点
8. p x ,查看 变量x
9. set variable x=10 ,设置变量x 的值为10
10. n ,下一行
11. c  n跳到下一个断点，n指定跳过的断点数
12. ret 返回
13. info locals,info goroutines ( 暂时还没生效过)