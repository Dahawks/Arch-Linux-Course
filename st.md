# 安装
在家目录执行
> git clone https://git.suckless.org/st

克隆下来后，进入st目录
> cd st

编辑`config.mk`

```
更改10和11行
X11INC = /usr/X11R6/include > X11INC = /usr/include/X11 
X11LIB = /usr/X11R6/lib     > X11LIB = /usr/include/X11
```

如果是使用的Ubuntu,debian等系统，需要安装`libx11-dev`,`libxft-dev`

使用`sudo make clean install`编译安装`st`

编译安装后会自动将`config.def.h`复制为`config.h`

手动删除`config.def.h`
> rm config.def.h

编辑`config.h`(st的配置文件，每次编辑完了，都要编译安装一次)
> vim config.h

```
第8行 字体
static char *font = "Liberation Mono:pixelsize=12:antialias=true:autohint=true";
static char *font = "字体(要已经下载好的字体):pixelsize=字体大小:antialias=true:autohint=true"
例如:
Static char *font = "Source Code Pro:pixelsize=24:antialias=true:autohint=true";
```

更改完成后执行
> sudo make clean install
编译安装

提交`st`到git

链接你的`github`
> git config --global user.email "2548171533@qq.com"
> git config --global user.name "dahawks"

> git status 查看修改

```
hawks@archlinux st]$ git status 
On branch master
Your branch is up to date with 'origin/master'.  

Changes not staged for commit:   
  (use "git add/rm <file>..." to update what will be committed)   
  (use "git restore <file>..." to discard changes in working directory)         
	deleted:    config.def.h         
	modified:   config.mk  

Untracked files:   
  (use "git add <file>..." to include in what will be committed)
  	config.h         
	st <        
	st.o <	这三个文件是不用的，在`.gitignore`中添加这三个文件
	x.o <
no changes added to commit (use "git add" and/or "git commit -a")
```

> vim .gitignore (没有的话，就新建一个)
在里面添加这些内容

```
st   
*.o   
*.orig   
*.rej
```

再一次`git status`
那三个不用的文件就不在了

使用`git add .`添加所有没有提交的更改
使用`git status`会发现所有的更改变为了绿色
使用`git commit -m "描述"`来提交更改

下载补丁到源代码目录
> sudo pacman -S wget
> wget https://st.suckless.org/patches/alpha/st-alpha-0.8.2.diff

通过`patch`命令来打补丁
> patch < 补丁名.diff

如果提示
```
[dahawks@archlinux st]$ patch < st-alpha-0.8.2.diff 
can't find file to patch at input line 5 
Perhaps you should have used the -p or --strip option? 
The text leading up to this was: 
-------------------------- 
|diff --git a/config.def.h b/config.def.h 
|index 0e01717..e116631 100644 
|--- a/config.def.h 
|+++ b/config.def.h 
-------------------------- 
File to patch: 在这里输入`config.h`
```

每打完一次补丁，编译安装一次
> sudo make clean install

提交`git`
> git status
> git add .
> git commit -m "alpha patch"

| 推荐的补丁 |
| :--------: | :--: |
| st-alpha-0.8.2.diff |
| st-anysize-0.8.1.diff |
| st-blinking-cursor-20180605.diff |
| st-copyurl-20190202-3be4cf1.diff |
| st-desktopentry-0.8.2.diff |
| st-dracula-0.8.2.diff |
| st-fontfix.diff |
| st-hidecursor-0.8.1.diff |
| st-lukesmith-externalpipe(if_you_dont_have_scrollback).diff |
| st-lukesmith-externalpipe(if_you_have_scrollback).diff |
| st-scrollback-20190331-21367a0.diff |
| st-vimBrowse-20191203-2b8333f.diff |


如果提示
```
hawks@archlinux st]$ patch < st-dracula-0.8.2.diff 
can't find file to patch at input line 5 
Perhaps you should have used the -p or --strip option? 
The text leading up to this was: 
-------------------------- 
|diff --git a/config.def.h b/config.def.h 
|index 877afab..6a1699f 100644 
|--- a/config.def.h 
|+++ b/config.def.h 
-------------------------- 
File to patch: config.h 
patching file config.h 
Hunk #1 FAILED at 84. 1 out of 1 hunk FAILED -- saving rejects to file config.h.rej
```
这里是说打补丁`失败`了，需要我们手动打补丁
打开`config.h.rej`文件查看需要我们手动打补丁的部分
前面有`-`是需要删除的
前面有`+`是需要添加的
绿色前面的`+`号是不需要的
根据`config.h.rej`文件中的`-`,`+`部分在`config.h`中修改
`/* */`是注释，里面的可以不用删除和添加
-----------------
第一行和第二行的 
--- config.def.h   
+++ config.def.h
可以不用修改
-----------------

 st-scrollback-20190331-21367a0.diff 
默认快捷键(Shift+PageUp,PageDown)
可以在`config.h`中修改默认快捷键
```
{ ShiftMask,            XK_Page_Up,     kscrollup,      {.i = -1} }, 
{ ShiftMask,            XK_Page_Down,   kscrolldown,    {.i = -1} },
这两行是`scrollback`绑定的快捷键
这里我们修改为(Alt+j,k) Alt键默认为`MODKEY`
{ MODKEY,            XK_k,     kscrollup,      {.i = -1} }, 
{ MODKEY,            XK_j,     kscrolldown,    {.i = -1} },
```

st-dracula-0.8.2.diff












