# Docker-compose mariadb
## docker-compose.yml 설정

```yml
version: "3.7"

services:
  local_db:
    image: mariadb
    restart: always
    environment:
      MYSQL_USER: root
      MYSQL_PASSWORD: <userpassword>
      MYSQL_ROOT_PASSWORD: <userpassword>
      MYSQL_DATABASE: surpin_dev
    volumes:
      - ~/data/mariadb:/var/lib/mysql
    ports:
      - "33067:3306"
```

## 포트 포워딩
우리가 로컬에 mysql이나 mariadb를 설치하고 있다면 이미 기본적으로 설정된 port가 이미 사용하고 있다. mysql과 mariadb와 같은경우에는 3306이라는 포트를 사용하고 있음으로 도커에 설치할 mariadb는 컨테이너에서는 3306/tcp를 이용하지만, 호스트 port는 33067로 설정하여 localhost:33067로 들어오는 모든 트래픽은 도커컨테이너의 3306으로 전달된다.

도커의 명령어로 예를 들어보겠다

```
docker run -p <host port number>:<container port number>/<protoco> [IMAGE NAME] [OTHER OPTION]
```
파라미터의 의미
- host port number : 호스트 시스템에서 사용되는 포트 번호
- container port number : 컨테이너 내에서 사용되는 포트 번호
- protocol : 프로토콜 유형 -udp,tcp,stcp 등


---

## 실행

```bash
$ docker-compose up -d
```

## 참조 사이트 
 [docker-compose](https://velog.io/@melangyun/Docker-compose.yml-DB%EC%99%80-%EC%97%B0%EA%B2%B0)

[포트 포워딩](https://tttsss77.tistory.com/155)
