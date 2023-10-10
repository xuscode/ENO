
# R2021x-linux

## 前期规划

     //v6r2022x.3ds.com:1521/enoviav6

     x3dpassadmin

     x3dpasstokens

     admin_platform@3ds.com
     Qwer1234

     https://v6r2022x.3ds.com:443/3dpassport

     https://v6r2022x.3ds.com:443/3dspace


     Files will be installed in the following directory:
     /app/DassaultSystemes/R2022x/3DPassport
     Java Development Kit (JDK) path: /app/jdk-11.0.16
     Apache TomEE+ installation path: /app/tomee/3dpassport
     Force lowercase users' login: No
     Database Type: Oracle
     Directory of tnsnames.ora: 
     Net service name or database URL for 3DPassport application: //v6r2022x.3ds.com:1521/enoviav6
     Database URL for the tokens database: //v6r2022x.3ds.com:1521/enoviav6
     Database username: x3dpassadmin
     Tokens database username: x3dpasstokens
     Database connection OK
     Administrator email: admin_platform@3ds.com
     3DPassport service URL: https://v6r2022x.3ds.com:443/3dpassport
     3DCompass service URL: https://v6r2022x.3ds.com:443/3dspace
     Mail server name: v6r2022x.3ds.com
     Mail sender name: admin_platform@3ds.com

     cp "/app/DassaultSystemes/R2022x/3DPassport/linux_a64/templates/3DPassport_httpd_fragment.conf" /app/apache14/conf/

## 输出tomee日志
     cd /app/tomee/3dpassport/logs/
     tail -f catalina.out

## 3pashboard

     Files will be installed in the following directory:
     /app/DassaultSystemes/R2022x/3DDashboard
     Java Development Kit (JDK) path: /app/jdk-11.0.16
     Apache TomEE+ installation path: /app/tomee/3ddashboard
     Choose the database type: Oracle
     tnsnames.ora directory: 
     Net_service_name: //v6r2022x.3ds.com:1521/enoviav6
     Database Connection User Name: x3ddashadmin
     3DPassport service URL: https://v6r2022x.3ds.com:443/3dpassport
     3DDashboard service URL: https://v6r2022x.3ds.com:443/3ddashboard
     3DCompass service URL: https://v6r2022x.3ds.com:443/3dspace
     6WTag service URL: https://v6r2022x.3ds.com:443/3dspace
     Mail server name: v6r2022x.3ds.com
     Mail sender name: admin_platform@3ds.com
     Domain to use for loading external Widgets (untrusted widgets): untrusted.v6r2022x.3ds.com
     Allow WebAPI for following domains: .*
     Shared directory: /app/DassaultSystemes/3DDashboardData

## 查看操作系统版本
首先检查Linux的操作系统。达索官方推荐的是Red HatEnterprise Linux 7.5和SuSELinux Enterprise Server 12 SP2两个版本（操作系统要求与r2020x相同）。

     [x3ds@r2021x ~]$ cat /etc/redhat-release
     Red Hat Enterprise Linux Server release 7.5 (Maipo)
## 查看机器名
     [x3ds@r2021x ~]$ hostname
     r2021x.mydomain.com
## 查看IP设置
     [x3ds@r2021x ~]$ cat /etc/hosts
     127.0.0.1   localhost  localhost.localdomain localhost4 localhost4.localdomain4
     ::1         localhost  localhost.localdomain localhost6 localhost6.localdomain6
     127.0.0.1 r2021x.3ds.com r2021x
     127.0.0.1 untrusted.3ds.com untrusted
     192.168.100.1   mydslsserver

## 主机名修改（如果需要）

一般来说，主机名都尽量在操作系统安装的时候就设置好，可以用hostname命令查看本机的主机名，如果不符合要求想修改的话，可以使用下面命令进行更改。
使用root账号，使用命令 

     vi /etc/sysconfig/network

增加内容如下： 

     NETWORKING=yes 
     HOSTNAME=dsu.3ds.com

## 修改HOST文件
使用root账号，使用命令
     
     vi /etc/hosts

