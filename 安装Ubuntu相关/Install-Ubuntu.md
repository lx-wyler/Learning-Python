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

