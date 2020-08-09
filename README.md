# Ratings Service.

Ratings service is developed on PHP. PHP will not run on itself and it requires a web server.

Apache HTTPD server is more famous and this app is already provided by developer in HTTPD conifguration rather than NGINX. So we choose the same to install and configure the web server with PHP.

1. Install Apache HTTPD Web Server.

```
# yum install httpd -y 
# yum install  http://rpms.remirepo.net/enterprise/remi-release-7.rpm -y 
# yum -y install yum-utils
# yum-config-manager --enable remi-php73
# yum -y install php php-opcache php73-php-pdo composer
```

2. Change the port number of Apache Web Server to 7004.

Open the configuration file `/etc/httpd/conf/httpd.conf` and change the line `Listen 80` to `Listen 7004`.

3. Clone the code.

Clone with following settings.

User - `root`
Path: `/root`

4. Copy ratings config.

```
# cp /root/ratings/status.conf /etc/httpd/conf.d/
```

5. Copy the ratings static content.

```
# rm -rf /var/www/html
# cp -r /root/ratings/html /var/www/html
```

6. Install PHP dependencies.

```
# cd /var/www/html
# composer install
```

7. Start the HTTPD Service.

```
# systemctl enable httpd 
# systemctl start httpd
```


