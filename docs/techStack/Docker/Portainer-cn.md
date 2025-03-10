---
title: Portainer 中文CE
---

### 镜像
[**portainer-ce仓库地址**](https://hub.docker.com/r/6053537/portainer-ce)

### 用法（Docker Compose）
``` yaml
services:
  portainer:
      container_name: portainer
      network_mode: bridge
      image: 6053537/portainer-ce:latest
      # image: hub-mirror.c.163.com/6053537/portainer-ce #推荐国内服务器或nas用，需要请用#注释上一行
      ports:
        - 9000:9000
#        - 8000:8000
#        - 9443:9443
      volumes:
        - portainer_data:/data
        - /var/run/docker.sock:/var/run/docker.sock
      restart: unless-stopped
volumes:
  portainer_data:
```