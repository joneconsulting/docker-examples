#### Docker Network 생성
`docker network create --driver bridge my-network`

#### Maridb Container 생성
`docker run -d -p 3306:3306 --network my-network --name my-mariadb -e MARIADB_ALLOW_EMPTY_ROOT_PASSWORD=true -e MARIADB_DATABASE=mydb mariadb:latest`

#### Backend Container 생성
- my-backend 디렉토리에서 Docker image 빌드
`docker build -t [docker-hub-계정]/my-backend:1.0 -f Dockerfile .`
- 실행1) `docker run -d -p 8088:8088 --network my-network --name my-backend [docker-hub-계정]/my-backend:1.0`
- 실행2) `docker run -d -p 8088:8088 --network my-network --name my-backend -e "spring.datasource.url=jdbc:mariadb://my-mariadb:3306/mydb" [docker-hub-계정]/my-backend:1.0`
