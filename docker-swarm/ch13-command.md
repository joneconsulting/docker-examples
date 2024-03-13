#### Dind 에서 registry 사용 시 (manager, worker01, worker02)
- /etc/docker/daemon.json 파일에 아래 내용 추가
````
{

    "insecure-registries": ["registry:5000"]

}
````

#### Docker Swarm에서 Service 생성 (13-3)
````
$ manager> docker service create --replicas 1 --publish 80:80 --name nginx registry:5000/edowon0623/nginx:latest
$ manager> docker service ls 
$ manager> docker service scale nginx=3
$ manager> docker service ps nginx
$ manager> docker service rm nginx
````


#### Docker Swarm에서 Stack 생성
````
$ manager> docker network create --driver overlay my-overlay-network
$ manager> docker stack deploy -c /stack/stack_sample.yml nginx
$ manager> docker stack ls 
$ manager> docker stack services nginx 
$ manager> docker stack ps nginx
$ manager> docker service rm nginx
````


