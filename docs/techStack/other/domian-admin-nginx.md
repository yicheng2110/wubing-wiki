---
title: Domain-Admin 自动部署 Nginx Config
---

### 域名校验

服务器目录: `/var/www/challenges/`

Nginx配置文件: 
``` nginx
server {
  listen 80;
  server_name xxx.xxx.com;
  
  location /.well-known/acme-challenge/ {
      alias ./challenges/;
      try_files $uri = 404;
  }
}
```

**Nginx**重启命令: `docker exec nginx nginx -c reload`

