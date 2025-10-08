---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: ME箱子
  icon: chest
  position: 210
categories:
- 设备
item_ids:
- ae2:chest

---

# ME箱子

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/chest.snbt" />
</GameScene>

ME箱子的功能类似于一个微型网络，集成了<ItemLink id="terminal" />、<ItemLink id="drive" />和<ItemLink id="energy_acceptor" />。
虽然它可以作为小型存储网络使用，但由于仅能容纳单个[存储元件](../items-blocks-machines/storage_cells.md)，
其实际用途较为有限。

它更适合用于直接操作内部安装的存储元件。其集成终端仅能查看和访问所安装驱动器中的物品，而通用网络上的[设备](../ae2-mechanics/devices.md)
可以访问任何[网络存储](../ae2-mechanics/import-export-storage.md)中的物品（包括ME箱子）。

它具有两种不同的GUI界面，并支持物品传输的侧面配置。与顶部的终端交互可打开集成终端界面，此面可向安装的存储元件存入物品但不可取出。
与其他任意面交互则会打开包含存储元件插槽和优先级设置的GUI界面，仅可通过带有元件插槽的面进行物品逻辑的存取操作。

可使用<ItemLink id="certus_quartz_wrench" />进行旋转。

内置小型AE能量缓存，若未接入带有[能量单元](../items-blocks-machines/energy_cells.md)的网络，
一次性存入或取出大量物品可能导致电力不足。

终端可使用<ItemLink id="color_applicator" />进行染色。

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/chest_color.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 设置

ME箱子具有与<ItemLink id="terminal" />或<ItemLink id="crafting_terminal" />完全相同的设置，
但不支持<ItemLink id="view_cell" />。

## 元件状态指示灯

箱子内的元件配有状态指示灯：

| 颜色   | 状态                                                                 |
| :----- | :------------------------------------------------------------------- |
| 绿色   | 空                                                                   |
| 蓝色   | 存有部分物品                                                         |
| 橙色   | [类型](../ae2-mechanics/bytes-and-types.md)已满，无法添加新类型        |
| 红色   | [字节](../ae2-mechanics/bytes-and-types.md)已满，无法存入更多物品      |
| 黑色   | 电力中断或驱动器无[频道](../ae2-mechanics/channels.md)                |

## 优先级

通过点击元件插槽GUI右上角的扳手图标可设置优先级。
物品进入网络时会优先选择最高优先级的存储位置。
当两个存储器或元件优先级相同时，若其中一处已存有该物品，则会优先选择该存储位置。
任何[已分区](cell_workbench.md)的元件在与其它存储器同优先级时，会被视为已存有该物品。
取出物品时则会从优先级最低的存储位置开始移除。此优先级系统意味着随着物品的存取操作，
高优先级存储器会逐渐填满，而低优先级存储器会逐渐清空。

## 配方

<RecipeFor id="chest" />