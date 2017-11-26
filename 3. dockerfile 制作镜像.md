第三章 docekrfile 制作镜像    
========    
  
1.关于dockerfile的名称    
----------     

创建一个文本文件名称无限制，在其内部编写    
  
2.dockerfile的内容格式和语法  
-------     
`FROM 【镜像名】`    
`MAINTAINER 【作者名】【<邮箱>】`    
`RUN 【命令】`    
`COPY 【本地配置文件相对路径】【镜像中的配置文件绝对路径】`  
  
3.dockerfile的执行命令  
----    
`docker build --tag 【作者名】/【原镜像名】：【版本：如latest】【位置：如.】`    
  
4.Docker的aliyun仓库的使用  
----    
从registry中拉取镜像：  
`$ sudo docker pull registry.cn-beijing.aliyuncs.com/georgeli/drupal:[镜像版本号]`  
将镜像推送到registry以北京的服务器为例：  
`$ sudo docker login --username=【你的阿里云账号】@aliyun.com registry.cn-beijing.aliyuncs.com`  
`$ sudo docker tag [ImageId] registry.cn-beijing.aliyuncs.com/【作者】/【项目名】:[镜像版本号]`  
`$ sudo docker push registry.cn-beijing.aliyuncs.com/georgeli/drupal:[镜像版本号]`  
  
5.sample:  
------     
使用docker tag重命名镜像，并将它通过私网ip推送至registry：  
`$ sudo docker images`  
REPOSITORY                                                         TAG                 IMAGE ID            CREATED             VIRTUAL SIZE  
registry.aliyuncs.com/acs/agent                                    0.7-dfb6816         37bb9c63c8b2        7 days ago          37.89 MB  
`$ sudo docker tag 37bb9c63c8b2 registry..aliyuncs.com/acs/agent:0.7-dfb6816`  
通过docker images 找到您的imageId 并对于改imageId重命名镜像domain到registry内网地址。  
`$ sudo docker push registry..aliyuncs.com/acs/agent`  
