# CLI - 相见恨晚的命令

## 终端打开文件

+ MacOS: `open`
+ Linux: `xdg-open`
+ Windows: `start`

使用MacOS的时候，我最喜欢的是`open`指令，因为可以快速在终端中打开文件，比如你跑了程序，生成了结果，你可以用`open your_file`打开这个文件，而不是打开`Finder`，浏览到你的目录，再打开文件。

比如`open xx.pdf`会使用`Preview`打开这个PDF，而`open xx.html`会使用浏览器打开这个html文件。非常方便，如果你要用`Finder`打开当前的工作目录，则使用`open .`就可以。

我是如此喜欢这个命令，以至于我要把`open .`包装在R里面，这样我在R的终端中也可以随意打开当前的工作目录，当然没有通用性的函数不是好函数，所以我的函数同时也支持Linux和Windows。Windows好搞，用`explorer`，但Linux，我并不知道别人的电脑装的是什么文件浏览器，所以不能直接用文件浏览器的指令放进去，于是我找到了`xdg-open`，这个函数我偷偷放在`rvcheck::o()`中，供自己使用。也就是说你在R中，使用`o()`就可以用文件浏览器打开当前的工作目录，而且这函数跨平台。

MacOS的`open`和Linux的`xdg-open`都可以打开别的文件，在使用了一段时间的Windows之后，还是无比想念`open`这个指令，后来我发现Windows中也有同样的指令，叫`start`，于是又可以很爽快地在终端中打开文件了，然后我也更新了`rvcheck::o()`函数，如果`o()`则打开目录，而`o(文件名)`则打开文件。


## 压缩PDF

用gs效果比imagemagick要好。

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH \
    -sOutputFile=output.pdf input.pdf
```

不加`-dPDFSETTINGS`参数的话，使用默认的`-dPDFSETTINGS=/prepress`，文件会稍大一点，文件最小的应该是使用`-dPDFSERRINGS=/screen`，但PDF效果可能很差。

