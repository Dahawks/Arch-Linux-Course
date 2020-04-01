- 建立一个`vi`指向`vim`的软链接，因为有的命令调用`vi`做编辑器而不是`vim`，比如`visudo`
> ln -sf /usr/bin/vim /usr/bin/vi
>
> -s 软链接(符号链接)
>
> -f 强制执行

- 安装man命令详解
> pacman -S man 
> 用法：
> man ls
> man 后面加上你需要查询的命令

- 安装中文`man`命令
> pacman -S man-pages-zh_cn man-pages-zh_tw
> 用法同上