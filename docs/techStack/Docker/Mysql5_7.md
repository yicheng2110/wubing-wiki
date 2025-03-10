---
title: Mysql 5.7.44 最后一个mysql5.7
---

### 用法（Docker Compose）
``` yaml
version: '3.8'

services:
  mysql:
    image: mysql:5.7.44
    container_name: mysql5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: database
      MYSQL_USER: user
      MYSQL_PASSWORD: user_password
    volumes:
      - ./mysql:/var/lib/mysql
    ports:
      - "3306:3306"
    networks:
      - mysql-net

networks:
  mysql-net:
    driver: bridge
```

### 环境变量
> todo