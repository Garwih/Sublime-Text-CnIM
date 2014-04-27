Sublime-Text-CnIM
=================

Linux下的Sublime Text中文输入法支持文件
以下内容运行在Ubuntu 14.04中，其他Linux发行版理论上大同小异，请根据你的系统环境做相应的更改。

###下载
```Bash
    git clone https://github.com/Garwih/Sublime-Text-CnIM.git
```
####*.使用sublime text 3官方.deb安装包安装的：
**复制文件到对应目录**
```bash
    cd Sublime-Text-CnIM
    sudo cp -r usr /
    sudo cp -r opt /
```
####*.其他方式安装的：
**安装编译环境**
```bash
    sudo apt-get install build-essential
    sudo apt-get install libgtk2.0-dev
```
**进入sub-fcitx.c所在目录，执行下面命令编译成共享库**
```bash
    gcc -shared -o sub-fcitx-cn.so sub-fcitx.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC
```
**使用下面命令启动Sublime Text 3，测试能否切换并输入中文**
```bash
    LD_PRELOAD=./sub-fcitx-cn.so subl
```
*subl为Sublime Text 3默认启动命令*

*如果你不是使用该命令，请将subl改为你自己的Sublime Text启动命令*

**如果上面的命令启动后能输入中文**

*复制sub-fcitx-cn.so到Sublime Text所在目录*
```bash
    sudo cp sub-fcitx-cn.so /opt/sublime_text/sub-fcitx-cn.so
```
*编辑Sublime Text启动命令*
```bash
    sudo gedit /usr/bin/subl
```
*在**#!/bin/sh**下面添加一行*
```bash
    export LD_PRELOAD=/opt/sublime_text/sub-fcitx-cn.so
```

###Enjoy～
