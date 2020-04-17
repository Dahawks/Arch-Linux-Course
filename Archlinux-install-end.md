##### 一，配置网络

> systemctl enable NetworkManager

##### 二，创建虚拟内存

1. 分配一块空间用于交换文件

    > fallocate -l 大小 /swapfile

2. 更改权限

    > chmod 600 /swapfile

3. 设置交换文件

    > mkswap /swapfile

4. 启用交换文件

    > swapon /swapfile

5. 编辑`/etc/fstab`为交换文件设置一个入口

    > vim /etc/fstab

    直接在最后一行添加以下内容

    > /swapfile none swap defaults 0 0

##### 三，新建用户

> useradd -m -G wheel username (将username替换为你的用户名)

各参数的含义：

`-m`：在创建用户的同时在`/home`目录下创建一个与用户名同名的文件夹。

`-G wheel`：`-G`代表把用户加入一个组中，后面跟着的`wheel`就是要加入的组名

为新用户设置一个密码

> passwd username (将username替换为你的用户名)

##### 四，配置sudo

1. 安装sudo

    > pacman -S sudo

2. 配置sudo

    > vim /etc/sudoers

    找到`# %wheel ALL=(ALL)ALL`

    去除掉前面的`#`注释符。保存并退出

3. 注：这里的`%wheel`就是代表`wheel`组，意味着`wheel`组中的所有用户都可以使用`sudo`命令

# Font
Source Code Pro
nerd-fonts-source-code-pro

noto-fonts

# Emoji
> sudo pacman -S ttf-linux-libertine ttf-inconsolata ttf-joypixels noto-fonts-emoji ttf-liberation ttf-droid
> yay -S ttf-twemoji-color

# Chinese
> sudo pacman -S wqy-bitmapfont wqy-microhei wqy-microhei-lite wqy-zenhei adobe-source-han-mono-cn-fonts adobe-source-han-sans-cn-fonts adobe-source-han-serif-cn-fonts

