---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 物质聚合器
  icon: condenser
  position: 310
categories:
- 机器
item_ids:
- ae2:condenser
---

# 物质聚合器

<BlockImage id="condenser" scale="8" />

物质聚合器可用作垃圾桶，或用于制造<ItemLink id="matter_ball" />（物质球）和
[奇点](singularities.md)。它可以接收任何存储元件能够存储的物品、流体等。

## 设置/配方

*   在垃圾桶模式下，物质聚合器会将进入其中的所有物品虚空化
*   在物质球模式下，聚合器会将放入的任何物品转化为<ItemLink id="matter_ball" />（物质球）。
    此模式需要在聚合器顶部栏位放入一个存储组件。每个物质球需要256个物品或桶，
    因此一个<ItemLink id="cell_component_1k" />（提供8192位容量）绰绰有余。
*   在奇点模式下，聚合器会将放入的任何物品转化为[奇点](singularities.md)。
    此模式需要在聚合器顶部栏位放入一个存储组件。每个奇点需要256,000个物品或桶，
    因此一个<ItemLink id="cell_component_64k" />（提供524,288位容量）绰绰有余。

请注意，在后两种会产生资源的模式下，如果能量和输出物品缓冲区都已完全填满，
物质聚合器*可能*会停止工作，并不再接收任何输入。

## 配方

<RecipeFor id="condenser" />