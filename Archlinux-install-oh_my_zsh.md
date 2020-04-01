### Archlinux 安装 oh-my-zsh

一,安装zsh，git，wget，curl

> sudo pacman  -S zsh git wget curl

用curl安装oh-my-zsh

sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

用wget安装oh-my-zsh

sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

这两种方式任意一种都可以