
    docker run hello-word

**run运行流程图**
![[clipboard.png]]

**底层原理: docker是怎么样工作的?**

>docker 是一个client-server结构的系统，Docker的守护进程运行在主机上，通过Socket从客户端访问
>dockerServer接收到docker-client的指令，就会执行这个命令！
>![[docker结构.png]]