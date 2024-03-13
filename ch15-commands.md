#### 실습 용 Docker 서버 (Dind)
`docker run --privileged --name manager -itd -p 10022:22 -p 18080:8080 -p 18088:8088 -p 10080:80 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker:latest /usr/sbin/init`

#### Jenkins 실행 (Docker 기반)
`docker run -d -p 8888:8080 -p 50000:50000 --restart=on-failure --name jenkins-server2 jenkins/jenkins:lts-jdk11`
* OpenJDK 11.0.15 JAVA_HOME=/opt/java/openjdk

#### Docker build 
`docker build -t [docker hub 계정]/myweb:1.0 -f Dockerfile .`