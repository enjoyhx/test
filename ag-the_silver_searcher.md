the_silver_searcher是什么？ ag又是什么？

作者主页关于the_silver_searcher的说明：http://geoff.greer.fm/ag/

The Silver Searcher is a tool for searching code. It started off as a clone of Ack, but their feature sets have since diverged slightly. In typical usage, Ag is 5-10x faster than Ack. See the GitHub page for more info.

源代码：https://github.com/ggreer/the_silver_searcher

看到有用arch的同事用ag用的很爽，而我还在使用grep和find...所以在CentOS上也折腾装了下。

**安装**
直接用yum install the_silver_searcher是没有的。
看到说明
````
yum -y groupinstall "Development Tools"
yum -y install pcre-devel xz-devel
````
yum里第一个范围就大了，不装，只装后一个就可以了。
然后
````
wget https://github.com/ggreer/the_silver_searcher/archive/master.zip
mv master ag.zip
unzip ag.zip
cd the_silver_searcher-master/
./build.sh
make install
````
这个方法在较新的6.5centos下安装成功。
在6.5以下的就不行了，提示什么macro `AM_COND_IF' not found in library

后采用编译的方式完成安装，同样需要先yum -y install pcre-devel xz-devel，否则会报No package 'libpcre' found等错误。
````
wget http://geoff.greer.fm/ag/releases/the_silver_searcher-0.30.0.tar.gz
./configure
make
make install
````
虽然过程中有些warning报错，但安装完成了。

**使用方法**
ag 'hx' /www/t086.com

常用参数
-i 忽略大小写
-l 只列出文件名
-g 文件名匹配
--php 只搜索php文件
--ignore-dir 忽略目录

如：ag --ignore-dir sitedata --php hx /www/9enjoy.com

更多
-h 看帮助吧

原文：http://www.9enjoy.com/ag-the_silver_searcher/
