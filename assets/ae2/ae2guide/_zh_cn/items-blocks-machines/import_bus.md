---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: ME输入总线
  icon: import_bus
  position: 220
categories:
- 设备
item_ids:
- ae2:import_bus
---

# ME输入总线

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/import_bus.snbt" />
</GameScene>

输入总线会从相邻的容器中抽取物品和流体（以及安装附加模组后的其他内容物），并将其输送至[网络存储](../ae2-mechanics/import-export-storage.md)。

为降低延迟，当输入总线长时间未成功导入物品时，会进入"休眠模式"降低运行速度，直到成功导入物品后才会唤醒并恢复全速运行（每秒4次操作）。

输入总线属于[线缆子部件](../ae2-mechanics/cable-subparts.md)。

## 过滤功能

默认情况下，总线会导入所有可获取的物品。在其过滤槽中放入物品可设置白名单，仅允许导入特定物品。

即使未实际拥有某物品，也可通过JEI/REI将其拖入过滤槽设置过滤。

对流体容器（如桶或流体储罐）右键点击可设置流体过滤而非容器本身。

## 升级组件

输入总线支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="capacity_card" /> 增加过滤槽数量
*   <ItemLink id="speed_card" /> 提升单次操作传输量
*   <ItemLink id="fuzzy_card" /> 允许根据耐久度过滤或忽略物品NBT数据
*   <ItemLink id="inverter_card" /> 将过滤器从白名单切换为黑名单
*   <ItemLink id="redstone_card" /> 添加红石控制功能，可选择高信号激活、低信号激活或脉冲触发

## 传输速率

| 加速卡数量 | 单次操作传输量 |
|:-----------|:---------------|
| 0          | 1              |
| 1          | 8              |
| 2          | 32             |
| 3          | 64             |
| 4          | 96             |

## 合成配方

<RecipeFor id="import_bus" />