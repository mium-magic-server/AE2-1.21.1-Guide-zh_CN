---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: ME存储总线
  icon: storage_bus
  position: 220
categories:
- 设备
item_ids:
- ae2:storage_bus
---

# 存储总线

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/storage_bus.snbt" />
</GameScene>

是否曾想过*保留*你的“箱子怪”而不是用更合理的东西替换它？我们为您呈现存储总线！

存储总线可将其连接的物品栏转变为[网络存储](../ae2-mechanics/import-export-storage.md)。
它通过允许网络查看该物品栏的内容，并通过向该物品栏推送和拉取物品来满足其他[设备](../ae2-mechanics/devices.md)对网络存储的存取需求。

由于AE2通过[设备](../ae2-mechanics/devices.md)功能交互实现涌现机制的哲学，你并不一定*必须*将存储总线用于*存储*。通过使用[子网络](../ae2-mechanics/subnetworks.md)使一个存储总线（或少数几个存储总线）成为网络中*唯一*的存储，你可以将其用作物品传输的源或目的地。（参见[“管道子网”](../example-setups/pipe-subnet.md)）

重要提示：像抽屉这样经过优化的大型物品栏没问题，但像巨型箱子这样具有许多槽位的*未*优化大型物品栏，与存储总线一起使用时会对性能造成严重影响。

它们是[线缆子部件](../ae2-mechanics/cable-subparts.md)。

## 过滤

默认情况下，总线会存储所有物品。放入其过滤槽的物品将作为白名单，仅允许存储这些特定物品。

即使你实际上没有任何该物品，也可以从JEI/REI中将物品和流体拖入过滤槽。

使用流体容器（如桶或流体储罐）右键单击，可将该流体设置为过滤器，而不是桶或储罐物品本身。

## 优先级

可以通过点击GUI右上角的扳手设置优先级。
进入网络的物品会首先尝试进入优先级最高的存储。如果两个存储具有相同的优先级，且其中一个已包含该物品，则会优先选择该存储。
任何已设置过滤的存储，在与其它存储处于同一优先级组时，会被视为已包含该物品。
从存储中移除物品时，会从优先级最低的存储中移除。此优先级系统意味着随着物品在网络存储中的存入和取出，高优先级存储会被填满，而低优先级存储会被清空。

## 设置

*   总线可以根据相邻物品栏的当前内容进行分区（过滤）
*   可以允许或禁止网络查看总线无法从相邻物品栏中提取的物品
    （例如，存储总线无法从<ItemLink id="inscriber" />的中间输入槽提取物品）
*   总线可以在存入和提取时都进行过滤，或仅在存入时过滤
*   总线可以设置为双向、仅存入或仅取出

## 升级

存储总线支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="capacity_card" /> 增加过滤槽数量
*   <ItemLink id="fuzzy_card" /> 允许总线按损坏程度过滤和/或忽略物品NBT
*   <ItemLink id="inverter_card" /> 将过滤器从白名单切换为黑名单
*   <ItemLink id="void_card" /> 在连接的物品栏已满时虚空掉存入的物品，对于防止农场堵塞非常有用。使用时请务必设置过滤！

## 配方

<RecipeFor id="storage_bus" />