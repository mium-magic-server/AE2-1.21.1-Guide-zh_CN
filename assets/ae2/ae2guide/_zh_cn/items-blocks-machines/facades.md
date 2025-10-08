---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 伪装板
  icon: facade
  icon_components:
    "ae2:facade_item": "minecraft:stone"
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:facade
---

# 伪装板

伪装板可用于让您的基地外观更加整洁。它们可以覆盖两种尺寸的线缆，并能由多种方块制成。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/facades_1.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

它们可以覆盖线缆的所有面，但会让[子部件](../ae2-mechanics/cable-subparts.md)和线缆连接从中穿出。

<GameScene zoom="6"  interactive={true}>
  <ImportStructure src="../assets/assemblies/facades_2.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

巧妙运用它们可以提升基地的美观度，或制作出各面纹理不同的方块。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/facades_3.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 隐藏伪装板

当手中持有<a href="network_tool.md">网络工具</a>时，伪装板将会被隐藏。

您可以直接与隐藏伪装板后的方块交互，而无需先移除伪装板。

## 配方

将您想要获得纹理的方块放置在4个<ItemLink id="cable_anchor" />中间。

![伪装板配方](../assets/diagrams/facade_recipe.png)