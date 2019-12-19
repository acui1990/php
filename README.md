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
### 安装expat
```
#tar vfx expat_2.0.1.orig.tar.gz
#cd expat-2.0.1
#./configure
#make
#make install
```
### apr-until安装
```
#tar vfx apr-util-1.5.4.tar.gz
#cd apr-util-1.5.4  
#./configure --prefix=/usr/local/apr/ --with-apr=/usr/local/apr/
#make
#make install 
```
### pcre安装
```
#tar jxvf pcre-8.00.tar.bz2
#cd pcre-8.00
#./configure --prefix=/usr/local/pcre
#make 
#make install
```

### apache安装
```
#tar jxvf httpd-2.4.38.tar.bz2
#cp -r apr-1.6.5 httpd-2.4.38/srclib/apr
#cp -r apr-util-1.6.1 httpd-2.4.38/srclib/apr-util
#cp -r pcre-8.00 httpd-2.4.38/srclib/pcre
#cd httpd-2.4.38
#./configure --prefix=/usr/local/apache --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util/ --with-pcre=/usr/local/pcre --enable-mods-shared=most --enable-so --with-included-apr
#make
#make install
```
### 启动和关闭apache
```
- 启动apache
- /usr/local/apache/bin/apachectl -k start
- 重启apache
- /usr/local/apache/bin/apachectl -k restart
- 修改apache配置  /usr/local/apache/conf/
- 在浏览器中输入http://9.146.192.254/index.html， 如果显示It works就证明已经搭建成功。（默认部署在/usr/local/apache/htdocs/index.html）
```

## MYSQL安装
MySQL可以通过Yum或其它安装包快速安装，也可以下载源代码编译安装。从源代码编译安装MySQL有一些好处，如可以指定编译生成参数、优化编译、指定安装位置等。

### 安装 libxml2
```
#cd /data/cuiyu
#tar zxvf  libxml2-2.6.32.tar.gz
#cd libxml2-2.6.32
#./configure --prefix=/usr/local/libxml2
#make
#make install
```

### 安装 mcrypt库
```
#tar zxvf libmcrypt-2.5.8.tar.gz
#cd libmcrypt-2.5.8
#./configure
#make
#make install
```

### 安装curl
```
#cd /data/cuiyu
#tar -zxf curl-7.42.1.tar.gz
#cd curl-7.42.1
#./configure --prefix=/usr/local/curl
#make
#make install
```

安装 mcrypt库
cd /data/cuiyu
tar zxvf libmcrypt-2.5.8.tar.gz
cd libmcrypt-2.5.8
./configure
make
make install安装 mcrypt库
cd /data/cuiyu
tar zxvf libmcrypt-2.5.8.tar.gz
cd libmcrypt-2.5.8
./configure
make
make install

### PHP安装
- 下载最新稳定版本PHP：http://www.php.net/downloads.php
- 解压缩，#tar jxvf php-5.6.16.tar.bz2
- 进入目录,  #cd php-5.6.16
-  #./configure --prefix=/usr/local/php --with-mysql=/usr/local/mysql --with-apxs2=/usr/local/apache2/bin/apxs --with-libxml-dir=/usr/local/libxml2 --with-curl=/usr/local/curl
- #make;
- #make install
- 修改APACHE的配置文件支持PHP vi /usr/local/apache2/conf/httpd.conf
在AddType application/x-gzip .gz .tgz下面增加最后两行，如下：
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .php5
- 测试PHP，cd /usr/local/apache2/htdocs/; vi test.php；
<?
php phpinfo()
?>
如果访问xx.xx.xx.xx/test.php 显示表格信息就证明表示PHP安装成功



