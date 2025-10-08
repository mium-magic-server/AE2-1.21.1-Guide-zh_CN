---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 网络工具
  icon: network_tool
  position: 410
categories:
- 工具
item_ids:
- ae2:network_tool
---

# 网络工具

<ItemImage id="network_tool" scale="4" />

网络工具是一种经过改良的[扳手](wrench.md)，它不仅能快速拆解物品、从[线缆](../ae2-mechanics/cable-subparts.md)上取下子部件，还能显示网络诊断信息并存储[升级卡](upgrade_cards.md)。不过，它无法旋转方块。

它拥有9个存储[升级卡](upgrade_cards.md)的槽位，只要该工具在你的物品栏中，这些升级卡就能在任何AE2设备的用户界面中使用。

右键点击网络的任何部分都会显示一个诊断信息窗口，类似于右键点击<ItemLink id="controller" />。该窗口会显示：

*   网络中正在使用的频道数量
*   用于切换查看能量单位（AE或FE）的全局设置选项
*   网络中存储的[能量](../ae2-mechanics/energy.md)量及网络的最大能量容量
*   输入网络和被网络使用的能量值
*   网络上所有[设备](../ae2-mechanics/devices.md)和组件的列表

在处理[子网络](../ae2-mechanics/subnetworks.md)时，此窗口也有助于判断两个不同的线缆或设备是否属于同一网络。

## 隐藏伪装板

当任意手持网络工具时，<a href="facades.md">伪装板</a>将会变为隐藏状态。

你可以直接与隐藏伪装板后的方块进行交互，而无需先移除伪装板。

## 配方

<RecipeFor id="network_tool" />