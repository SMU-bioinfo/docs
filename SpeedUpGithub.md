1. 用`SSH`连接`github`

======================

1.1 检查`SSH`是否存在
---------------------

    ll ~/.ssh/

看是否存在`id_rsa.pub`,`id_ecdsa.pub`,
`id_ed25519.pub`这几个默认文件之一,如果没有，那就先创建。

1.2 创建新的`SSH` key，并把它添加到`ssh-agent`
----------------------------------------------

    ssh-keygen -t rsa -b 4096 -C "you_email@example.com" -f ~/.ssh/github_id_sra
    #会让你选择保存的文件在哪里
    #并输入密码
    ll ~/.ssh/

创建完成后，再添加到`ssh--agent`.

    # Start the ssh-agent in the background.
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/github_id_rsa

1.3 将生成的`SSH`key添加到你的`github`账号下
--------------------------------------------

复制好`github_id_rsa.pub`文件中的信息，
网页打开github账户，点击`Settings`,接着点左栏中的`SSH and GPG keys`,然后点击`New SSH key`,输入`title`(备注:如YourComputer)，并在下面`key`中粘贴复制的信息。再点`Add SSH key`
输入账号密码就可以了。

1.4 测试`SSH`连接
-----------------

    ssh -T git@github.com

如果出现`Hi username! You've successfully authenticated, but GitHub does not provide shell access`则表示成功,如果出现`Permission denied (publickey)`类似信息，[参考这个](https://help.github.com/en/github/authenticating-to-github/error-permission-denied-publickey)

2. 生成gitee公匙

================

2.1 生成公匙文件
----------------

    # Generating public/private rsa key pair
    ssh-keygen -t rsa -C "your@example.com" -f ~/.ssh/gitee_id_sra
    cat ~/.ssh/gitee_id_rsa.pub

接着复制`gitee_id_rsa.pub`文件内容到`gitee`个人设置的`SSH公匙`下添加即可。

3. 生成config文件

=================

添加如下信息在`~/.ssh/config`中

    # github
    Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_id_rsa
    # gitee
    Host gitee.com
    HostName gitee.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/gitee_id_rsa

4. 加速下载`github`中的仓库

===========================

要想快速下载`github`中的仓库，配置好后就可以先在网页右上角的加号`+`下选择从`github`中导入，然后`gitee`可以去拉`github`的目标仓库，网速会比较快，接着再通过`git clone`操作`clone`到本地。从而实现在大陆下载`github`中的仓库过慢的问题。

5. reference

============

[connecting to github with
ssh](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
