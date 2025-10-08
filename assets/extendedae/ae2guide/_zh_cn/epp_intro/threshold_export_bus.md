---

navigation:

    parent: epp_intro/epp_intro-index.md

    title: ME阈值输出总线

    icon: extendedae:threshold_export_bus

categories:

- 扩展设备

item_ids:

- extendedae:threshold_export_bus

---



# ME阈值输出总线



<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/cable_threshold_export_bus.snbt"></ImportStructure>

</GameScene>



ME阈值输出总线会在ME网络中存储的物品数量高于/低于设定阈值时工作。



## 示例



![图形用户界面](../pic/thr_bus_gui1.png)



铜的阈值设置为128，因此当网络中存储的铜超过128时就会输出铜。



![图形用户界面](../pic/thr_bus_gui2.png)



阈值设置与上图相同，但模式设置为"低于"。当存储的铜低于128时就会输出铜。