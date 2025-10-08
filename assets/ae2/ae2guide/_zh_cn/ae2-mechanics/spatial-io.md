---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 空间IO
  icon: spatial_storage_cell_2
---

# 空间IO

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/spatial_storage_1x1x1.snbt" />

  <BoxAnnotation color="#33dd33" min="1 1 1" max="2 2 2">
        待移动的空间范围
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />

</GameScene>

空间IO是一种在你的世界中剪切和粘贴物理空间范围的方法。它可以用来移动<ItemLink id="flawless_budding_quartz" />，
在你的基地中设置一个可以更换不同内部结构的房间以用于不同目的，甚至移动末地传送门！

它的工作原理是将定义的空间范围与空间存储维度中一个相同大小的范围进行*交换*，将位于塔阵列中的所有东西发送到空间存储维度，
并将该维度中的所有东西传送到塔阵列中。

这意味着如果你有在不同维度间旅行的方法（空间IO*可以*用来制作传送器，但这非常复杂、有点不稳定，且超出了本指南的范围），
你可以将它们用作自定义大小的紧凑机器或口袋维度。

# 多方块结构设置

空间IO需要其组件以特定方式排列才能运作，并定义要剪切和粘贴的空间范围。

所有组件必须位于同一个[网络](me-network-connections.md)上才能运作，并且一个网络上只能有一个空间IO设置。
因此，推荐使用[子网络](subnetworks.md)。

## 空间IO端口

<BlockImage id="spatial_io_port" p:powered="true" scale="4" />

<ItemLink id="spatial_io_port" />控制着空间IO操作。它显示多方块结构的统计数据，并存放[空间存储元件](../items-blocks-machines/spatial_cells.md)。

它显示：
- 网络中存储的和最大的[能量](energy.md)
- 执行操作所需的能量。这可能非常巨大并且是瞬时消耗的，所以请确保你有足够的[能量电池](../items-blocks-machines/energy_cells.md)来储存。
- 塔阵列的效率
- 定义的空间范围的大小

要执行空间IO操作，请将一个空间存储元件放入输入槽，并给空间IO端口一个红石脉冲。
然后它将*交换*塔中的空间范围与空间存储维度中的空间范围。这意味着如果你将一组方块发送到空间存储维度，
*然后在塔中放入另一组方块*，将元件放回输入槽，并再次触发IO端口，第二组方块将消失，第一组方块将重新出现。

**请小心，定义范围内的任何实体，包括你自己，都会被一同带走，如果你没有出来的方法，你将被困在空间存储维度中，一个黑暗、毫无特征的盒子里。** 用这个来恶作剧你的朋友吧！

## 空间塔

<BlockImage id="spatial_pylon" p:powered_on="true" scale="4" />

<ItemLink id="spatial_pylon" />是空间IO设置的主要部分，并定义了要受影响的空间范围。

该范围由塔外部的边界框在所有方向上向内收缩1个方块来定义。

规则是：
- 最小尺寸为3x3x3（这定义了一个1x1x1的范围）
- 所有空间塔必须在外部边界框内
- 所有空间塔必须在同一网络上
- 所有塔的长度必须至少为2个方块

例如，假设你想定义一个3x3x3的范围。根据规则2，所有塔必须位于你想要定义的范围周围的一个5x5x5外壳内。
它们几乎可以是任何配置，只要它们包含在那个1方块厚的5x5x5外壳内。

<GameScene zoom="4" interactive={true}>
<ImportStructure src="../assets/assemblies/spatial_storage_3x3x3_pylon_demonstration.snbt" />

<BoxAnnotation color="#33dd33" min="1 1 1" max="4 4 4">
        待移动的空间范围
  </BoxAnnotation>

<BoxAnnotation color="#3333ff" min="5 5 0" max="0 0 5">
  </BoxAnnotation>

<IsometricCamera yaw="195" pitch="30" />
</GameScene>

一个更合理的设置是这样的：

<GameScene zoom="4" interactive={true}>
<ImportStructure src="../assets/assemblies/better_spatial_storage_3x3x3.snbt" />

<BoxAnnotation color="#33dd33" min="1 1 1" max="4 4 4">
        待移动的空间范围
  </BoxAnnotation>

<BoxAnnotation color="#3333ff" min="5 5 0" max="0 0 5">
  </BoxAnnotation>

<IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 效率

塔阵列的效率取决于你填充外壳的程度。围绕大范围的最小设置将非常低效，并且可能需要*数十亿*的AE能量。

## 元件维度

一旦一个[空间存储元件](../items-blocks-machines/spatial_cells.md)被使用过，它就会获得一个永久定义的XYZ维度集（例如，3x4x2），
并链接到空间存储维度中的一个空间范围。**在空间存储元件被使用后，你无法重置、重新格式化或调整其大小。**
如果你想使用不同的维度，请制作一个新的元件。

这些维度与元件名称中的维度不同，一个16^3的元件可以拥有*最大*为16x16x16的任何维度。

请注意，这个范围是有方向性的，无法旋转。一个2x2x3的范围与一个3x2x2的范围是不同的，即使它们的大小相同。

如果元件的XYZ维度与定义的范围（在IO端口处可见）不匹配，IO端口将无法操作。