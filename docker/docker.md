
#### 常用命令
- Docker
    - 内核虚拟化技术
    - 提供一致性环境
     -提供弹性云服务
    - 组建微服务架构
- 获取镜像
    - docker pull hub.c.163.com/public/nginx:1.2.1
- 查看镜像
    - docker images 
- 删除镜像
    - docker rmi IMAGE_NAME
    - 删除所有镜像 docker rmi `docker images  -q`
- 创建镜像
    - docker build -t mysql:5.6 /tmp/dockerfile/
---
- 启动容器
    - docker run --name mysql -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=testdb -v /home/data/mysql:/var/lib/mysql hub.c.163.com/library/mysql:5.6
        - -d 让容器在后台运行
        - -p 添加主机到容器的端口映射
        - -v 添加目录映射，即主机上的/home/data/mysql和容器中/var/www/html目录是同步的
        - –name 容器的名字
        - –link 与另外一个容器建立起联系，这样我们就可以在当前容器中去使用另一个容器里的服务。
        - -e 设置环境变量，这里是设置mysql的root用户的初始密码，这个必须设置 
- 开启容器
    - docker start CONTAINER-ID
- 停止容器
    - docker stop CONTAINER-ID
    - 停止运行所有容器 docker stop `docker ps -a -q`
- 删除容器
    - docker rm -f  CONTAINER-ID
        - -f 删除并关闭
    - docker rm docker ps -a -q
        - -a 标志列出所有容器
        - -q 标志只列出容器的ID，然后传递给rm命令，依次删除容器。
- 进入容器
    - docker exec it CONTAINER-ID bash
        - -t 在容器里生产一个伪终端
        - -i 对容器内的标准输入 (STDIN) 进行交互
- 查询容器
    - docker ps -a
---

#### Docker Compose 

- 简介 负责快速在集群中部署分布式应用
- 安装
    - `sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
    - sudo chmod +x /usr/local/bin/docker-compose
    - docker-compose --version
- 卸载
    - sudo rm /usr/local/bin/docker-compose
    - pip uninstall docker-compose
- 运行
    - docker-compose up 
        - -d 让容器在后台运行 
- 查看
    - docker-compose ps #查看当前正在运行中的容器
- 停止
    - docker-compose stop [container name]# 停止正在运行的容器，如果不写容器名称则停止所有
- 启动
    - docker-compose start [container name]# 启动被停止的容器，参数说明同上
- 重启
    - docker-compose restart [container name] # 重启容器，参数说明同上