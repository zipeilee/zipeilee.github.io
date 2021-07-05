---
title: Manjaro折腾便条
top: false
cover: false
toc: true
date: 2021-07-04 02:53
password:
summary: 
img: https://raw.githubusercontent.com/zipeilee/zipeilee.github.io/master/medias/featureimages/8.jpg
tags: 
    - Linux
    - manjaro
    - 开发环境
categories: 
---

> 这是一份manjaro系统安装折腾指南。使用manjaro最主要的原始它的包管理器pacman十分强大，并且滚动更新，软件包版本一般都比较新（受够了ubuntu的apt安装Julia还是1.4.x版本了）。为什么不用archlinux，因为懒得折腾。

## 安装manjaro

### step1 通过[官网](https://manjaro.org/download/)下载镜像

Manjaro 提供 三种不同的桌面环境版本，由于熟悉，我选择的是`gnome`版本。

### step2 制作启动盘
 
使用[Rufus](https://rufus.ie/zh/)制作启动盘。DD模式写入，分区类型选择gpt。

### step3 安装系统

没什么好说的，进bios从u盘启动，跟随引导界面安装就是了。manjaro的安装十分简单。

关于硬盘分区，可以参考archwiki上的[相关文章](https://wiki.archlinux.org/title/Installation_guide_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))。
你也可以不看这些，直接按照引导界面的提示来操作。

## 安装好之后的基本配置

### 换源

terminal中输入
```bash
sudo pacman-mirrors -i -c China -m rank
```
换上国内镜像


### 添加[archlinuxcn repo](https://github.com/archlinuxcn/repo)

添加repo
```
[archlinuxcn]
Server = https://repo.archlinuxcn.org/$arch
```
到`/etc/pacman.conf` .

导入PGP keys：

```bash
sudo pacman -Syy && sudo pacman -S archlinuxcn-keyring
```

更新软件包
```bash
sudo pacman -Syu
sudo pacman -Syyu
```
安装yay（AUR助手）
```bash
sudo pacman -S yay
```
### 安装neofetch
```bash
sudo pacman -S neofetch
neofetch
```
### 添加中文输入法ibus-rime
```bash
sudo pacman -S ibus-rime
```
添加配置文件
```
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
ibus-daemon -d -x
```
到`~/.xprofile`中。
重启会话，在区域与语言中，添加输入源 `中文(Rime)`即可。

tips：rime默认的朙月拼音是繁体，在输入界面按F4可以选简体。

## 开始折腾
### 科学上网
科学上网方法千千万，我选v2ray.
v2ray的使用参考prjetcV上的[新手上路](https://www.v2fly.org/guide/start.html#%E5%AE%A2%E6%88%B7%E7%AB%AF)教程。

配置好了之后，使用[systemed](https://wiki.archlinux.org/title/Systemd)管理v2ray进程，常用命令：
```bash
systemctl start v2ray #开始进程
systemctl stop v2ray #结束进程
systemctl enable v2ray #开机自启动
systemctl disable v2ray #关闭开机自启动
```
有一个十分好用的跨平台图形化界面叫做qv2ray。manjaro源里没有，archlinuxcn repo里有，但是因为依赖的问题用不了。
尝试从aur自行编译失败了。解决办法是从snap安装。打开应用商店，把snap打开就行了。

关于科学上网，[新v2ray白话文指南](https://guide.v2fly.org/)是个好东西，常看常新。


### 安装字体
pacman的库中已经有许多字体包了，你可以使用pacman查找安装字体，也可以使用pacman打包不在库中的字体，具体参考[wiki](https://wiki.archlinux.org/title/Fonts_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))，下面以安装微软的连字字体[cascadia-code](https://github.com/microsoft/cascadia-code)为例：

搜索库里的字体：
```bash
pacman -Ss ttf
```
找到`ttf-cascadia-code`,说命库里已有，无需手动安装，直接通过pacman 下载：
```shell
sudo pacman -S ttf-cascadia-code 
```

### 使用 zsh
manjaro已经将[zsh](https://wiki.archlinux.org/title/Zsh_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
设为默认shell软件，并且安装了`git`, `syntax-highlighting`, `autosuggestions`等插件，所以我没有所以使用oh-my-zsh重新配置一遍。

我单独安装了一个`autojump`插件，直接用pacman下载，按照提示在~/.zshrc里添加相应的语句就行了。