---

navigation:

    parent: ae2:items-blocks-machines/items-blocks-machines-index.md

    icon: ae2netanalyser:network_analyser

    title: ME网络分析仪

categories:

- 工具

item_ids:

- ae2netanalyser:network_analyser

---



# 分析ME网络



<ItemImage id="ae2netanalyser:network_analyser" scale="4"></ItemImage>



是否曾为寻找ME网络中离线设备而苦恼？或只是想查看网络运行状况？ME网络分析仪正是您需要的工具！



## 我的ME网络状况如何？



点击连接至ME网络的任何方块、线缆或设备，即可查看所有设备状态及其连接方式。



![概览图](./pic/showoff.png)



不同颜色和形状代表不同状态：

- 蓝色立方体：正常ME设备，拥有充足频道且可传输8个频道
- 黄色立方体：密集ME设备，拥有充足频道且可传输32个频道  
- 红色立方体：离线ME设备，频道数量不足
- 蓝色连线：最多可承载8个频道的连接
- 黄色连线：最多可承载32个频道的连接
- 粉色连线：ME P2P连接
- 数字：该连线当前承载的频道数量



注意：最大频道数实际取决于您的ME频道模式。当启用无限频道模式时，分析仪将不显示频道数量。



## 自定义显示



可通过配置GUI更改分析模式和颜色。



![界面](./pic/gui.png)



ME网络分析仪提供5种模式：
- 完整模式：显示所有网络状态
- 节点模式：仅显示节点状态
- 连线模式：仅显示连接状态
- 无数字模式：不显示频道数量
- P2P模式：仅显示ME P2P连接



还可自定义节点与连线的颜色。



![界面2](./pic/color.png)