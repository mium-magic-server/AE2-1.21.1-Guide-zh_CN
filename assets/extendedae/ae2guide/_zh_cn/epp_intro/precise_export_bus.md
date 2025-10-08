---

导航:

    parent: epp_intro/epp_intro-index.md

    title: ME精确输出总线

    icon: extendedae:precise_export_bus

分类:

- 扩展设备

物品ID:

- extendedae:precise_export_bus

---

# ME精确输出总线

<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/cable_precise_export_bus.snbt"></ImportStructure>

</GameScene>

ME精确输出总线可按指定数量导出物品/流体。仅当容器能够完全接收全部输出时才会执行导出操作。

## 示例

![图形用户界面](../pic/pre_bus_gui1.png)

这意味着每次操作导出3个圆石。当网络中圆石数量低于3时停止导出。

![图形用户界面](../pic/pre_bus_gui2.png)

当目标容器无法容纳全部导出物时也会停止导出。此刻箱子仅能再容纳2个圆石，因此输出总线停止工作。