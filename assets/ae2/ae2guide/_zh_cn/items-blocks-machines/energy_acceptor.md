---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 能源接收器
  icon: energy_acceptor
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:energy_acceptor
---

# 能源接收器

<Row gap="20">
<BlockImage id="energy_acceptor" scale="8" /> 

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/cable_energy_acceptor.snbt" />
</GameScene>
</Row>

能源接收器可将来自其他科技模组的通用能量形式转换为AE2的内部能量形式——[AE能量](../ae2-mechanics/energy.md)。
虽然<ItemLink id="controller" />控制器也能实现此功能，但控制器面数宝贵，因此通常更适合使用能源接收器。

能量转换比例如下：

*   2 FE = 1 AE (Forge版本)
*   1 E  = 2 AE (Fabric版本)

转换速度完全取决于网络可存储的AE能量总量，具体原理请参阅[此页面](../ae2-mechanics/energy.md)。

## 变体

能源接收器有两种不同变体：标准型和扁平/[子部件](../ae2-mechanics/cable-subparts.md)型，可使某些装置布局更紧凑。

能源接收器可在合成网格中切换标准型与扁平型。

## 配方

<RecipeFor id="energy_acceptor" />

<RecipeFor id="cable_energy_acceptor" />