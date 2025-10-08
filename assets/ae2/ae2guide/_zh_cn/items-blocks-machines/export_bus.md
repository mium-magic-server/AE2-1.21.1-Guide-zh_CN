---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: ME输出总线
  icon: export_bus
  position: 220
categories:
- 设备
item_ids:
- ae2:export_bus
---

# ME输出总线

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/export_bus.snbt" />
</GameScene>

输出总线会从[网络存储](../ae2-mechanics/import-export-storage.md)中提取物品和流体（以及任何其他附加内容，取决于模组附加），并将其推入所连接的容器中。

为降低延迟，若输出总线近期未成功输出物品，会进入"休眠模式"降低操作频率，直到成功输出物品时才会唤醒并加速至全速运行（每秒4次操作）。

输出总线属于[线缆子部件](../ae2-mechanics/cable-subparts.md)。

## 过滤功能

默认状态下总线不会输出任何物品。将其充物品放入过滤槽会形成白名单，仅允许输出指定的物品。

即使未实际拥有该物品，也可通过JEI/REI将物品和流体拖入过滤槽。

对流体容器（如桶或流体储罐）右键点击可设置流体过滤器而非容器物品本身。

## 升级项目

输出总线支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="capacity_card" /> 增加过滤槽数量，并提供过滤项输出顺序的设置选项
*   <ItemLink id="speed_card" /> 提升每次操作传输的物品数量
*   <ItemLink id="fuzzy_card" /> 允许根据损伤值进行过滤和/或忽略物品NBT数据
*   <ItemLink id="crafting_card" /> 可向[自动合成系统](../ae2-mechanics/autocrafting.md)发送合成请求获取所需物品。可设置为优先从存储中提取，或始终请求合成新物品
*   <ItemLink id="redstone_card" /> 增加红石控制功能，可选择高信号激活、低信号激活或脉冲触发模式

## 传输速率

| 加速卡数量 | 每次操作传输量 |
|:-----------|:---------------|
| 0          | 1              |
| 1          | 8              |
| 2          | 32             |
| 3          | 64             |
| 4          | 96             |

## 合成配方

<RecipeFor id="export_bus" />