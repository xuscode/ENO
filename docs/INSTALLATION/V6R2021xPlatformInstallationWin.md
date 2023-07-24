
# V6R2021x Platform Installation
-----------------

## hostname
-----------------
v6r2021x.3ds.com

## host 
-----------------
127.0.0.1	v6r2021x.3ds.com
127.0.0.1	untrusted.v6r2021x.3ds.com

## database password
-----------------
Qwer1234

## add to oracle lisener 
-----------------
    (SID_DESC =
      (GLOBAL_DBNAME = ORCL)
      (ORACLE_HOME = C:\app\oracle\product\12.2.0\dbhome_1)
      (SID_NAME = ORCL)
    ) 
	
  C:\app\oracle\product\12.2.0\dbhome_1\NETWORK\ADMIN\listener.ora
  C:\app\oracle\product\12.2.0\dbhome_1\network\admin\tnsnames.ora
	
## JAVA 
-----------------
[download link](https://developer.ibm.com/languages/java/semeru-runtimes/downloads/)

    JAVA_HOME = C:\Java\Jdk
    JRE_HOME = C:\Java\Jre

## Apache24 
-----------------
[download link](https://www.apachehaus.com/cgi-bin/download.plx)

C:\Apache24\bin\httpd.exe -k install

    Apache HTTP Server 2.4.29 is a Validated Platform as a reverse proxy. Here is the list of required modules

    mod_authz_core.so
    mod_cache.so
    mod_cache_disk.so
    mod_deflate.so
    mod_filter.so
    mod_headers.so
    mod_log_config.so
    mod_proxy.so
    mod_proxy_http.so
    mod_proxy_wstunnel.so
    mod_rewrite.so
    mod_setenvif.so
    mod_socache_shmcb.so
    mod_ssl.so
    mod_slotmem_shm.so
    mod_alias.so
    mod_authz_host.so
    mod_dir.so
    mod_mime.so
    Apache HTTP Server 2.4.x, with x>29, is a Compatible Platform

    Apache HTTPD 2.4.39 version has a defect which affects the file upload request. See, https://bz.apache.org/bugzilla/show_bug.cgi?id=63325

    Workaround:

    Set the default RequestReadTimeout handshake=0 header=20-40,MinRate=500 body=20,MinRate=500 in httpd.conf.
    Reload.

## connect to sql 
-----------------
sqlplus / as sysdba

@ALL.sql

Qwer1234


## tomee port
-----------------

    APP_Name					Server Name				ShutdownPort	HTTPPort		AJPPort		RedirectPort	SSL_PORT		URL
    TomEE-3DPassport			3dpassport				8005			8080			8009		8443			443				https://v6r2021x.3ds.com/3dpassport
    TomEE-3DDashboard			3ddashboard				8105			8180			8109		8444			443				https://v6r2021x.3ds.com/3ddashboard
    TomEE-3DSearch				Federated_Search		8205			8280			8209		8453			443	
    TomEE-3DSpace				3dspace_CAS				8305			8380			8309		9443			443	
    TomEE-3DSpaceNoCAS			3dspace_NoCAS			8405			8480			8409		9444			443	
    TomEE-CentralFCS			Central_FCS				8505			8580			8509		9445			443	
    TomEE-RemoteFCS				Remote_FCS				8605			8680			8609		9446			443	
    TomEE-3DSywm				3DSwym					8705			8780			8709		9447			444	
    TomEE-3DNotification		3DNotification			8805			8880			8809		9448			446	
    TomEE-3DComment				3DComment				8905			8980			8909		9449			446	

## 3DPASSPORT  
-----------------
8080
8081
8082

//v6r2021x.3ds.com:1521/orcl
https://v6r2021x.3ds.com:443/3dpassport
https://v6r2021x.3ds.com:443/3dspace

x3dpassadmin
x3dpasstokens

admin_platform@3ds.com
Qwer1234

## 3DDASHBOARD  
-----------------
http
8083
ajp
8084
shutdown
8085

//v6r2021x.3ds.com:1521/orcl

x3ddashadmin

https://v6r2021x.3ds.com:443/3dpassport
https://v6r2021x.3ds.com:443/3ddashboard
https://v6r2021x.3ds.com:443/3dspace
https://v6r2021x.3ds.com:443/3dspace

untrusted.v6r2021x.3ds.com

admin_platform@3ds.com


## 3DSEARCH  
-----------------
8086


https://v6r2021x.3ds.com:443/3dpassport
https://v6r2021x.3ds.com:443/federated
https://v6r2021x.3ds.com:443/3dspace
https://v6r2021x.3ds.com:444/3dswym

https://v6r2021x.3ds.com/federated/search?query=test

## FULL TEXT SEARCH  

http://v6r2021x.3ds.com:19000

http://v6r2021x.3ds.com:19001/admin/


## 3DSPACE  

spaceuser

//v6r2021x.3ds.com:1521/orcl

space_data_ts
space_index_ts

https://v6r2021x.3ds.com:443/3dpassport
http://v6r2021x.3ds.com:19000
https://v6r2021x.3ds.com:443/federated
https://v6r2021x.3ds.com:443/3ddashboard
https://v6r2021x.3ds.com:443/3dspace

https://v6r2021x.3ds.com:444/3dswym

https://v6r2021x.3ds.com:443/enoviav5
https://v6r2021x.3ds.com:446/3dcomment
https://v6r2021x.3ds.com:446/3dnotification


v6r2021x.3ds.com
admin_platform@3ds.com
9080

-----------------
    Files will be installed in the following directory:
      C:\DassaultSystemes\R2020x\3DSpace
    Java Development Kit (JDK) path: C:\Java\jdk
    Database type: Oracle
    The directory of tnsnames.ora: 
    Oracle Connection User Name: spaceuser
    Oracle Instance Name: //v6r2021x.3ds.com:1521/orcl
    Default and Administration data tablespace: space_data_ts
    Default and Administration index tablespace: space_index_ts
    Directory for files storage: C:\DassaultSystemes\3DSpaceData
    Database will be updated
    Data table space for eService Production vault: space_data_ts
    Index table space for eService Production vault: space_index_ts
    Data table space for vplm vaults: space_data_ts
    Index table space for vplm vaults: space_index_ts
    3DPassport service URL: https://v6r2021x.3ds.com:443/3dpassport
    3DSpace Full Text Search configuration URL: http://v6r2021x.3ds.com:19000
    3DSearch service URL: https://v6r2021x.3ds.com:443/federated
    3DDashboard service URL: https://v6r2021x.3ds.com:443/3ddashboard
    3DSpace service URL: https://v6r2021x.3ds.com:443/3dspace
    3DSwym service URL: https://v6r2021x.3ds.com:444/3dswym
    ENOVIA VPM V5 service URL: https://v6r2021x.3ds.com:443/enoviav5
    3DComment service URL: https://v6r2021x.3ds.com:446/3dcomment
    3DNotification service URL: https://v6r2021x.3ds.com:446/3dnotification
    Mail server name: v6r2021x.3ds.com
    Mail sender name: admin_platform@3ds.com
    Build the application: Yes
    Install the embedded Apache TomEE+ and deploy the application: Yes
    Java Heap Size: Medium Java heap size 2048m
    The embedded Apache TomEE+ will be installed.
      Apache TomEE+ connection port: 9080
    Full Text Search configuration steps: Yes
    Create Tools entries in Start Menu: Yes
    Create Shortcuts on the Desktop: Yes

-----------------
    Files will be installed in the following directory:
      C:\DassaultSystemes\R2020x\3DSpace
    Java Development Kit (JDK) path: C:\Java\jdk
    Database type: Oracle
    The directory of tnsnames.ora: 
    Oracle Connection User Name: spaceuser
    Oracle Instance Name: //v6r2021x.3ds.com:1521/orcl
    Default and Administration data tablespace: space_data_ts
    Default and Administration index tablespace: space_index_ts
    Directory for files storage: C:\DassaultSystemes\3DSpaceData
    Database will be updated
    Data table space for eService Production vault: space_data_ts
    Index table space for eService Production vault: space_index_ts
    Data table space for vplm vaults: space_data_ts
    Index table space for vplm vaults: space_index_ts
    3DPassport service URL: https://v6r2021x.3ds.com:443/3dpassport
    3DSpace Full Text Search configuration URL: http://v6r2021x.3ds.com:19000
    3DSearch service URL: https://v6r2021x.3ds.com:443/federated
    3DDashboard service URL: https://v6r2021x.3ds.com:443/3ddashboard
    3DSpace service URL: https://v6r2021x.3ds.com:443/3dspace
    3DSwym service URL: https://v6r2021x.3ds.com:444/3dswym
    ENOVIA VPM V5 service URL: 
    3DComment service URL: https://v6r2021x.3ds.com:446/3dcomment
    3DNotification service URL: https://v6r2021x.3ds.com:446/3dnotification
    Mail server name: v6r2021x.3ds.com
    Mail sender name: admin_platform@3dspace.3ds.com
    Build the application: Yes
    Install the embedded Apache TomEE+ and deploy the application: Yes
    Java Heap Size: Medium Java heap size 2048m
    The embedded Apache TomEE+ will be installed.
      Apache TomEE+ connection port: 8380
    Full Text Search configuration steps: Yes
    Create Tools entries in Start Menu: Yes
    Create Shortcuts on the Desktop: Yes

-----------------
    set SERVICE_NAME=TomEE
    set PR_DISPLAYNAME=Apache TomEE
    set "PR_DESCRIPTION=3DEXPERIENCE_3Dpassport"

    3DEXPERIENCE__3DPassport
    3DEXPERIENCE__3DDashboard
    3DEXPERIENCE__3DSearch
    3DEXPERIENCE__3DSpace
    3DEXPERIENCE__3DSpaceNoCAS
    3DEXPERIENCE__3DNotification
    3DEXPERIENCE__3DComment
    3DEXPERIENCE__3DSwym

-----------------

    请执行以下脚本完成在 3DPassport 中注册 3DSpace：
    <server>/<os>/code/command/3DSpaceRegistrationIn3DPassport.[sh|bat]
    运行此脚本之前，确保 3DPassport 已在运行。

## 3DSPACE MQL  
-----------------
    A manual step is required after this hot fix installation.
    The following MQL command must be executed (it may take several minutes).
    Start a MQL command window from <server> installation and type this: 
      MQL>set context person creator;
      MQL>exec prog VPLMDataMigration;


-----------------

    Files will be installed in the following directory:
      C:\DassaultSystemes\R2018x\3DSwym
    Selected Components: 
      3DSwym Foundation
      3DSwym Video Converter
      3DSwym Index

  
