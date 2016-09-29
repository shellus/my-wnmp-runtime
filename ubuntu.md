ubuntu下用的环境配置

## nginx:

`sudo apt-get install nginx`

## mysql:

`sudo apt-get install mysql-server`

## redis:

`sudo apt-get install redis-server`


## php：
``` 
sudo apt-get purge `dpkg -l | grep php| awk '{print $2}' |tr "\n" " "`
```

`sudo add-apt-repository ppa:ondrej/php`

`sudo apt-get update`

`sudo apt-get install php5.6-cli php5.6-fpm php5.6-dev php5.6-curl php5.6-gd php5.6-mysql php5.6-json php5.6-mcrypt php5.6-readline php5.6-bcmath php5.6-mbstring php5.6-zip`
