---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 量子桥
  icon: quantum_ring
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:quantum_link
- ae2:quantum_ring
---

# 量子网络桥

![一个已形成的量子网络桥](../assets/diagrams/quantum_bridge_demonstration.png)

量子网络桥可以将[网络](../ae2-mechanics/me-network-connections.md)延伸至无限距离，甚至跨越维度。
它总共可以承载32个频道（无论线缆如何连接到每个面），本质上就像一个无线的[致密线缆](cables.md#dense-cable)。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/quantum_bridge_internal_structure_1.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/quantum_bridge_internal_structure_2.snbt" />

  <BoxAnnotation color="#33dd33" min="1 1 1" max="6 2 3">
        两个端点之间的一条假想线缆
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

需要注意的是，**两端都必须被区块加载**，因此如果两端相距甚远，必须使用<ItemLink id="spatial_anchor" />或其他区块加载器。

# ME量子环

<BlockImage id="quantum_ring" scale="8" />

将八个这样的方块围绕一个<ItemLink id="quantum_link" />放置，即可创建一个量子网络桥。只有与<ItemLink id="quantum_link" />相邻的4个<ItemLink id="quantum_ring" />方块可以接受网络连接，4个角落的方块无法连接到线缆。

## 配方

<RecipeFor id="quantum_ring" />

# ME量子链接仓

<BlockImage id="quantum_link" scale="8" />

将一个这样的方块用<ItemLink id="quantum_ring" />包围，即可创建一个量子网络桥。此方块本身不连接任何线缆，只有在完整的桥形成后才会被注册为网络的一部分。

此方块的物品栏只能容纳一个<ItemLink id="quantum_entangled_singularity" />，并且支持自动化交互。

## 配方

<RecipeFor id="quantum_link" />