### UnionFS（联合文件系统）
![[Pasted image 20211114220555.png]]



### docker镜像加载原理
> docker的镜像实际上由一层一层的文件系统组成，这种层级的文件系统是UnionFS

![[Pasted image 20211114220508.png]]

![[Pasted image 20211114220759.png]]


### docker分层理解
![[Pasted image 20211114221614.png]]

![[Pasted image 20211114221524.png]]

### commit镜像
如何提交一个自己的镜像
![[Pasted image 20211114222317.png]]