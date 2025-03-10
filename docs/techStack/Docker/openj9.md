---
title: OpenJ9 Docker镜像
---

### Docker Hub 地址

[**ibm-semeru-runtimes**](https://hub.docker.com/_/ibm-semeru-runtimes)

### 镜像选择
- JRE: `ibm-semeru-runtimes:open-17-jre`
- JDK: `ibm-semeru-runtimes:open-17-jdk`

### 基于 SpringBoot 的 DockerFile

```dockerfile
FROM ibm-semeru-runtimes:open-17-jre
ENV TZ=Asia/Shanghai

WORKDIR /app
# 注意打包后的jar名称
ADD application/target/app.jar /app/app.jar

EXPOSE 8089
# 这里配置了配置文件为 "deploy"
ENTRYPOINT ["java", "-jar", "app.jar", "--spring.profiles.active=deploy"]
```