## 操作系统安装时，勾选安装以下内容
     E-mail Server
     FTP Server
     Large Systems Performance
     Performance Tools
     Compatibility Libraries
     Development Tools
     Security Tools

## 此外还需要用root安装以下Linux的rpm文件

     # rpm -Uvh ksh-20120801-139.el7.x86_64.rpm
     # rpm -Uvh libaio-devel-0.3.109-13.el7.x86_64.rpm
     # rpm -Uvh libaio-0.3.109-13.el7.x86_64.rpm
     # rpm -Uvh numactl-devel-2.0.9-7.el7.x86_64.rpm
     # rpm -Uvh redhat-lsb-core-4.1-27.el7.centos.1.x86_64.rpm redhat-lsb-submod-security-4.1-27.el7.centos.1.x86_64.rpm  spax-1.5.2-13.el7.x86_64.rpm
     # rpm -Uvh motif-2.3.4-14.el7_5.x86_64.rpm  libXp-1.0.2-2.1.el7.x86_64.rpm xorg-x11-xbitmaps-1.1.1-6.el7.noarch.rpm
     # rpm -Uvh httpd-2.4.6-88.el7.centos.x86_64.rpm httpd-tools-2.4.6-88.el7.centos.x86_64.rpm
     # rpm -Uvh mod_ssl-2.4.6-88.el7.centos.x86_64.rpm
     # rpm -Uvh  zlib-devel-1.2.7-18.el7.x86_64.rpm
     # rpm -Uvh compat-libstdc++-33-3.2.3-72.el7.x86_64.rpm
     # rpm -Uvh xorg-x11-server-Xvfb-1.20.1-3.el7.x86_64.rpm

## 安装数据库之前，先用root创建目录并开通权限
   
     # cd /
     # mkdir app
     # chmod -R 777 app
 
     # cd /app
     # mkdir -p ./oracle/product/19.3.0.0/db_1
     # chown -R x3ds:oinstall ./oracle



## 安装JDK

解压jdk文件，并将解压的目录移动到app目录下。
下载地址：
https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html

     tar zxvf jdk-11.0.13_linux-x64_bin.tar.gz   
     mv jdk-11.0.13 /app/jdk-11.0.13

修改环境变量

使用root账号配置x3ds用户的环境变量
     # vi /home/x3ds/.bash_profile
     <add the following lines at the bottom of file>
     
     TMP=/tmp; export TMP
     TMPDIR=$TMP; export TMPDIR
     
     ORACLE_HOSTNAME=r2021x.mydomain.com; export ORACLE_HOSTNAME
     ORACLE_UNQNAME=MYDB; export ORACLE_UNQNAME
     ORACLE_BASE=/app/oracle; export ORACLE_BASE
     ORACLE_HOME=$ORACLE_BASE/product/19.3.0.0/db_1; export ORACLE_HOME
     ORACLE_SID=MYDB; export ORACLE_SID
     
     PATH=/usr/sbin:$PATH; export PATH
     PATH=$ORACLE_HOME/bin:$PATH; export PATH
     
     LD_LIBRARY_PATH=$ORACLE_HOME/lib:/lib:/usr/lib:/usr/local/lib;

     export  LD_LIBRARY_PATH
     CLASSPATH=$ORACLE_HOME/jlib:$ORACLE_HOME/rdbms/jlib; 

     export CLASSPATH
配置完成后需要使用x3ds账号运行source~/.bash_profile 生效，或者重启操作系统生效。

## 安装数据库

下载数据库安装介质LINUX.X64_193000_db_home.zip

官网地址：https://www.oracle.com/database/technologies/oracle-database-software-downloads.html#19c
按下面方法解压：
拷贝LINUX.X64_193000_db_home.zip  到/tmp
 
     $ cd /app/oracle/product/19.3.0.0/db_1
     $ unzip /tmp/LINUX.X64_193000_db_home.zip


用第4步创建的用户x3ds安装数据库（建议不要使用root安装）

     $ cd /app/oracle/product/19.3.0.0/db_1
     $ ./runInstaller

