---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 能量
  icon: energy_cell
---

# 能量

你的网络需要能量才能运行。网络拥有一个能量池，[设备](../ae2-mechanics/devices.md)会直接从其中抽取能量，而
<ItemLink id="vibration_chamber" />（谐振仓）、<ItemLink id="energy_acceptor" />（能源接收器）（和 <ItemLink id="controller" />（控制器））则会向其添加能量。你可以
使用 <ItemLink id="network_tool" />（网络工具）右键点击网络上的任意位置，或者右键点击网络的控制器（如果有的话）来查看网络的能量统计信息。这种网络范围的存储和分配意味着
没有能量传输速率限制，因此设备可以抽取任意高的能量，
能源接收器也可以以功能上无限的速度输入能量，仅受你的能量存储限制。

## 能量接收

<Row>
  <BlockImage id="energy_acceptor" scale="4" />

  <GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/blocks/cable_energy_acceptor.snbt" />
  </GameScene>

  <BlockImage id="controller" p:state="online" scale="4" />

  <BlockImage id="vibration_chamber" p:active="true" scale="4" />
  
  <BlockImage id="crystal_resonance_generator" scale="4" />
</Row>

AE2 内部不使用 Forge Energy（在 Forge 上）或 TechReborn Energy（在 Fabric 上）。而是将它们转换为
自己的单位，AE。这种转换是单向的。能量可以通过 <ItemLink id="energy_acceptor" />（能源接收器）和
<ItemLink id="controller" />（控制器）进行转换，不过控制器的面最好用于更多的[频道](../ae2-mechanics/channels.md)。
它也可以通过 <ItemLink id="vibration_chamber" />（谐振仓）产生，或使用 <ItemLink id="crystal_resonance_generator" />（水晶谐振发电机）被动产生，但 AE2 的设计初衷
是与拥有更好能量生成的其他科技模组一起使用。

所有这些都意味着，在规划你的基地能量分配基础设施时，最好将 AE2 网络视为一个单一的大型多方块机器。

Forge Energy 和 Techreborn Energy 的转换比率为：

*   2 FE = 1 AE (Forge)
*   1 E  = 2 AE (Fabric)

## 能量存储

<Row>
  <BlockImage id="energy_cell" scale="4" p:fullness="4" />

  <BlockImage id="dense_energy_cell" scale="4" p:fullness="4" />

  <BlockImage id="creative_energy_cell" scale="4" />
</Row>

出于相对明显的原因，网络在一个游戏刻内无法输入或消耗超过其存储能力的能量。如果一个网络
只能存储 800 AE，那么当它的[设备](../ae2-mechanics/devices.md)请求能量时，它们最多只能使用 800 AE（假设存储是满的），
而能源接收器最多也只能向网络输入 800 AE（假设存储是空的）。

这是一个常见导致奇怪行为的原因，例如有人建立了一个小型网络，只有一个能源接收器、驱动器、终端和一些
设备，并试图将物品栏中满格的圆石一次性存入网络。在一个游戏刻内一次性插入所有圆石
所需的能量超过了网络的存储容量，因此并非所有圆石都被插入，网络
能量耗尽，从而重启。

**这可以通过添加能源元件来解决。**

网络每有一个线缆、机器或部件，就拥有 25 AE 的内置能量缓存。

<ItemLink id="controller" />（控制器）拥有少量的内部能量存储，为 8,000 AE。

<ItemLink id="energy_cell" />（能源元件）可以存储 200k AE，通常一个就足以满足大多数使用场景，轻松处理
正常网络使用时的功率激增。

<ItemLink id="dense_energy_cell" />（致密能源元件）可以存储 1.6M AE，适用于你想让网络依靠存储的能量运行，或
处理大型[空间存储](spatial-io.md)设置带来的巨大瞬时能量消耗的情况。

<ItemLink id="creative_energy_cell" />（创造能源元件）是一个用于测试的创造模式物品，提供**无限的能量！！！**之类的。