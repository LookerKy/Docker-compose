# Docker Mariadb utf8 character set

## 선행 사항

### docker bash 접속

```bash
$ docker exec -it [container Id] bash
```

### 패키지 업데이트

```
apt-get update
```

### nano vim 설치

```
apt-get install nano vim
```

### utf8 설정

**[/etc/mysql/conf.d/utf8.cnf]**

```conf
[client] 
default-character-set = utf8 

[mysqld] 
init_connect = SET collation_connection = utf8_general_ci
init_connect = SET NAMES utf8
character-set-server = utf8
collation-server = utf8_general_ci

[mysqldump]
default-character-set = utf8

[mysql]
default-character-set = utf8
```
