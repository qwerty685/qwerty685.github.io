---
sort: 2
---

# Linux 常用命令介绍

现在的许多工作需要在服务器上完成，所以经常需要使用到Linux命令行工具。尽管之前学习过《Linux操作系统》这门课程，由于之前使用次数不多，大多指令都不太熟。因此打算记录一下常用指令以及用法，方便以后查询。



## Screen

`screen`指令是Linux在命令行场景下的重要工具，主要的功能包括一下三个：

+ *会话恢复*：支持从当前会话中退出以及再次登陆会话的功能。这个场景用于执行耗时很长的任务，我们能够方便地将任务挂载在后台，并随时查看执行情况。
+ *多窗口*：支持同时创建多个会话并按照横或者纵列进行会话排列。
+ *会话共享*：支持其他用户登陆当前会话。同时支持会话的密码保护。

###  常用参数：

> -A 　将所有的视窗都调整为目前终端机的大小。
> -d <作业名称> 　将指定的screen作业离线。
> -h <行数> 　指定视窗的缓冲区行数。
> -m 　即使目前已在作业中的screen作业，仍强制建立新的screen作业。
> -r <作业名称> 　恢复离线的screen作业。
> -R 　先试图恢复离线的作业。若找不到离线的作业，即建立新的screen作业。
> -s 　指定建立新视窗时，所要执行的shell。
> -S <作业名称> 　指定screen作业的名称。
> -v 　显示版本信息。
> -x 　恢复之前离线的screen作业。
> -ls或--list 　显示目前所有的screen作业。
> -wipe 　检查目前所有的screen作业，并删除已经无法使用的screen作业。

### 常见用法

```
# 创建名称为task的会话
screen -S <task>
# 查看当前所有会话
screen -ls
# 返回（重连）task会话
screen -r <task>
# 远程关闭task会话
screen -d <task>
```

### 操作指令

screen指令支持在会话中进行某些操作（Ctrl+a X），下面是具体的操作以及使用方法：

```
C-a ? -> 显示所有键绑定信息
C-a c -> 创建一个新的运行shell的窗口并切换到该窗口
C-a n -> Next，切换到下一个 window 
C-a p -> Previous，切换到前一个 window 
C-a 0..9 -> 切换到第 0..9 个 window
Ctrl+a [Space] -> 由视窗0循序切换到视窗9
C-a C-a -> 在两个最近使用的 window 间切换 
C-a x -> 锁住当前的 window，需用用户密码解锁
C-a d -> detach，暂时离开当前session，将目前的 screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里，每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。 
C-a z -> 把当前session放到后台执行，用 shell 的 fg 命令则可回去。
C-a w -> 显示所有窗口列表
C-a t -> Time，显示当前时间，和系统的 load 
C-a k -> kill window，强行关闭当前的 window
```



