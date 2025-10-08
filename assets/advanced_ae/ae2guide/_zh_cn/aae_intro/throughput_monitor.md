---

navigation:

  parent: aae_intro/aae_intro-index.md

  title: ME吞吐量监控器

  icon: advanced_ae:throughput_monitor

categories:

  - 高级物品

item_ids:

  - advanced_ae:throughput_monitor

  - advanced_ae:throughput_monitor_configurator

---



# ME吞吐量监控器



<GameScene zoom="8" background="transparent">

<ImportStructure src="../structure/throughput_monitors.snbt"></ImportStructure>

<IsometricCamera yaw="195" pitch="30" />

</GameScene>



吞吐量监控器是监控器的一个子类型。它提供与<ItemLink id="ae2:storage_monitor" />相同的功能，

并额外增加了吞吐量计量功能。它会追踪单一物品/流体类型并监控其数量变化，

向用户显示每秒的吞吐量。



它*不*需要频道。



## 按键绑定



*   手持物品右键点击或手持流体容器双击右键，可将监控器设置为该物品/流体。
*   空手右键点击可清除监控器。
*   空手Shift+右键点击可锁定监控器。



## 吞吐量监控配置器



<ItemImage id="advanced_ae:throughput_monitor_configurator" scale="4"></ItemImage>



吞吐量监控配置器是一种可用于更改显示数据的工具。手持该工具右键点击监控器

可在三种选项间循环切换：



* 每Tick物品数
* 每秒物品数
* 每分钟物品数



注意：切换模式后读数可能需要一些时间才能稳定，请勿轻信初始数值！