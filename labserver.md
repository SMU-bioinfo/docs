
尽量不要自己安装软件，找管理员。

另外有一些可以共用，比如你自己可以安装到home下面的，统一大家都安装到/opt下，所有人有权限。没权限的话，找管理员，自己只要设置好PATH就行。

## R

统一加这一行到`~/.Renviron`下：

```
R_LIBS_USER='/opt/R/library'
```

这样所有人安装的包都在同一目录中，当然如果你需要不同的版本的时候除外，共用的尽量保持更新。

## 远程挂程序

最简单的莫过于`nohup`，命令还是一样跑，前面加上nohup，就可以实现挂起。当然这时候如果你想看命令的输出呢？默认情况下，命令的输出会写入到`nohup.out`中，你当然可以自己用`> filename`去指定输出，或者`>/dev/null`把输出扔掉。

那么`nohup.out`是实时在更新的，命令一有输出就写入，你用`cat`这些命令就没法实时看，你可以用`tail`命令，一方面它读文件尾部，我们只关心实时写入的文件尾，另一方面，它有`-f`参数，实现循环读取，也就是不断地去监测文件是否有变化，有变化就把新写入的读出来。这样可以实现我们挂程序同时又可以察看命令输出的目的。

万一你跑了程序没有用`nohup`，又想要挂起呢，用`bg`命令可以把程序放到后台去跑，同样地，`fg`命令可以把后台程序放到前台来。

一个主流的做法是让你的终端随时可以挂起任何任务，我自己以前用过`screen`，这是老牌软件，绝对可靠。新晋派是`tmux`，有很多比较fancy的特性，不过我没用过了，没经验，如果你们使用它的话，可以把使用经验记录下来。

+ [nohup 命令](https://www.ibm.com/support/knowledgecenter/zh/ssw_aix_72/com.ibm.aix.cmds4/nohup.htm)
+ [Linux bg command](https://www.computerhope.com/unix/ubg.htm)
+ [fg Command](https://www.ibm.com/support/knowledgecenter/en/ssw_aix_71/com.ibm.aix.cmds2/fg.htm)
+ [使用 screen 管理你的远程会话](https://www.ibm.com/developerworks/cn/linux/l-cn-screen/)
+ [A Gentle Introduction to tmux](https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340)

### 有GUI的程序怎么办？

大概可以参考[Windows远程及本地运行Linux的GUI程序](https://mp.weixin.qq.com/s/1bJPkAypZu_gFuKTfd3xyA)。

MacOS的话，需要有`XQuartz`安装（可以通过`Homebrew`），而Windows下需要有`Xming`安装（可以通用[scoop](https://github.com/YuLab-SMU/docs/blob/master/windows-scoop.md)）。

有X server的话，就可以直接ssh -X，然后就可以跑了。

不过要实现程序挂起，好像得通过VNC才可实现，当然你也可以试一下`TeamViewer`。

