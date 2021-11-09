Docker默认镜像为官方镜像，可以配置成国内加速器提高速度

　　登录阿里云控制台，搜索容器镜像服务获取到镜像加速服务地址

　　新建配置文件

1

`/etc/docker/daemon``.json`

 　　输入以下内容

`{`

 `"registry-mirrors"``: [``"镜像加速器地址"``]`

`}`

 　　PS：镜像加速器地址为获取到的地址，也可以是国内任意镜像加速器地址

　　重启docker服务即可

`sudo` `systemctl daemon-reload`

`sudo` `systemctl restart docker`

 　　PS：对Ubuntu和CentOS都适用