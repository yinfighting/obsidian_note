       示例文件: 以fabric-sample1.4.2  first-network中的crypto-config.yaml为例子

--- 

```yaml
# ---------------------------------------------------------------------------
# "OrdererOrg" - 管理Orderer节点的组织的定义
# ---------------------------------------------------------------------------
OrdererOrg:                      
	Name: Orderer                # 节点名称
	Domain: example.com          # 节点域名
	Specs:						 # 规范列表
		- Hostname: orderer      # 主机名
		- Hostname: orderer2
		- Hostname: orderer3
		- Hostname: orderer4
		- Hostname: orderer5
		
# ---------------------------------------------------------------------------
# "PeerOrgs" - 管理Peer节点的组织的定义
# ---------------------------------------------------------------------------
PeerOrgs:
  - Name: Org1
	Domain: org1.example.com
	EnableNodeOUs: true          # 如果设置了EnableNodeOUs，就在msp下生成config.yaml文件
	# 对于peer节点的组织定义，有两种写法。
	# 一种是利用编辑配置文件中的一组Specs规范条目。**每个规范条目由两个字段组成：Hostname和CommonName.
	# Hostname表示组织中节点的主机名称, CommonName是一个可选参数,可以通过重写来指定节点的名称,如果不指定,则默认 {{Hostname.Domain}}
	# Specs:
    #   - Hostname: foo # implicitly "foo.org1.example.com"
    #     CommonName: foo27.org5.example.com 
    #   - Hostname: bar
    #   - Hostname: baz
	# 另一种是使用模板来定义:
	Template:
		Count: 2
		# Start: 5
        # Hostname: {{.Prefix}}{{.Index}} # default peer0.+Domain
    # ---------------------------------------------------------------------------
    # "Users"
    # ---------------------------------------------------------------------------
    # Count: 除Admin之外的用户帐户数量
    # ---------------------------------------------------------------------------
    Users:
      Count: 1                   # 表示生成几个 普通User
	
    # ---------------------------------------------------------------------------
    # Org2: See "Org1" for full specification
    # --------------------------------------------------------------  -------------
  - Name: Org2
    Domain: org2.example.com
    EnableNodeOUs: true
    Template:
      Count: 2
    Users:
      Count: 1
	
```