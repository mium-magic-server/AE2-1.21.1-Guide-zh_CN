---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 控制器
  icon: controller
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:controller
---

# 控制器

<BlockImage id="controller" p:state="online" scale="8" />

控制器是 [ME 网络](../ae2-mechanics/me-network-connections.md) 的路由中枢。
没有它，网络将是“临时”的，最多只能连接总共 8 个使用 [频道](../ae2-mechanics/channels.md) 的 [设备](../ae2-mechanics/devices.md)。

一个 [ME 网络](../ae2-mechanics/me-network-connections.md) 中不能存在 2 个控制器。

控制器每面提供 32 个 [频道](../ae2-mechanics/channels.md)。

每个控制器方块需要消耗 6 AE/t 的能量才能运作。每个控制器方块可以存储 8000 AE 能量，因此更大的网络可能需要额外的能量存储。详情请参阅 [能量系统](../ae2-mechanics/energy.md)。

多方块控制器可以以相当自由的形式建造。

<GameScene zoom="2" background="transparent">
  <ImportStructure src="../assets/assemblies/controllers.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

但是，必须遵循以下几条规则：

1.  一个 [ME 网络](../ae2-mechanics/me-network-connections.md) 中的所有控制器方块必须相互连接；否则方块将变为红色。
2.  控制器的尺寸必须在 7x7x7 以内；否则它将变为红色。
3.  控制器在一个坐标轴上最多只能有 2 个相邻的方块；如果有方块违反此规则，它将被禁用并变为红色。

<GameScene zoom="2" background="transparent">
  <ImportStructure src="../assets/assemblies/controller_rules.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

只要遵循所有规则并供能，控制器就会发光并循环变色。

你可以右键单击控制器以获得与 <ItemLink id="network_tool" /> 相同的 GUI 界面。

## 配方

<RecipeFor id="controller" />