---
layout: default
title: 一个强大的linux命令screen
---
# {{ page.title }}
{{ page.date | date_to_string }}


  最近租了个服务器，想搭建一个自己的网站玩玩，决定用nodejs开发。应用搭建起来之后碰到了一个问题，因为服务器管理是ssh来的，我ssh连接上去运行自己的node应用一切正常了，但是当我断开ssh连接之后node应用也自动关闭掉了，这让老衲如何是好？？？

  找朋友咨询了一下，学到了一个有用的linux命令——screen
这个命令我们可以理解成在服务器里虚拟了一个进程作为一个窗口来运行我们的命令，即使ssh断开这个进程仍然会一直运行！
下面我们来看看这个命令怎么使用吧：）

  直接在命令行里面输入screen我们就可以创建一个窗口了，也可以输入screen -S 窗口名称 来创建一个自己命名的窗口；更简单的做法是screen node app.'s 直接用screen命令来运行我的node应用，就会进入一个窗口，显示我的node应用已经成功运行起来。这个时候ctrl+a 再按c就可以隐藏这个窗口，这个时候即使关闭ssh，我的应用仍然是运行的。

	运行命令screen -ls就可以查看服务器上存在的所有screen和其状态；
	运行命令screen -r screenId 就可以回复之前隐藏的screen窗口；


下面是screen的命令参数：

	-A 　将所有的视窗都调整为目前终端机的大小。
	-d <作业名称> 　将指定的screen作业离线。
	-h <行数> 　指定视窗的缓冲区行数。
	-m 　即使目前已在作业中的screen作业，仍强制建立新的screen作业。
	-r <作业名称> 　恢复离线的screen作业。
	-R 　先试图恢复离线的作业。若找不到离线的作业，即建立新的screen作业。
	-s 　指定建立新视窗时，所要执行的shell。
	-S <作业名称> 　指定screen作业的名称。
	-v 　显示版本信息。
	-x 　恢复之前离线的screen作业。
	-ls或--list 　显示目前所有的screen作业。
	-wipe 　检查目前所有的screen作业，并删除已经无法使用的screen作业。


下面是screen下的命令：

	C-a ? -> Help，显示简单说明
	C-a c -> Create，开启新的 window
	C-a n -> Next，切换到下个 window 
	C-a p -> Previous，前一个 window 
	C-a 0..9 -> 切换到第 0..9 个window
	Ctrl+a [Space] -> 由視窗0循序換到視窗9
	C-a C-a -> 在两个最近使用的 window 间切换 
	C-a x -> 锁住当前的 window，需用用户密码解锁
	C-a d -> detach，暂时离开当前session，将目前的 screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里    每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。 
	C-a z -> 把当前session放到后台执行，用 shell 的 fg 命令則可回去。
	C-a w -> Windows，列出已开启的 windows 有那些 
	C-a t -> Time，显示当前时间，和系统的 load 
	C-a K -> kill window，强行关闭当前的 window