此处为前置条件的检查，如果出现shmmax等参数配置提醒，请使用root编辑/etc/sysctl.conf文件，调整资源配置。
<请先备份再修改>

     # vi /etc/sysctl.conf
     <add the following lines at the  bottom of file>
     fs.aio-max-nr = 1048576
     fs.file-max = 6815744
     kernel.shmall = 2147483648
     kernel.shmmax =  12640366592
     kernel.shmmni = 4096
     kernel.sem = 250 32000 100 128
     net.ipv4.ip_local_port_range = 9000  65500
     net.core.rmem_default = 262144
     net.core.rmem_max = 4194304
     net.core.wmem_default = 262144
     net.core.wmem_max = 1048586
 
使用下面的命令检查是否修改已生效
     
     # /sbin/sysctl -p
     # /sbin/sysctl -a

遇到swap size的提醒，可以选择ignore（忽略）


至此，数据库安装完毕。下面我们进行测试与验证。

打开浏览器，输入网址https://r2021x.mydomain.com:5500/em
输入用户名system，密码Qwerty12345
 
使用lsnrctl status命令验证
 
使用sqlplus命令验证
 
密码永不过期的设置：

     $ sqlplus system/system_pwd@MYDB
     SQL> ALTER PROFILE DEFAULT LIMIT PASSWORD_LIFE_TIME UNLIMITED;
     SQL> exit

## Httpd服务的配置

在第6步中已经安装过httpd的rpm文件，因此可以直接进行配置和启动等操作。

     # systemctl enable httpd
     # systemctl start httpd
     # systemctl status httpd
     # chkconfig httpd on
     
     # cd /etc/httpd/conf
     # vi httpd.conf
 
在下面这行添加#号  (line#353)

     #IncludeOptional conf.d/*.conf
     
保存并重启httpd

     # systemctl restart httpd

测试页面

## 安装AdoptOpenJDK

AdoptOpenJDK JDK 11.0.6 with OpenJ9 is a Qualified Platform
官网下载https://adoptopenjdk.net/archive.html?variant=openjdk11&jvmVariant=openj9
解压缩：OpenJDK11U-jdk_x64_linux_openj9_11.0.6_10_openj9-0.18.1.tar.gz

     $ cd /app
     $ mkdir openjdk
     $ cd openjdk
     $ tar xvfz /tmp/OpenJDK11U-jdk_x64_linux_openj9_11.0.6_10_openj9-0.18.1.tar.gz
 
 编辑环境变量文件，添加在exportPATH之后
     $ vi  ~/.bash_profile
 
     export JAVA_HOME=/app/openjdk/jdk-11.0.6+10
     export PATH=$JAVA_HOME/bin:$PATH

## 配置License文件
使用root操作

     # cd /var
     # mkdir -p DassaultSystemes/Licenses
     # cd DassaultSystemes/Licenses
     # vi DSLicSrv.txt

<填写DSLS Server(s)>
例如:

     mydslsserver:4085

