# Nginx + php-fpm + mysql - Official



### mySQL : Official

| Official image | 8.0.13, 8.0, 8, latest (8.0/Dockerfile) |
| -------------- | --------------------------------------- |
| Port           | 8082:3306                               |

- 이전 방식의 mysql_native_password로 변경

/etc/mysql/my.cnf

```c
[mysqld]
default-authentication-plugin=mysql_native_password
```

```mysql
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
or 
mysql> ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
```

- 변경사항 적용

```mysql
mysql> FLUSH PRIVILEGES;
```





### Nginx : Official

| Official image | 1.15.6-alpine, mainline-alpine, 1-alpine, 1.15-alpine, alpine (mainline/alpine/Dockerfile) |
| -------------- | ------------------------------------------------------------ |
| Port           | 8080:80                                                      |

- default.conf

```bash
$ vi /etc/nginx/conf.d/default.conf
```





### PHP : Dockerfile

| Official image | 7.2.12-fpm-alpine3.8, 7.2-fpm-alpine3.8, 7-fpm-alpine3.8, fpm-alpine3.8, 7.2.12-fpm-alpine, 7.2-fpm-alpine, 7-fpm-alpine, fpm-alpine (7.2/alpine3.8/fpm/Dockerfile) |
| -------------- | ------------------------------------------------------------ |
| Port           | 9000                                                         |

php.ini

```bash
$ cd /usr/local/bin/php
```

mysql pod install by docker-php-ext-install

```bash
$ cd /usr/local/bin/
$ docker-php-ext-install -j$(nproc) mysqli
$ docker-php-ext-install -j$(nproc) pdo
$ docker-php-ext-install -j$(nproc) pdo_mysql
```

docker-php-ext-install

```bash
$ cd /usr/local/bin/php
```

