ubuntu下用的环境配置

## nginx:

`sudo apt-get install nginx`

## mysql:

### 安装
`sudo apt-get install mysql-server`

### 修改my.conf (可能在/etc/mysql/mysql.conf.d/mysqld.cnf)
```
[mysqld]
default-storage-engine=INNODB
character-set-server=utf8
collation-server=utf8_general_ci
```

### 设置用户允许远程连接

my.conf里面bind-address从127.0.0.1改为0.0.0.0
```
mysql -uroot -proot

use mysql;

update `user` set `host`='%' where `user`='root';

flush privileges;
```

| 记得重启mysql哦

## redis:

`sudo apt-get install redis-server`


## php：
``` 
sudo apt-get purge `dpkg -l | grep php| awk '{print $2}' |tr "\n" " "`
```

`sudo add-apt-repository ppa:ondrej/php`

`sudo apt-get update`

`sudo apt-get install php5.6-cli php5.6-fpm php5.6-dev php5.6-curl php5.6-gd php5.6-mysql php5.6-json php5.6-mcrypt php5.6-readline php5.6-bcmath php5.6-mbstring php5.6-zip`
