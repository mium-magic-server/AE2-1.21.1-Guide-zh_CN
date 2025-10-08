---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 网络连接
  icon: fluix_glass_cable
---

# 网络连接

## “网络”的含义是什么？

“网络”是指一组通过能够传递[频道](../ae2-mechanics/channels.md)的方块（例如[线缆](../items-blocks-machines/cables.md)或完整方块机器与[设备](../ae2-mechanics/devices.md)）连接起来的[设备](../ae2-mechanics/devices.md)群。
（<ItemLink id="charger" />、<ItemLink id="interface" />、<ItemLink id="drive" /> 等）
严格来说，单根线缆本身就是一个网络。

## 关于设备位置的补充说明

对于具有特定网络功能的[设备](../ae2-mechanics/devices.md)（例如 <ItemLink id="interface" /> 向[网络存储](../ae2-mechanics/import-export-storage.md)推送和拉取物品、<ItemLink id="level_emitter" /> 读取网络存储内容、<ItemLink id="drive" /> 作为网络存储等），
设备的物理位置并不重要。

再次强调，**设备的物理位置并不重要**。唯一重要的是设备是否连接到网络（当然，还有它连接到的是哪个网络）。

## 网络连接

判断网络中连接了哪些组件的一个简单方法是使用 <ItemLink id="network_tool" />。它会显示网络上的所有组件，因此如果你看到了不该看到的东西，或者没看到应该看到的东西，那就说明网络连接有问题。

例如，这是两个独立的网络。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/2_networks_1.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1 2 2">
        网络 1
  </BoxAnnotation>

<BoxAnnotation color="#5CA7CD" min="2 0 0" max="3 2 2">
        网络 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

这也是两个独立的网络，因为 <ItemLink id="quartz_fiber" /> 只共享[能量](../ae2-mechanics/energy.md)，而不提供网络连接。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/2_networks_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1 2 2">
        网络 1
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="1.3 0 0" max="3 2 2">
        网络 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

然而，这只是一个网络，而不是两个独立的网络。[量子桥](../items-blocks-machines/quantum_bridge.md)的作用类似于无线的[致密线缆](../items-blocks-machines/cables.md#dense-cable)，因此两端都在同一个网络上。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/actually_1_network.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="7 3 3">
        全部为 1 个网络
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

这也只是一个网络，因为[线缆](../items-blocks-machines/cables.md)的颜色与网络连接无关，只是不同颜色的线缆不会相互连接。所有颜色的线缆都可以连接到福鲁伊克斯（或“未染色”）线缆。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/actually_1_network_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="4 2 2">
        全部为 1 个网络
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 子网络背景下的连接

[子网络](../ae2-mechanics/subnetworks.md)利用网络连接（特别是**不**连接）来限制哪些[设备](../ae2-mechanics/devices.md)可以访问其他设备。

子网络实际上就是一个独立的网络。

例如，以[自动幸运矿石处理装置](../example-setups/ore-fortuner.md)为例。这里有 3 个独立的网络，每个网络在设置中都服务于特定目的。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/ore_fortuner.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 2" max="3 1 3">
        网络 1，充当管道子网，限制输入总线可以访问的内容，使其通过成型面板“存储”矿石方块。
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="0 0 0" max="3 1 1">
        网络 2，充当另一个管道子网，限制破坏面板可以访问的内容，使其将附魔后的矿石块存储在桶中，而不是你的主网络中。这也意味着它们不会占用主网络上的任何频道。
  </BoxAnnotation>

  <BoxAnnotation color="#82CD5C" min="2 0 1" max="4 1 2">
        网络 3，包含你所有存储和合成功能的主网络。这里主要是提供能量，并且特意*不*连接到 2 个子网络。
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## P2P 背景下的连接

[P2P 通道](../items-blocks-machines/p2p_tunnels.md)的一种变体传输的是[频道](channels.md)而不是物品、流体或红石信号，这有时会让人困惑。通道所依附的网络与通道所承载的网络无关。它们*可以*是同一个网络，但不必是，而且通常不是。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_channels_network_connection.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1.98 2 1">
        网络 1，被承载的网络（通常是你的主网络）
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="2.02 0 0" max="3.98 1 1">
        网络 2，运行 ME P2P 通道的网络（通常*不是*你的主网络）
  </BoxAnnotation>

  <BoxAnnotation color="#915dcd" min="4.02 0 0" max="6 1 1">
        网络 1，被承载的网络（通常是你的主网络）
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 不太直观的连接

在这种情况下，这只是一个网络，因为 <ItemLink id="pattern_provider" />（样板供应器）作为一个完整方块设备，其作用类似于线缆，而 <ItemLink id="inscriber" />（压印器）也有类似的作用。因此，网络连接会穿过供应器和压印器。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_network_connection_1.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="4 2 2">
        全部为 1 个网络
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

为了防止这种情况（对于许多涉及[子网络](../ae2-mechanics/subnetworks.md)的自动合成设置非常有用），你可以用 <ItemLink id="certus_quartz_wrench" />（赛特斯石英扳手）右键点击供应器，使其变为定向，这样它就不会让频道穿过某一面。

<Row gap="40">
<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_network_connection_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1.98 2 2">
        网络 1
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="2.02 0 0" max="4 2 2">
        网络 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_directional_connection.snbt" />

  <BoxAnnotation color="#ee3333" min="1 .3 .3" max="1.3 .7 .7">
        注意线缆没有连接
  </BoxAnnotation>

  <IsometricCamera yaw="255" pitch="30" />
</GameScene>
</Row>

其他不提供定向网络连接的部件包括大多数[子部件](../ae2-mechanics/cable-subparts.md)[设备](../ae2-mechanics/devices.md)，例如 <ItemLink id="import_bus" />（输入总线）、<ItemLink id="storage_bus" />（存储总线）和 <ItemLink id="cable_interface" />（线缆接口）。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/subpart_no_connection.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>