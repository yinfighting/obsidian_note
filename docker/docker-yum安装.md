### 1、安装环境

此处在Centos7进行安装，可以使用以下命令查看CentOS版本

lsb_release -a

![](https://img2018.cnblogs.com/blog/761230/201909/761230-20190920092034990-377974794.png)

在 CentOS 7安装docker要求系统为64位、系统内核版本为 3.10 以上，可以使用以下命令查看

uname -r

![](https://img2018.cnblogs.com/blog/761230/201909/761230-20190920092306272-1825494524.png)

### 2、用yum源安装

**2.1 查看是否已安装docker列表**

yum list installed | grep docker

![](https://img2018.cnblogs.com/blog/761230/201909/761230-20190924101015120-484595522.png)

**2.2 安装docker**

yum -y install docker

-y表示不询问安装，直到安装成功，安装完后再次查看安装列表

![](https://img2018.cnblogs.com/blog/761230/201909/761230-20190924101635249-774913670.png)

[[docker配置镜像]]

**2.3 启动docker**

systemctl start docker
重启 : systemctl daemon-reload && systemctl restart docker

**2.4 查看docker服务状态**

systemctl status docker

![](https://img2018.cnblogs.com/blog/761230/201909/761230-20190924101735498-1013963263.png)

以上说明docker安装成功

[[dcoker run运行流程]]