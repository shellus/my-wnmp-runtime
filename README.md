# my-wnmp-runtime
配置windows下WNMP环境的步骤

----

###下载：

- nginx

  http://nginx.org/en/download.html

- php

  http://windows.php.net/download#php-5.6

  注意从左边推荐链接下载对应的vc运行库

- mariadb

  https://downloads.mariadb.org/

- redis
  http://redis.io/download

- mongodb
  https://www.mongodb.com/download-center?jmp=nav#community

- install windows service 

  https://github.com/kohsuke/winsw

  usage: winsw.exe install/uninstall/start/stop/stutas

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<service>
  <id>php-cgi</id>
  <name>php-cgi</name>
  <description>php-cgi</description>
  <executable>php-cgi.exe</executable>
  <env name="HOME" value="C:\Program Files\php-5.6.25-nts-Win32-VC11-x64" />
  <logpath>C:\Program Files\php-5.6.25-nts-Win32-VC11-x64</logpath>
  <logmode>roll</logmode>
  <depend></depend>
  <startargument>-b127.0.0.1:9000 -c php.ini</startargument>
</service>

```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<service>
  <id>nginx</id>
  <name>nginx</name>
  <description>nginx</description>
  <logpath>C:\Program Files (x86)\nginx-1.11.3\</logpath>
  <logmode>roll</logmode>
  <env name="HOME" value="C:\Program Files (x86)\nginx-1.11.3\" />
  <executable>nginx.exe</executable>
  <startargument></startargument>
  <stopexecutable>nginx.exe -s stop</stopexecutable>
</service>

```

mongodb and redis-server 自带windows服务安装

### 使用
`sc <command> <service_name>`

example:

`sc start nginx`
  
