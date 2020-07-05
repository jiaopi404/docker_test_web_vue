<!--
 * @Author: your name
 * @Date: 2020-07-05 17:07:16
 * @LastEditTime: 2020-07-05 21:56:42
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /docker_vue_demo_001/README.md
--> 
# docker_vue_demo_001

## 1. 安装 docker

[docker-desktop](https://www.docker.com/products/docker-desktop)

## 2. 构建 docker 镜像

1. 构建项目: `npm run build` 或 `yarn build`

2. 构建镜像: `docker build -f ./docker/docker-file -t jiaopi404/docker-vue-test:001 .`

- `-f` 文件位置
- `-t` docker 的 tag, docker hub 的 镜像 存放位置 docker.io/username/docker_name:tag_name, 因此构建时附带 username 方便推送到自己的仓库
- `.` 镜像存放位置

## 3. 推送到 仓库

1. 登录: `docker login`

2. push 到仓库: `docker push jiaopi404/docker-vue-test:001`


## 4. 云服务器拉取镜像

1. 登录: `docker login`

2. 从仓库拉取: `docker pull jiaopi404/docker-vue-test:001`

## 5. 云服务器构建 `docker-compose.yml` 文件

`122.51.**.***` 为例

- 目录: `~/docker_file_web_vue_001/docker-compose.yml`

```docker
version: '2' # 2 表示 docker-compose 版本, 云服务器 1.25.2, 因此使用 version: '2'
services: # 构建的服务
  web: # 自定义服务名
    image: docker.io/jiaopi404/docker-vue-test:001 # 镜像名字
    ports: # 开启的端口
        - '8050:80' # 云服务器主机 映射 到容器 80 端口
```

## 6. 运行容器

1. 当前目录: `~/docker_file_web_vue_001`

2. 命令: `docker-compose up -d`

- `-d` 后台运行
