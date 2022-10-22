# 安装系统

> 1. 镜像下载
>
>    在[这里](https://cn.ubuntu.com/)下载，根据自己需要选择合适的版本
>
> 2. 系统分区
>
>    可以参考下面的分区
>
>    ![](C:\Users\lx\Desktop\微信图片_20211230164431.jpg)

# 安装软件

> - 搜狗输入法
>
>   [官网](https://pinyin.sogou.com/linux/?r=pinyin)下载对应系统版本的软件，有两个，注意自己系统，下载点下载后会跳出来一个[网页](https://pinyin.sogou.com/linux/help.php)，按照网页操作即可。
>
> - VSCODE
>
>   [官网](https://code.visualstudio.com/)下载.deb安装包，然后用**```sudo dpkg -i ***.deb```**安装
>
> - Chrome
>
>   在终端输入
>
>   ```shell
>   wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
>   ```
>
>   将安装包下载到当前目录下，然后安装
>
>   ```shell
>   sudo dpkg -i ./***.deb  # ***就是安装包的名称，可以在下载后改简单点，容易操作
>   ```
>
>   更改默认的搜索引擎为百度，使用下面的地址
>
>   ```http
>   https://www.baidu.com/s?ie=${inputEncoding}&wd=%s
>   ```
>
> - 剩下的等再次安装的时候记录（conda、docker、cuda等）
>
>   或者参考知乎稚晖君的[文章](https://zhuanlan.zhihu.com/p/336429888)

# 解决22.04遇到的问题

1. 使用```sudo apt update```和```sudo apt upgrade```后出依赖问题，可能是更换的源和安装的系统，版本不匹配导致。比如，源里面其中一句```deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse```中，**focal**就是系统版本。

   此时使用```lsb-release -a```查看自己系统版本号，然后替换上面的**focal**。（```sudo gedit /etc/apt/sources.list```），再次执行更新即可。

2. [安装梯子](http://qv2ray.net/lang/zh/getting-started/step2.html#%E4%B8%8B%E8%BD%BD-v2ray-%E6%A0%B8%E5%BF%83%E6%96%87%E4%BB%B6)

   Qv2ray需要配置。首选项里面的第二个选项卡，第一个需要选v2ray这个文件，第二个选择该文件所在的路径。v2ray和v2ctl需要可执行。外面的```applmage```文件需要可执行，第一次用命令行打开。

3. 安装VMware tools后无法复制和托文件

   想办法移除VMware tools，然后运行下面三条命令

   ```bash
   sudo apt-get autoremove open-vm-tools
   sudo apt-get install open-vm-tools
   sudo apt-get install open-vm-tools-desktop
   ```

   重启即可。

   > 好像执行第一个命令，能移除VMware tools，然后再执行下面两个就行了。
