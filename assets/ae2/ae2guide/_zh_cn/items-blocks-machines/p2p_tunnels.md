---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: P2P通道
  icon: me_p2p_tunnel
  position: 210
categories:
- 设备
item_ids:
- ae2:me_p2p_tunnel
- ae2:redstone_p2p_tunnel
- ae2:item_p2p_tunnel
- ae2:fluid_p2p_tunnel
- ae2:fe_p2p_tunnel
- ae2:light_p2p_tunnel
---

# 点对点通道

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_tunnels.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

P2P通道是一种在网络中传输物品、流体、红石信号、能量、光和[频道](../ae2-mechanics/channels.md)的方式，而无需让它们直接与网络交互。P2P通道有多种变体，但每种仅传输其特定类型的内容。它们本质上就像是能够远距离直接连接两个方块面的传送门。它们不是双向的，有明确的输入和输出端。

![传送门](../assets/assemblies/p2p_portal.png)

例如，朝向物品P2P通道的漏斗会表现得像是直接连接到了木桶，物品将可以流动。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_hopper_barrel.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

然而，两个相邻的木桶之间不会传输物品。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_barrel_barrel.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

还有其他变体，例如红石P2P通道。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_redstone.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

以及用于传输频道的ME P2P通道。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_channels.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## P2P通道类型与同调

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_tunnels.snbt" />
  <IsometricCamera yaw="180" pitch="90" />
</GameScene>

P2P通道有多种类型。只有ME P2P通道可以直接合成，其他类型是通过用特定物品右键点击其他P2P通道来制作的：
- 使用任何[线缆](../items-blocks-machines/cables.md)右键点击可选择ME P2P通道。
- 使用各种红石元件右键点击可选择红石P2P通道。
- 使用箱子或漏斗右键点击可选择物品P2P通道。
- 使用桶或瓶子右键点击可选择流体P2P通道。
- 使用几乎所有含有能量的物品右键点击可选择能源P2P通道。
- 使用火把或荧石右键点击可选择光P2P通道。

某些通道类型有特殊之处。例如，ME P2P通道的频道无法通过其他ME P2P通道，并且能源P2P通道会通过增加其[能量](../ae2-mechanics/energy.md)消耗，间接地对流经自身的FE征收2.5%的“税”。

## P2P最常用的形式

P2P通道最常见的用途是使用ME P2P通道来压缩[频道](../ae2-mechanics/channels.md)传输的密度。无需使用一束致密线缆，单根致密线缆就可以用来传输大量频道。

在此示例中，8个ME P2P输入端从主网络的<ItemLink id="controller" />获取256个频道（8*32），并由8个ME P2P输出端在其他地方输出它们。请注意，每个P2P通道的输入或输出端都会占用1个频道。这样我们就可以通过一根细线缆传输许多频道。并且由于我们的P2P通道位于专用的[子网络](../ae2-mechanics/subnetworks.md)上，我们甚至没有消耗主网络的任何频道！另请注意，虽然P2P通道可以直接放置在控制器上，但也可以在中间放置一根[致密智能线缆](../items-blocks-machines/cables.md#smart-cable)以便更轻松地可视化频道。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/p2p_compact_channels.snbt" />

  <BoxAnnotation color="#dddddd" min="1.3 1.3 6.3" max="2 2.7 6.7">
        石英纤维在主网络和P2P子网络之间共享能量。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4.1 0 5.7" max="5 2.3 6.4">
        您可以将通道输入端直接放在控制器上，或者用线缆连接它。
  </BoxAnnotation>

  <IsometricCamera yaw="225" pitch="30" />
</GameScene>

关于另一个示例（包括其与[量子桥](quantum_bridge.md)的配合使用），请参见这张我懒得修改的MS Paint示意图：

![P2P与量子桥](../assets/diagrams/p2p_quantum_network.png)

## 嵌套

但是，你不能用这个方法来通过单根线缆发送无限多的频道。ME P2P通道的频道无法通过另一个ME P2P通道，因此你不能递归地嵌套它们。请注意观察红色线缆上的外层ME P2P通道是如何离线的。请注意，这仅适用于ME P2P通道，其他类型的P2P通道（如红石P2P通道工作正常所示）可以通过ME P2P通道。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_nesting.snbt" />
  <IsometricCamera yaw="225" pitch="30" />
</GameScene>

## 链接

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_linking_frequency.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

P2P通道连接的端点可以使用<ItemLink id="memory_card" />进行链接。频率将以2x2的颜色阵列形式显示在通道的背面。
- Shift+右键点击以生成一个新的P2P链接频率。
- 右键点击以粘贴设置、升级卡或链接频率。

你Shift+右键点击的通道将成为输入端，而你右键点击的通道将成为输出端。你可以有多个输出端，但对于ME P2P通道，输入端的频道会在输出端之间分配，因此你无法复制频道。

## 配方

<RecipeFor id="me_p2p_tunnel" />