# php
tlinux环境上搭建环境，部署PHP项目,我没有用yum和rpm这些安装管理工具。对版本没要求的可以直接安装yum install。以下方法是用源码安装，将下载的文件（.tar.gz）上传到目的服务器上，然后解压进入对应...
## apache安装
先安装依赖，再安装Apache，否则就会报各种APR not found. Please read the documentation此类错误
### apr安装
```
 #tar vfx apr-1.5.2.tar.gz         #解压缩
 #cd apr-1.5.2                       #进入目录
 #./configure --prefix=/usr/local/apr/  #configure
 #make                   #make
 #tar vfx apr-1.5.2.tar.gz #解压缩
 #make install   
```
### apr-until安装
