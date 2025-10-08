---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 空间锚
  icon: spatial_anchor
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:spatial_anchor
---

# 空间锚

<BlockImage id="spatial_anchor" p:powered="true" scale="8"/>

AE2网络需要保持区块加载才能使其所有[设备](../ae2-mechanics/devices.md)正常工作，如果只有部分区块被加载，网络可能无法正常运行。空间锚解决了这个问题，它会强制加载其网络所占据的区块。
即使只有一根电缆跨越区块边界，也足以加载该新区块。

其"加载"效果会通过[量子桥](quantum_bridge.md)传播，但不会跨维度传播。因此如果你有一个通往下界的量子桥，就需要在主世界和下界的网络上各放置一个空间锚。

默认情况下，它还会在其加载的区块中启用随机刻，这可以在AE2配置中关闭。

如果需要，你可以使用<ItemLink id="certus_quartz_wrench" />（赛特斯石英扳手）来旋转它。

## 设置

*   空间锚提供了全局设置选项，可以查看以AE或E/FE为单位的能量
*   可以显示世界内的全息图，展示被加载的区块范围

## 能量消耗

空间锚将根据以下公式消耗[能量](../ae2-mechanics/energy.md)：

e = 80 + (x*(x+1))/2

其中x代表被加载的区块数量

## 配方

<RecipeFor id="spatial_anchor" />