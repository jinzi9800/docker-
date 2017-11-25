第二章 docker容器的bash命令
==================
**1．创建容器**
--------------
`docker run【镜像名】`
**2．docker run的参数**
------------------
`--name【被命名的容器名】`    // 命名容器
`-i`     //让容器变成带交互的（全写就是--interactive）
`-t`     // 指定了编辑器（--tty），后面一般跟随/bin/bash
`-d`     // 让容器在后台运行 （--dettach）
**3．查看容器**
--------------
`docker ps -all`
**4．删除容器**
--------------
`docker rm`
`-v`  // 连数据盘和容器一起删除**
`docker rm -v 【容器名】`
**5．查看容器的日志**
--------------
`docker logs 【容器名or ID】`
**6．停止容器**
--------------
`docker stop 【容器名】`
**7．重启容器**
--------------
`docker restart 【容器名】`
**8．启动容器**
--------------
`docker start 【容器名】`
**9．创建Docker的数据盘data volumes**
--------------
`docker run -v 【主机上存储目录的位置】: 【容器中存储目录的绝对路径】 -i -t --name =【被创建容器名】 【镜像名】 bash`
**10．仅创建容器不运行的容器——数据容器**
--------------
`docker create -v 【主机上存储目录的位置】:【容器中存储目录的绝对路径】--name 【准备制作的数据容器名】【镜像名】`
**11．使用数据容器**
--------------
`docker create --volumes-from 【数据容器名】`
**12．查看docker没有使用的数据盘**
--------------
`docker volume ls -f dangling=true`
**13．查看docker的网络**
--------------
`docker network ls`
* `host` //和主机一样的网络，能够访问到主机就可以访问到host
`docker run -d --name 【被创建的容器名】 -net host【镜像名】` //创建容器并指定host端口
* `none` //完全隔离
`docker run -d --name 【被创建的容器名】 -net none【镜像名】` //创建容器并指定none端口
* `briage:` //桥接网络(默认属性:容器和主机的一座桥。可以被指定端口)
`docker run -d --name 【被创建的容器名】 【镜像名】` //创建容器并指定briage端口
**14．检查docker容器的网络**
--------------
`docker network inspect 【brige/none/host/某个链接名】`
**15．自定义网络**
--------------
`docker network create --driver 【网络类型: bridge、host、none】【被创建的网络名】等`
**16．把已经创建的网络放到指定的自定义网络里**
--------------
`docker network connnect 【连接到的网络名】【容器名】`
**17．把已经创建的网络从指定的自定义网络里移除掉**
--------------
`docker network disconnnect【连接到的网络名】【容器名】`
**18．设定端口号**
--------------
`docker run -d --name【被创建的镜像名】-p 【主机上的端口号】: 【镜像上的端口号】`
**19．公布容器上面的所有端口**
--------------
`docker run -d --name【被创建的镜像名】【-P/--publish-all】 【主机上的端口号】: 【镜像上的端口号】`
**20．登陆某一个已经创建的容器**
--------------
`docker exec -it 【已存在镜像名】bash`
**21．查看docker服务**
--------------
`docker service ls`
