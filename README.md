GALETTE 0.8.3.3
[Galette homepage] (http://galette.eu/)


1 : Build all Docker images
-----------------------------

In Dockers directory, run the commands : 
```bash
$ docker build -t bflash4k/apache2-php7 ./docker-apache2-php7/
$ docker build -t bflash4k/galette_app:0.8.3.3 ./docker-galette_app/
$ docker build -t bflash4k/galette_data ./docker-galette_data/
```
Two more images are downloaded from [Docker Hub] (http://hub.docker.com):

- mysql server 5.7 (from  https://hub.docker.com/r/mysql/mysql-server/
- phpmyadmin 4.7 (from  https://hub.docker.com/r/phpmyadmin/phpmyadmin/


2 : Modify docker-compose.yml
-----------------------------
By default, galette_app and galette_data are "Local volume". It means datas (app and db) are store inside a container. If you want (prefer), you can map these volumes to your own directories:

```yaml
svc_application:
    container_name: galette_app
    image: bflash4k/galette_app:0.8.3.3
    volumes:
        - /home/oguiter/Devel/Docker/OG1/app_galette/www:/var/www/html
        #- galette_app:/var/www/html
svc_data:
    container_name: galette_data
        image: bflash4k/galette_data
        volumes:
            - /home/oguiter/Devel/Docker/OG1/app_galette/Data:/var/lib/mysql
            # - galette_data:/var/lib/mysql
```

PHPMyAdmin : [127.0.0.1:8081](http://127.0.0.1:8081)

MySQL : [127.0.0.1:8082](http://127.0.0.1:8082)

3 : useful commands 
-----------------------------
In Galette directory:
```bash
$ docker-compose up -d
```
:exclamation: host name for database creation is "galette_mysql" :exclamation:

Bash access is possible with:
```bash
$ docker exec -ti $(docker ps |grep -i galette_www_php | awk "{print \$1}") /bin/bash
```


