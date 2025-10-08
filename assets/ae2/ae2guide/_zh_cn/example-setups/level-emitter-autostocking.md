---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 等级发射器自动补货
  icon: level_emitter
---

# 等级发射器自动补货

有人可能会问：“如何保持一定数量的物品库存，并在需要时自动合成更多？”

一种解决方案是使用 <ItemLink id="export_bus" />、<ItemLink id="level_emitter" /> 和 <ItemLink id="crafting_card" />，从你的网络[自动合成](../ae2-mechanics/autocrafting.md)中自动请求新物品。此设置适用于维持大量单一物品的库存。

当然，你也可以通过省略等级发射器和红石卡，让网络持续合成。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/level_emitter_autostocking.snbt" />

  <BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (1) 输出总线：筛选为所需物品。装有红石卡和合成卡。红石模式设置为“有红石信号时激活”，合成行为设置为“不使用库存物品”。
        <Row><ItemImage id="redstone_card" scale="2" /> <ItemImage id="crafting_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0.7 1 0" max="1 2 1">
        (2) 等级发射器：配置了所需物品和数量，设置为“当数量小于设定数值时发出红石信号”。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (3) 接口：保持默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        连接到主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

* <ItemLink id="export_bus" /> (1) 筛选为所需物品。它装有 <ItemLink id="redstone_card" /> 和 <ItemLink id="crafting_card" />。
  “红石模式”设置为“有红石信号时激活”，“合成行为”设置为“不使用库存物品”。
* <ItemLink id="level_emitter" /> (2) 配置了所需物品和数量，并设置为“当数量小于设定数值时发出红石信号”。
* <ItemLink id="interface" /> (3) 保持默认配置。

## 工作原理

1. 如果[网络存储](../ae2-mechanics/import-export-storage.md)中所需物品的数量低于 <ItemLink id="level_emitter" /> 中指定的数量，它将发出红石信号。
2. 接收到红石信号后（由于装有 <ItemLink id="crafting_card" /> 且设置为不使用库存物品），<ItemLink id="export_bus" /> 将请求网络的[自动合成](../ae2-mechanics/autocrafting.md)来合成更多所需物品，然后将其输出。
3. 当有物品被推入（且未配置其内部库存时），<ItemLink id="interface" /> 会将该物品推入网络存储。