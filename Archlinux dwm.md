##### 零，安装`xorg`服务
	> sudo pacman -S xorg xorg-server xorg-xinit
##### 一，安装`dwm`

- 在家目录执行下面命令，将`dwm`源代码下载下来

```
git clone https://git.suckless.org/dwm
```

- 进入`dwm`目录

```
cd dwm
```

- 编辑`config.h`文件以配置`dwm`
```
vim config.h
```
- 如果没有`config.h`文件，但是有`config.def.h`文件，那么将`config.def.h`复制为`config.h`文件，将`config.def.h`文件删除
```
cp config.def.h config.h
rm config.def.h
```

- 配置`dwm`
    - 修改窗口间隔
	    > static const unsigned int borderpx  = 1;        /* border pixel of windows */
	    > 1 是像素，改成你想要的像素。

- 编译`dwm`
	
	> 使用`make`命令编译

- 编译安装`dwm`
	
	> sudo make clean install

- 通过`startx`命令进入dwm
	- 复制`xinitrc`到家目录并改名为`.xinitrc`
	> cp /etc/X11/xinit/xinitrc ~/.xinitrc
	
	- 编辑`~/.xinitrc`
	
	    在最下面添加`exec dwm`
	
	    将以下几行注释掉(在前面加上`#`注释)
		```
		# twm &
		# xclock -geometry 50x50-1+1 &
		# xterm -geometry 80x50+494+51 &
		# xterm -geometry 80x20+494-0 &
		# exec xterm -geometry 80x66+0+0 -name login
		```
	

