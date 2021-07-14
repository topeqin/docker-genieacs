# Docker-gogs
https://hub.docker.com/r/gogs/gogs
https://github.com/gogs/gogs/tree/main/docker

```bash
1. install mysql and add db naming gogs for Gogs service usage 
docker pull mysql:5.7 (gogs required the version greater or equal 5.7)
docker run -di --name=mymysql -p 13306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:5.7
docker exec -it mymysql /bin/bash
mysql -uroot -p123456
> show databases;
> create database gogs;
2. install the gogs based its official image
 2.1 docker pull gogs
 2.2 sudo mkdir /projects/gogs or /var/gogs
 2.3 docker run --name mygogs -p 10022:22 -p 3001:3000 -v /projects/gogs:/data gogs/gogs
 2.4 Access http://IP:3001 and configure the mysql ssh domain and so on
     pay attention the exposed host port and your server IP address, after successfully configure, you can start gogs service
 2.5 docker start mygogs


### ToDo
### compose service with mysql or postgresql

