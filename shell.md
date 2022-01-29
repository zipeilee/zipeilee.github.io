# Terminal Shell Prompt

## WSL
- linux子系统 可以互相访问使用linux和windows的二进制文件(exe)
- 安装 微软商店有各种发行版,也可以使用tar包安装商店未提供的发行版(比如arch),tar包可以通过docker获得

## Terminal Shell Prompt 的区别

### 终端Terminal
一台大型主机往往需要支持许多用户同时使用，每个用户所使用操作的设备，就叫做Terminal——终端，终端使用通信电缆与电脑主机连接，甚至可以通过电信网络（电话、电报线路等等）连接另一个城市的电脑

终端模拟器:
- Windows Termianl
- Xshell
- iterm2
- Kitty

### Shell
Shell(壳)是操作系统的外壳,是与操作系统进行交互的软件

- Bash
- Zsh
- PowerShell
- Fish
###   Prompt(命令行提示符)
提示符就是提示你输入 Shell 命令用的，每次运行完一个命令后都会再显示一次提示符，等待下一个命令。不同发行版、不同 Shell 的默认提示符格式也不同。

比如bash中最常见的`[prin@localhost ~]$`
一般来说，提示符都会包含这些信息：当前用户、主机名、当前目录等。有的可能更高级，包括了当前 Git 状态、环境信息、时间、上一条命令的返回值等等。
比如zsh的某些某些主题(比如power10k).

我们可以通过修改`$PS1`环境变量来自定义自己喜欢的名利提示符形式.

## Fish 
### 为什么使用Fish
- 自动补全 
- 高亮
- 以上功能无需插件
- 在wsl中速度比带插件的zsh快

### Fish和Zsh Bash的区别
语法不同,比如最基本的赋值,配置环境变量,正则表达式
以配置代理为例.

### 如何使用fish
在fish中输入help可以在浏览器打开帮助文档

因此不推荐设置将fish设置为默认的shell(因为这样需要把你的bash配置完全重写),配合Windows Termianl使用,仅将其作为交互式shell使用.这样能照常使用bash的初始化脚本.

只需在windows terminal中加入命令 ` -e fish `
即可.
## 自定义Fish的Prompt

### 网页界面
在fish中输入
```
fish_config
```
即可进入网页配置界面.(注意,若使用wsl可能需要配置一下wsl默认的浏览器.)

### fish_prompt 函数
