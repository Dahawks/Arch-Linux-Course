### Archlinux 安装 oh-my-zsh

一,安装zsh，git，wget，curl

> sudo pacman  -S zsh git wget curl

用curl安装oh-my-zsh

curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh

用wget安装oh-my-zsh

sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O - | sh

这两种方式任意一种都可以



二,插件

- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) 自动补全插件
	1. 下载`zsh-autosuggestions`到`.oh-my-zsh`的插件目录
	> git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
	2. 编辑`.zshrc`文件
	找到`plugins=(git)`这一行，如果没有就添加。更改为如下
	> plugins=(git zsh-autosuggestions)
