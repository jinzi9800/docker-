1.维护集群的命令  

2.查看集群服务器的列表：  
------    
`docker node ls`  

3.升级：  
------    
`docker service update 【镜像名】 -- image 【作者】/【镜像名】：【被命名的版本名】 --update-parallelism 【每次更新的镜像数量】 --update dalay 【间隔时间（如6s）】`  

4.创建集群  
------    
5.配置的领袖服务器  
------    
##登陆领袖服务器##    
>>生成领袖服务器  

`docker swarm init --listen-addr 【监听的地址和端口号】`  

>>命令检查是否创建成功  

`docker node ls`  

6.配置干事服务器  
--------     
##登陆干事服务器##  

>>生成干事服务器命令  

`docker swarm join --listen-addr 【本机端口号】【领袖服务器的地址和端口号】`  

>>登陆领袖服务器,检查是否创建干事服务器成功  

`使用命令docker node ls`  

7.创建协作用的overlay类型的网络  
-----    
`docker network create --driver overlay 【被创建网络名】`  

8.使用命令检查是否创建网络成功  
---    
`docker network ls`  

9.创建集群管理的可视化界面（可选）  
-----------    
`docker run -itd -p 【本地端口】:【容器端口】 -e host=【领袖服务器IP】-e port=【端口号】 -v 【本地docker.sock地址即/var/run/docker.sock】【容器docker.sock地址即/var/run/docker.sock】manomark/visualizer`  

10.使用集群  
---    
`docker service create --name 【容器名】 --network 【网络名】 -p 【服务器端口号】:【容器中的端口号】 --replicas 1 【镜像名】`  

11.查看服务是否被创建：  
---    
`docker service ls`  

12.查看服务的任务：  
---    
`docker service tasks 【容器名】`  

13.使用负载均衡：  
---    
`docker sevice scale 【容器名】=【整数（像让集群中复制出多少个容器服务访问的用户）】`  