## 生成证书

     cp /etc/pki/tls/openssl.cnf to /etc/pki/tls/openssl_ca.cnf
     
     编辑 /etc/pki/tls/openssl_ca.cnf (line#42, 48,50, 55, 66)  
     (#42) dir  = /etc/httpd/conf/ssl     #  Where everything is kept     
     (#48) new_certs_dir =  $dir/       # default place  for new certs.     
     (#50) certificate=  $dir/MyRootCA.crt      # The CA  certificate     
     (#55) private_key  =  $dir/MyRootCA.key # The private key    
     (#66:remove “#”) copy_extensions = copy

在/etc/httpd/conf/ssl下面，手动创建两个文件
a. 运行命令touch index.txt
b. 运行命令touch serial，然后编辑文件，添加一行，内容为: 01

     cp /etc/pki/tls/openssl.cnf to /etc/pki/tls/openssl_server.cnf
 
编辑  /etc/pki/tls/openssl_server.cnf (line#127, 225, 351)

     (#127:remove “#”) req_extensions = v3_req # The extensions to add to  a certificate request
     (#225:add the black lines)
     …
     basicConstraints = CA:FALSE
     keyUsage = nonRepudiation, digitalSignature, keyEncipherment
     subjectAltName = @alt_names
     [ alt_names ]
     DNS.1 = r2021x
     DNS.2 = r2021x.mydomain.com
     [ v3_ca ]
     


使用root操作
     # export OPENSSL_CONF=/etc/pki/tls/openssl_ca.cnf
     # cd /etc/httpd/conf
     # mkdir ssl
     # cd ssl

     # openssl req-new -x509 -sha256 -nodes -days 3650 -newkeyrsa:4096 -keyoutMyRootCA.key-out MyRootCA.crt-passinpass:Qwerty12345-subj "/C=JP/ST=BEIJING/L=BEIJING/O=DS/OU=CS/CN=MYROOTCA"


在/etc/httpd/conf/ssl下面，手动创建两个文件
a. 运行命令touch index.txt
b. 运行命令touch serial，然后编辑文件，添加一行，内容为: 01

     # export OPENSSL_CONF=/etc/pki/tls/openssl_server.cnf
     openssl req -new -sha256 -nodes -days 3560 -newkey rsa:2048 -keyout r2021x.key -out r2021x.csr -subj "/C=JP/ST=BEIJING/L=BEIJING/O=DS/OU=CS/CN=r2021x.mydomain.com"

     openssl ca -config /etc/pki/tls/openssl_ca.cnf -policy policy_anything -extensions usr_cert -out r2021x.crt -infiles r2021x.csr

     Enter y
     Enter y

     openssl.exe x509 -noout -text -in r2021x.crt
     
     openssl rsa -in MyRootCA.key -out untrusted.key -passin pass:Qwerty12345
     openssl req -new -key untrusted.key -out untrusted.csr  -subj "/C=CN/ST=BEIJING/L=BEIJING/O=DS/OU=CS/CN=untrusted.mydomain.com"
     openssl x509 -sha256 -req -in untrusted.csr -CA MyRootCA.crt  -CAkey MyRootCA.key -CAcreateserial -out untrusted.crt -days 3650  -passin pass:Qwerty12345
     openssl x509 -noout -text -in untrusted.crt
     
     export JAVA_HOME=/app/openjdk/jdk-11.0.6+10
     export PATH=$JAVA_HOME/bin:$PATH
     
     keytool -import -cacerts -storepass changeit -alias MyRootCA -file  MyRootCA.crt -noprompt
     
黑色字体部分请替换成实际名称

## 安装证书
 

## 测试证书
使用root账号操作
 
     # cd /etc/httpd/conf
     # vi httpd.conf
<在文件末尾添加以下内容>
     <IfModule !ssl_module>
          LoadModule ssl_module modules/mod_ssl.so
     </IfModule>
     
     SSLRandomSeed startup builtin
     SSLRandomSeed connect builtin
     SSLCryptoDevice builtin
     
     <VirtualHost r2021x.mydomain.com:80>
          ServerName r2021x.mydomain.com
          DocumentRoot "/var/www/html"
     </VirtualHost>
 
Include conf/r2021x.conf
新建r2021x.conf文件 :
 
     # cd /etc/httpd/conf
     # vi r2021x.conf
     
     Add the following lines
     Listen 443
     <VirtualHost r2021x.mydomain.com:443>
          
          ServerName r2021x.mydomain.com
          ServerAlias r2021x
          
          ErrorLog logs/r2021x_error_log
          TransferLog logs/r2021x_access_log
          LogLevel warn
          SSLEngine on
          SSLProxyEngine on
          
          SSLCertificateFile conf/ssl/r2021x.crt
          SSLCertificateKeyFile conf/ssl/r2021x.key
          
          SetEnvIf User-Agent ".*MSIE.*" \
                         nokeepalive  ssl-unclean-shutdown \
                         downgrade-1.0  force-response-1.0
     
     </VirtualHost>
 
重启服务

     # systemctl restart  httpd

打开浏览器，输入网址测试，出现绿色或者黑色的锁头图标表示证书导入成功。
 
下面开始安装3D体验平台的第一个应用服务3DPassport

使用x3ds用户进行数据库的相关操作（不要使用root）

     $ dbstart $ORACLE_HOME
     $ sqlplus / as sysdba
     
     SQL> CREATE TABLESPACE x3dpassadmin_ts
          DATAFILE  '/app/oracle/oradata/MYDB/x3dpassadmin_ts01.dbf' SIZE 10M
          AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED
          EXTENT MANAGEMENT LOCAL
          SEGMENT SPACE MANAGEMENT AUTO;
     
     SQL> CREATE TABLESPACE x3dpasstokens_ts
          DATAFILE  '/app/oracle/oradata/MYDB/x3dpasstokens_ts01.DBF' SIZE 10M
          AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED
          EXTENT MANAGEMENT LOCAL
          SEGMENT SPACE MANAGEMENT AUTO;
     SQL> CREATE USER x3dpassadmin IDENTIFIED BY Qwerty12345;
     SQL> ALTER USER x3dpassadmin DEFAULT TABLESPACE x3dpassadmin_ts;
     SQL> GRANT CREATE PUBLIC SYNONYM TO x3dpassadmin;
     SQL> GRANT CREATE SEQUENCE TO x3dpassadmin;
     SQL> GRANT CREATE SESSION TO x3dpassadmin;
     SQL> GRANT CREATE SYNONYM TO x3dpassadmin;
     SQL> GRANT CREATE TABLE TO x3dpassadmin;
     SQL> GRANT DROP PUBLIC SYNONYM TO x3dpassadmin;
     SQL> GRANT UNLIMITED TABLESPACE TO x3dpassadmin;
     SQL> CREATE USER x3dpasstokens IDENTIFIED BY Qwerty12345;
     SQL> ALTER USER x3dpasstokens DEFAULT TABLESPACE x3dpasstokens_ts;
     SQL> GRANT CREATE PUBLIC SYNONYM TO x3dpasstokens;
     SQL> GRANT CREATE SEQUENCE TO x3dpasstokens;
     SQL> GRANT CREATE SESSION TO x3dpasstokens;
     SQL> GRANT CREATE SYNONYM TO x3dpasstokens;
     SQL> GRANT CREATE TABLE TO x3dpasstokens;
     SQL> GRANT DROP PUBLIC SYNONYM TO x3dpasstokens;
     SQL> GRANT UNLIMITED TABLESPACE TO x3dpasstokens;
 

从V6R2021x.AM_3DEXP_Platform.AllOS.3-10.iso文件中找到3DPassport/Linux64/1/，运行StartGUI.sh
例如:
     $ cd /tmp/installer/V6R2021x_GA/3DPassport/Linux64/1
     $ ./StartGUI.sh
     
 
自定义一个密码（如：Qwerty12345）
 
 
 
 
安装完毕。

23.用root编辑r2021x.conf文件

     # cd /etc/httpd/conf
     # vi r2021x.conf

文件末尾，</VirtualHost>之前，添加一行
     Include /app/DassaultSystemes/R2021x/3DPassport/linux_a64/templates/3DPassport_httpd_fragment.conf
 
 
 
重启http服务

     #systemctl restart httpd
 
如果httpd启动不成功，请检查3DPassport_httpd_fragment.conf文件，将setifempty改为set
     …
     SetEnvIf Origin "^http(s)?:\/\/(.+\.)?(mydomain.com)(:\d{1,5})?$"  origin_is=$0
     Header set Access-Control-Allow-Origin %{origin_is}e  env=origin_is
     Header set Access-Control-Allow-Credentials "true"
     Header set Access-Control-Allow-Methods "GET, POST,  OPTIONS, HEAD, PUT, DELETE, PATCH"
     Header set Access-Control-Allow-Headers  "accept,x-requested-method,origin,x-requested-with,x-request,cache-control,content-type,X-DS-IAM-CSRFTOKEN"
     Header set Access-Control-Expose-Headers  "X-DS-IAM-CSRFTOKEN"
     Header set Access-Control-Max-Age "600“
     …
## 测试3DPssport服务
 
输入前面定义的管理员admin_platform密码（如：Qwerty12345）
 