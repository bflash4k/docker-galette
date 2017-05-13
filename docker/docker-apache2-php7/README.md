## Apache2 and php7 on Ubuntu 16.04 LTS (aka xenial)

This is docker images of Ubuntu LTS versions with apache2 and php7

To access site contents from utside the container you should map /var/www/

### Build

```bash
$ docker build -t bflash4k/apache2-php7 .
```

### Examples

- plain, accessable on port 8080 `docker run -d -p 8080:80 bflash4k/apache2-php7`
- with external contents in /home/bflash4k/html `docker run -d -p 8080:80 -v /home/bflash4k/html:/var/www/html bflash4k/apache2-php7`

The docker container is started with the -d flag so it will run in the background. To run commands or edit settings inside
the container run `docker exec -ti <container id> /bin/bash'


