---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: ME驱动器
  icon: drive
  position: 210
categories:
- 设备
item_ids:
- ae2:drive
---

# ME驱动器

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/drive.snbt" />
</GameScene>

驱动器是一种[设备](../ae2-mechanics/devices.md)，您可以将[存储元件](storage_cells.md)插入其中，以便将其用于[网络存储](../ae2-mechanics/import-export-storage.md)。它有10个槽位，每个槽位可容纳一个存储元件。

如果出于某种原因需要，您可以使用任何物品物流方式（如漏斗或AE2总线）来推送和拉取驱动器物品栏中的存储元件。

可以使用<ItemLink id="certus_quartz_wrench" />（赛特斯石英扳手）来旋转它。

## 存储元件状态指示灯

驱动器中的存储元件上有一个LED指示灯，用于显示其状态：

| 颜色   | 状态                                                                           |
| :----- | :------------------------------------------------------------------------------- |
| 绿色   | 空                                                                             |
| 蓝色   | 存有部分内容                                                                     |
| 橙色   | [类型](../ae2-mechanics/bytes-and-types.md)已满，无法添加新类型                         |
| 红色   | [字节](../ae2-mechanics/bytes-and-types.md)已满，无法再插入更多物品                       |
| 黑色   | 无电力或驱动器未分配[频道](../ae2-mechanics/channels.md)                               |

## 优先级

可以通过点击图形用户界面右上角的扳手图标来设置优先级。
进入网络的物品将首先尝试存入优先级最高的存储器。
如果两个存储器或存储元件具有相同的优先级，且其中一个已包含该物品，则会优先选择该存储器。
任何[已分区](cell_workbench.md)的存储元件，当与其他存储器处于同一优先级组时，将被视为已包含该物品。
从存储中移除物品时，会优先从优先级最低的存储器中移除。
此优先级系统意味着，随着物品在网络存储中的存入和取出，高优先级的存储器将被填满，而低优先级的存储器将被清空。

## 配方

<RecipeFor id="drive" />