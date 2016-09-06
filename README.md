# my-wnmp-runtime
配置windows下WNMP环境的步骤

下载：

nginx

http://nginx.org/en/download.html

php

http://windows.php.net/download#php-5.6

install windows service 

https://github.com/kohsuke/winsw

winsw.exe install/uninstall/start/stop/stutas

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

```conf
        location ~ \.php(.*)$  {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_split_path_info  ^((?U).+\.php)(/?.+)$;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            fastcgi_param  PATH_INFO  $fastcgi_path_info;
            fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_path_info;
            include        fastcgi_params;
        }

```
