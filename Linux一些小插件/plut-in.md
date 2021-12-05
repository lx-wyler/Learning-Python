# 显示CPU、内存、网速等信息的插件
> 1. 添加软件源（必须得添加这个，没这个会提示搜不到包）

> ```sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor && sudo apt update```
> 
> 可以使用下面这个命令来删除该源
> 
> ```sudo add-apt-repository -r ppa:fossfreedom/indicator-sysmonitor```
> 
> 2. 安装软件
> ···
> sudo apt install indicator-sysmonitor -y
> ···
> 3. 打开软件，任务栏会显示一些信息，在显示信息的地方右键打开Preferences，General里设置开机启动，Advanced里面添加显示网速的选项：```Net:{net}```
