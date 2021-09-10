# Install Oracle as Docker Image

## Pre Processing
* Clone https://github.com/oracle/docker-images.
* Download the Oracle Database 19c binary LINUX.X64_193000_db_home.zip from http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html
* Put the zip in the `docker-images/OracleDatabase/SingleInstance/dockerfiles/19.3.0` directory. Do not unzip it.

## Build Docker Image
```sh
cd ./docker-images/OracleDatabase/SingleInstance/dockerfiles
./buildContainerImage.sh -v 19.3.0 -e
```
It will take a long time and will take 20 GB space

## First time run 
```
docker run \
--name oracle19c \
-p 1521:1521 \
-p 5500:5500 \
-e ORACLE_PDB=orcl \
-e ORACLE_PWD=password \
-v /opt/oracle/oradata \
-d \
oracle/database:19.3.0-ee
```

## Server Start and Stop 
```
docker start oracle19c
```
```
docker stop oracle19c
```