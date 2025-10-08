---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: ME IO端口
  icon: io_port
  position: 210
categories:
- 设备
item_ids:
- ae2:io_port
---

# ME IO端口

<BlockImage id="io_port" p:powered="true" scale="8" />

IO端口允许你在[网络存储](../ae2-mechanics/import-export-storage.md)与[存储元件](../items-blocks-machines/storage_cells.md)之间快速填充或清空物品。

可以使用<ItemLink id="certus_quartz_wrench" />（赛特斯石英扳手）调整其朝向。

## 设置

*   IO端口可设置为当存储元件为空、已满或工作完成时，将其移至输出槽位
*   若插入<ItemLink id="redstone_card" />（红石卡），将提供多种红石控制选项
*   在图形用户界面中央有一个箭头，可设置物品传输方向：从存储元件到[网络存储](../ae2-mechanics/import-export-storage.md)，或从网络存储到存储元件

## 升级

IO端口支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="speed_card" />（加速卡）可提升每次操作传输的物品数量
*   <ItemLink id="redstone_card" />（红石卡）可添加红石控制功能，支持高信号激活、低信号激活或脉冲激活模式

## 配方

<RecipeFor id="io_port" />