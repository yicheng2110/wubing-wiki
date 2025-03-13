---
title: 设置Docker 使用网络代理
---

### 传统设置镜像地址

> `/etc/docker/daemon.json`

```json
{
    "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
```

### docker pull / docker push 方式
docker pull /push 的代理被 systemd 接管，所以需要设置 systemd…

```shell
# 创建目录
sudo mkdir -p /etc/systemd/system/docker.service.d
# 编写文件
sudo vim /etc/systemd/system/docker.service.d/http-proxy.conf
```

> `http-proxy.conf` 文件内容
```ini
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:7890"
Environment="HTTPS_PROXY=http://127.0.0.1:7890"
```

> 重启服务
```shell
sudo systemctl daemon-reload
sudo systemctl restart docker
```

### 设置 docker 全局代理

`~/.docker/config.json`文件编辑以下内容

```json
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://172.17.0.1:7890",
     "httpsProxy": "http://172.17.0.1:7890",
     "noProxy": "localhost,127.0.0.1,.daocloud.io"
   }
 }
}
```


