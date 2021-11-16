## 帮助命令
```
docker version         		显示docker的版本信息
docker info					显示docker的系统信息，包括镜像和容器数量
docker --help				帮助命令
```

## 镜像命令
### 1. docker images         		 
查看所有本地的主机上的镜像
![[docker-images.png]]
###### 可选项
		-a 	列出所有的镜像
		-q	只显示镜像的id
	
### 2. docker search        &emsp;&emsp; 		搜索镜像
	eg： docker search mysql
###### 可选项
		-filter=STARS=3000		搜索出来的镜像就是STARS大于3000的

### 3. docker pull        &emsp;&emsp;&emsp;&emsp; 		下载镜像
	eg： docker pull mysql
###### 可选项
		：版本号		镜像名称：版本号

### 4. docker rmi         	&emsp;&emsp;&emsp;&emsp;	删除镜像
	eg： docker rmi -f e234234223432   		   删除指定的镜像ID
		 docekr rmi  45323453 234241  			删除多个
		 docker rmi -f $(docker images -aq)		删除全部的容器

## 容器命令
>  说明： 我们有了镜像才可以创建容器，
### 1. docker run [可选参数] image         		 
###### 参数说明
		-name=“name” 			容器名称，用来区分容器， 如tomcat1，tomcat2
		-d						后台方式运行
		-it						使用交互方式运行，进入容器查看内容
		-p						指定容器的端口 -p 8080：8080  主机端口：容器端口
				> -p  ip:主机端口：容器端口
				> -p  主机端口：容器端口（常用）
				> -p  容器端口
		-p						随机指定端口
###### 从容器中退回主机
		exit					容器停止退出
		ctrl+p+q				容器不停止退出
	
### 2. docker ps       &emsp;&emsp;&emsp;&emsp;  		查看运行中的容器
	eg： docker ps
###### 可选项
		-a						列出历世运行过的容器
		-n=?					显出最近创建的容器

### 3. docker rm  容器id   &emsp;&emsp;&emsp;&emsp; 		删除容器
	eg： docker rm 容器ID 删除指定的容器,不能删除正在运行的容器,如果强制rm -f
		 docker rm -f $(docker ps -aq)       删除所有的容器
	     docker ps -a -q|xargs docker rm     删除所有的容器
 >启动和停止容器的操作
	docker start 容器id 启动容器
	docker restart 容器id 重启容器
	docker stop 容器id 停止当前正在运行的容器
	docker kill 容器id 强制停止当前容器
### 4. docker logs  容器id   &emsp;&emsp;&emsp;&emsp; 		显示容器日志
	eg： docker logs -ft --tail 10 容器id 显示10行 
		 docker logs -ft 显示全部日志
 >查看容器中进程信息       &emsp;&emsp;&emsp;&emsp;&emsp;        docker top 容器id
 
 >查看镜像源数据		&emsp;&emsp;&emsp;&emsp;&emsp;   docker inspect 容器id
 
 >进入当前正在运行的容器
 >>我们通常容器都是使用后台方式运行的,需要进入容器,修改一些配置 
 >>方式一: docker exec -it 容器id /bin/bash 
 >>方式二: docker attach 容器id /bin/bash   //正在执行当前的代码 
 >>区别:
 >> exex: 进入容器后开启一个新的终端,可以在里面操作 
 >> attach: 进入容器正在执行的终端,不会启动新的进程
 
>从容器内拷贝文件到主机上
>```
>docker cp 容器id:容器内路径 主机路径 
>eg: docker cp 容器id:/home/test.java /home 
>-- 拷贝是一个手动过程,未来我们使用-v卷的技术,可以实现
>```

[[容器命令.png]]

