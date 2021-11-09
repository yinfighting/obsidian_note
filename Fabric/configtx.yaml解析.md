### configtx.yaml 这个核心配置文件用来做三件事：
1. 生成启动 Orderer 需要的创世块；
2. 创建应用通道的 配置交易文件；
3. 生成组织锚节点更新配置交易文件  ；

```yaml
## 一些列组织的定义，【被其他 部分引用】
##
## 【注意】：本文件中 &KEY 均为 *KEY 所引用； xx：&KEY 均为 <<: *KEY 所引用
##
Capabilities:   ##能力,解释没看懂??
	## 通道功能适用于orderers and the peers，并且必须得到两者的支持。 将功能的值设置为true.
	Channel: &ChannelCapabilities  
	  V1_3: true  
	## Orderer功能仅适用于orderers，可以安全地操纵，而无需担心升级peers。 将功能的值设置为true
	Orderer: &OrdererCapabilities  
	  V1_1: true
	## 应用程序功能仅适用于Peer 网络，可以安全地操作，而无需担心升级或更新orderers。 将功能的值设置为true
	Application: &ApplicationCapabilities  
 	  V1_1: true
Organizations:
  - $OrdererOrg      ## 定义Orderer组织
  	Name:			 ## Orderer的组织的名称
	SkipAsForeign:
	ID:				 ## Orderer 组织的ID （ID是引用组织的关键）
	MSPFir:			 ## Orderer的 MSP 证书目录路径
	Policees:
		Readers:  
		  Type: Signature  
		 Rule: "OR('OrdererMSP.member')"  
		Writers:  
		  Type: Signature  
		 Rule: "OR('OrdererMSP.member')"  
		Admins:  
		  Type: Signature  
		 Rule: "OR('OrdererMSP.admin')"  
		Endorsement:  
		  Type: Signature  
		 Rule: "OR('OrdererMSP.member')"
	AnchorPeers:     ## 定义组织锚节点 用于跨组织 Gossip 通信
	- Host: peer0.org1.example.com  
 	  Port: 7051
  - $Org1            ## 定义Peer组织 1
  	Name:
	ID:
	MSPDir
	AnchorPeers:
Application:

Orderer

Channel

Profiles:


```