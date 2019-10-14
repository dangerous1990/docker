[TOC]

# 一、下载docker文件
```
docker pull streamsets/datacollector:3.9.1
```

# 二、安装jdbcpackage
创建一个Dockerfile文件
```
ARG SDC_VERSION=3.9.1
FROM streamsets/datacollector:${SDC_VERSION}

ARG SDC_LIBS
RUN "${SDC_DIST}/bin/streamsets" stagelibs -install="${SDC_LIBS}"
```
重新build一个镜像
```
docker build -t yzh/datacollector:3.9.1 --build-arg SDC_VERSION=3.9.1 --build-arg SDC_LIBS=streamsets-datacollector-jdbc-lib .
```

# 三、添加mysql、clickhouse jdbc依赖jar包

https://github.com/dangerous1990/docker/tree/master/streamsets/lib  

jar包地址

# 四、docker
```
docker run -d -p 18630:18630  \
-v $PWD/lib:/opt/streamsets-datacollector-3.9.1/streamsets-libs-extras/streamsets-datacollector-jdbc-lib/lib/ \
-v $PWD/data:/data \
--name streamsets
yzh/datacollector:3.9.1
```

# 五、docker-compose
```
version: '2.1'
services:
    streamset:
        image: yzh/datacollector:3.9.1
        ports:
            - 18630:18630
        volumes:
            - ./data:/data
            - ./lib:/opt/streamsets-datacollector-3.9.1/streamsets-libs-extras/streamsets-datacollector-jdbc-lib/lib/
```
