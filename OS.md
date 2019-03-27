## Mac

首推当然还是MacOS，毕竟MS Office/QQ etc + Unix还是不错的。

没有Mac机器的情况下，[Hackintosh](https://hackintosh.com/)也是一种可能的选择。

+ <https://zhuanlan.zhihu.com/p/31556033>


## Linux

首推Arch Linux，用过绝对欲罢不能。用Arch很多人会推荐Manjaro，原因当然是Arch难装，然而我不推荐，因为Manjaro是基于Arch，而不是Arch，软件仓库是有区别的，有点像ubuntu和debian的感觉，而Arch拥有最多最新的软件。

事实上Arch是需要自己安装一遍的，因为在这个过程你会学到很多，并且如果你不能handle安装的话，Arch出问题，你也可能搞不定，所谓能力多大，责任多大，Arch给你自由，你也应该有相应的能力。

如果要先上手，我推荐[Antergos](https://antergos.com/)或者[Anarchy](https://anarchy-linux.org/)，因为它们就是原生的Arch，只不过是做了一个installer而已。


Linux必须要学，学Linux会让你打开新世界的大门，会让你对Mac和Windows都有不一样的看法，以及更好的用它们。
最主要的一点是comforatble to work in command line，请记住这一点，所以不要去玩Linux的桌面，不要去折腾这些。坚持使用一种桌面环境，不要不断去尝试不同的桌面，也不要去搞各种桌面配置。我推荐xfce（简单+可定制，用户友好）和i3wm（平铺，效率高）。

Linux怎么学？做为一个走了很多弯路的过来人，我推荐尝试在虚拟机中安装一次gentoo，甚至于lfs，一般Linux的安装和装windows没啥区别，反正是点下一步，会装系统跟不会装系统其实是同一level。你装gentoo或lfs，不看文档是不行的，在安装的过程中会强迫你去看官方的手册，而手册写得非常详细，安装过程可以让你了解Linux系统是由什么组件组合起来的，通过读手册你对linux会有比较清晰的认识。这也是为什么我推荐Arch的另一个原因，Arch同样手册很详细，比gentoo简单点，而且不用浪费时间在编译上，但做为学习gentoo更好，更折腾一点，让安装过程慢一点，对学习是极好的。

再者，学Linux的捷径是学习BASH，你不一定用bash，你可以用python，perl等其它的脚本语言，但bash一定要学一点，因为bash是Linux的外壳，不学bash，不足以知Linux。事实上内核是硬件的抽象层，你不需要知道你的数据是怎么写入硬盘的，这是内核要干的事情，而对于我们来说，所谓Linux无非是POSIX和shell。


+ [The Unix Workbench](https://seankross.com/the-unix-workbench/)
+ [The Art of Command Line](https://github.com/jlevy/the-art-of-command-line)
+ [shell 十三問? ](http://bbs.chinaunix.net/thread-218853-1-1.html)
+ [Bash by example, Part 1](https://www.ibm.com/developerworks/library/l-bash/index.html)
+ [Bash by example, Part 2](https://www.ibm.com/developerworks/library/l-bash2/index.html)
+ [Bash by example, Part 3](https://www.ibm.com/developerworks/library/l-bash3/index.html)
+ [Introduction to text manipulation on UNIX-based systems](https://www.ibm.com/developerworks/aix/library/au-unixtext/index.html)


Bash by Example这三篇是非常好的Bash教学材料，真正做到从入门到精通，最后一篇，用实例构建一个`ebuild`系统！`ebuild`是gentoo的包管理系统，最早期的实验版本是bash的，后来推出gentoo，用python写，现在有人用c++写的（funtoo系统）。这里你可以看到用（简单的）bash可以构建出一个系统，自动化下载、编译、安装包。


## Windows

Windows也是推荐的，毕竟国内的环境，有时候不投降不行。而用惯命令行用Windows会很不爽。


我试用了WSL，把Ubuntu子系统换成了Arch，但是我生成的ssh key，无法连接到github，用`ssh -T git@github.com`测试，根本找不到github在那里，所以很可能在WSL是无法ssh的，要在Windows主系统下才行。这让我很不爽，而弃坑（如果我错了请指出）。


传统做法，当然你可以用虚拟机，WSL之所以受欢迎就是不想切换到虚拟机，然而WSL必定也没有虚拟机这种全面支持，必定也有些限制。


那么就只能找原生的bash了，[Git for Windows](https://gitforwindows.org/)就提供了一个bash；Emacs自身也是带有`shell`和`eshell`的，都可以用，但bash真的可以干的事情太少，太多的指令是缺失的（没错，你在shell里用的很多命令都不是shell自己本身的）。

如果是Linux，不单单全，安装也容易，那么如果我们要用跑在Windows上的Bash的话，最重要的是一个所谓的【包管理器】，如同homebrew之于MacOS， apt之于Debian，pacman之于Arch等等，让我们可以安装各种各样的命令行程序。

我之前有用过`Chocolatey`，但用着感觉不爽，因为要管理员身份去安装。我需要一个普通用户随时可以安装软件的管理器，于是我找到了`scoop`，它的理念很像homebrew的装瓶（bottle）和倾倒（poured），基本上下载压缩包，解压这样的绿色操作而已，而软件从那里下载等各种信息，存放于纯文本的json文件中，请移步[Scoop文档](scoop.md)。


### ln -s的坑

在cmder下的bash，用ln -s创建软链接，会实际拷贝数据。

应该使用管理员的CMD，使用`mklink`命令：
```
创建符号链接。

MKLINK [[/D] | [/H] | [/J]] Link Target

        /D      创建目录符号链接。默认为文件
                符号链接。
        /H      创建硬链接而非符号链接。
        /J      创建目录联接。
        Link    指定新的符号链接名称。
        Target  指定新链接引用的路径
                (相对或绝对)。
```

比如：

```
mklink /D C:\Users\YGC\github D:\github
```

