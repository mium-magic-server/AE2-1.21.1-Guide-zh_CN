---
navigation:
  parent: ae2机制/ae2机制索引.md
  title: 子网络
---

# 子网络

<GameScene zoom="4" interactive={true}>
<ImportStructure src="../assets/assemblies/subnet_demonstration.snbt" />

<DiamondAnnotation pos="6.5 2.5 0.5" color="#00ff00">
        物品管道子网络
    </DiamondAnnotation>

<DiamondAnnotation pos="5.5 2.5 0.5" color="#00ff00">
        流体管道子网络
    </DiamondAnnotation>

<DiamondAnnotation pos="4.5 2.5 0.5" color="#00ff00">
        过滤型破坏面板
    </DiamondAnnotation>

<DiamondAnnotation pos="3.5 2.5 0.5" color="#00ff00">
        成型面板子网络
    </DiamondAnnotation>

<DiamondAnnotation pos="2.5 2.5 0.5" color="#00ff00">
        利用接口-存储总线交互的子网络，充当主网络可访问的本地子存储
    </DiamondAnnotation>

<DiamondAnnotation pos="1.5 1.5 0.5" color="#00ff00">
        另一个物品管道子网络，用于将充能后的物品送回样板供应器
    </DiamondAnnotation>

<IsometricCamera yaw="195" pitch="30" />
</GameScene>

“子网络”是一个定义相对宽松的术语，但可以说，子网络是任何用于支持主网络或执行某些小任务的[网络](../ae2-mechanics/me-network-connections.md)。它们通常规模较小，无需控制器。其主要用途通常有两个：

*   限制哪些[设备](../ae2-mechanics/devices.md)可以访问哪些存储（你不希望“管道”子网络上的输入总线访问主网络存储，否则它会将物品放入你的存储元件中，而不是放入目标容器中）。
*   为主网络节省频道，例如让一个样板供应器输出到一个连接了多台机器上多个存储总线的接口，仅使用1个频道，而不是在每台机器上都放置一个样板供应器，使用多个频道。

构建子网络时，跟踪[网络连接](../ae2-mechanics/me-network-connections.md)非常重要。
通常，人们会拼凑一些接口、总线之类的东西，并期望它成为一个子网络，而实际上所有设备仍然通过各种完整方块设备连接到主网络。

不同颜色的线缆除了彼此不会连接之外，与创建子网络没有直接关系。

一些例子包括：

*   一个用整个AE2网络取代你的垃圾桶/虚空升级的设置，该网络决定如何最佳利用你的垃圾。根据可用性和需求，智能地将物品路由到堆肥桶阵列或某些模组的回收机。
*   构建抽象层。从你的子网络管理复杂合成操作的所有细节，这样从主网络的角度来看，整个工厂“看起来像”一台机器。
*   并行处理。用10台慢速机器的副本替换一台慢速机器。从主网络的角度来看，没有任何变化，甚至没有使用更多频道。
*   一个输入总线和存储总线的设置，用于像物品或流体管道一样将物品或流体从一个容器传输到另一个容器。
*   一个破坏面板和存储总线，使得破坏面板只能将其破坏的物品放入存储总线，从而允许你过滤该面板。
*   一个接口和成型面板，使得插入接口的任何物品都会被推送到成型面板并放置/掉落至世界中。
*   一个自动生产赛特斯石英的设置，由主网络上的<ItemLink id="level_emitter" />（等级发射器）进行调节和控制。
*   一个通过特殊的“存储总线连接接口”交互可从主网络访问的专用存储系统，用于存储农场的产出，而不会让你的主存储无限溢出。
*   等等

对于创建子网络，<ItemLink id="quartz_fiber" />（石英纤维）非常有用。它能在网络之间传输能量而无需连接它们，让你无需到处放置能源接收器和能源线缆即可为子网络供电。