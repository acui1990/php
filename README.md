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
```
#tar vfx apr-util-1.5.4.tar.gz
#cd apr-util-1.5.4  
#./configure --prefix=/usr/local/apr/ --with-apr=/usr/local/apr/
#make
#make install 
```
### apache安装

```
#tar vfx apr-util-1.5.4.tar.gz
#cd apr-util-1.5.4  
#./configure --prefix=/usr/local/apr/ --with-apr=/usr/local/apr/
#make
#make install 
```
1.下载最新稳定版apache： http://apache.dataguru.cn//httpd/httpd-2.2.31.tar.bz2
2.解压缩，#tar jxvf httpd-2.2.31.tar.bz2
3.进入目录,  #cd  httpd-2.2.31
4. configure,  ./configure —prefix=/usr/local/apache2
5.#make;
6.#make install;
5.启动，#/usr/local/apache2/bin/apachectl -k start
6.在浏览器中输入10.12.xx.xx/index.html， 如果显示It works就证明已经搭建成功。（默认部署在/usr/local/apache2/htdocs/index.html）

### 启动和关闭apache
```
#/usr/local/apache2/bin/apachectl -k start
#/usr/local/apache2/bin/apachectl -k stop
#/usr/local/apache2/bin/apachectl -k restart
```
## MYSQL安装
MySQL可以通过Yum或其它安装包快速安装，也可以下载源代码编译安装。从源代码编译安装MySQL有一些好处，如可以指定编译生成参数、优化编译、指定安装位置等。

## php安装
### libxml2安装
这个是安装PHP必须的
1.下载最新版本的源码：http://www.php.net/downloads.php， 文件名libxml2-git-snapshot.tar.gz
2.解压缩，# tar zxvf  libxml2-2.6.32.tar.gz
3.进入目录；# cd libxml2-2.6.32
4.configure;  #./configure --prefix=/usr/local/libxml2
5.#make;
6.#make install

### PHP安装
1.下载最新稳定版本PHP：http://www.php.net/downloads.php
2.解压缩，#tar jxvf php-5.6.16.tar.bz2
3.进入目录,  #cd php-5.6.16
4. #./configure --prefix=/usr/local/php --with-mysql=/usr/local/mysql --with-apxs2=/usr/local/apache2/bin/apxs --with-libxml-dir=/usr/local/libxml2 --with-curl=/usr/local/curl
5.#make;
6.#make install
7.修改APACHE的配置文件支持PHP vi /usr/local/apache2/conf/httpd.conf
在AddType application/x-gzip .gz .tgz下面增加最后两行，如下：
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .php5
6.测试PHP，cd /usr/local/apache2/htdocs/; vi test.php；
<?
php phpinfo()
?>
如果访问xx.xx.xx.xx/test.php 显示表格信息就证明表示PHP安装成功



