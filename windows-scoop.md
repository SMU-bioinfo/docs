A command-line installer for Windows
----


## 安装Scoop

安装很简单，参照[主页](https://scoop.sh/)，只需在Powershell中执行：

```
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

## 开发


### Cmder终端

[cmder](http://cmder.net/): portable console emulator for Windows
 
```
scoop install cmder-full
```

Cmder非常好用，而且可以使用CMD, Powershell，bash，WSL等，我基本上只用bash。




### git 

```
## 如果装cmder-full就不用装git了，因为一并已经装了
##
## 命令行
scoop install git

## github桌面程序
scoop bucket add extras
scoop install github
```

### R

```
## R
scoop install r
scoop install rstudio
```

### Editor

```
## Visual Studio Code
scoop install vscode

## Vim
scoop install vim

## Emacs
## scoop bucket add extras
scoop install emacs

## spacemacs
## should have emacs installed
cd ~
git clone https://github.com/syl20bnr/spacemacs .emacs.d
```

## 文档

### Epub Reader

```
## scoop bucket add extras
scoop install calibre
```

### Zotero 

```
## scoop bucket add extras
scoop install zotero
```


## Browser

```
## scoop bucket add extras

## Firefox
## 普通版本
scoop install firefox
## 开发者版本
scoop install firefox-developer
```


## 命令行指令


```
## make for pipeline
scoop install make

## wget for download
scoop install wget
```

## IM

```
## slack
scoop install slack
```
