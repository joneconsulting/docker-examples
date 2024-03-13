#### Service Rolling Updates
````
$ docker service create --name mynginx1 --replicas 3 nginx:latest

$ docker service update --image nginx:1.10 mynginx1

$ docker service create --replicas 2 --name mynginx2 --update-delay 10s \ 
--update-parallelism 2 nginx:1.24 
````

#### Docker Save / Load (이미지)
````
$ docker save -o 파일명.tar nginx:latest

$ docker load -i 파일명.tar
````

#### Docker Export / Import (컨테이너)
````
$ docker export 컨테이너ID > 파일명.tar

$ docker import 파일명.tar > 이미지명:태그명
````

#### Docker Commit
````
$ docker commit 컨테이너명 이미지명:테그명
````

#### Docker Swarm Rollback
````
$ docker service create --name myngnix \
      --replicas 2 --rollback-delay 10s --rollback-parallelism 1 \
      --rollback-failure-action pause ngnix:1.10

$ docker service inspect redis --pretty

$ docker service update --image ngnix:1.24 mynginx

$ docker service update --rollback mynginx
````

