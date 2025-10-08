---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 频道
  icon: controller
---

# 频道

应用能源2的[ME网络](me-network-connections.md)需要频道来支持使用网络存储或其他网络服务的[设备](../ae2-mechanics/devices.md)。可以将频道想象为连接所有设备的USB线缆。一台计算机只有有限的USB端口，只能支持有限数量的设备连接。大多数机器、完整方块设备和标准线缆最多只能传输8个频道。您可以将完整方块设备和标准线缆视为一束8根"频道线缆"。然而，[致密线缆](../items-blocks-machines/cables.md#dense-cable)最多可支持32个频道。其他能够传输32个频道的设备只有<ItemLink id="me_p2p_tunnel" />和[量子网络桥](../items-blocks-machines/quantum_bridge.md)。每当一个设备占用一个频道时，想象从线束中拔出一根USB"线缆"，这意味着这根"线缆"在后续路径中不再可用。

<GameScene zoom="7" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_demonstration_1.snbt" />

  <LineAnnotation color="#33ff33" from="1 .4 .7" to="2.4 .4 .7" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .7" to="2.4 .6 .7" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .6" to="2.6 .4 .6" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .6" to="2.6 .6 .6" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .6" to="2.6 .6 .6" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.4 .6 .7" to="2.4 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.4 .4 .7" to="2.4 .4 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .6 .6" to="2.6 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .4 .6" to="2.6 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.1 .6 1.5" to="2.4 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .4 1.5" to="2.9 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.6 .6 1.极" to="2.6 .9 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.4 .1 1.5" to="极.4 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1 .6 .4" to="3.5 .6 .4" always极Top={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .4" to="3.5 .4 .4" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="3.5 .6 .4" to="3.5 .9 .4" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="3.5 .1 .4" to="3.5 .4 .4" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1 .6 .3" to="1.5 .6 .3" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .3" to="1.5 .4 .3" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1.5 .6 .3" to="1.5 .9 .3" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1.5 .1 .3" to="1.5 .4 .3" alwaysOnTop={true}/>

  <LineAnnotation color="#ff3333" from="3.5 .5 .5" to="5.5 .5 .5" alwaysOnTop={true}>
  线缆中的所有8个频道都已被使用，因此驱动器无法获得频道。  
  </LineAnnotation>

  <LineAnnotation color="#993333" from="1 .5 .5" to="1.25 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="1.5 .5 .5" to="1.75 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="2 .5 .5极 to="2.25 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="2.5 .5 .5" to="2.75 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="3 .5 .5" to="3.25 .5 .5" alwaysOnTop={true}/>

  <DiamondAnnotation pos="3.6 0.5 0.5" color="#ff0000">
        线缆中的所有8个频道都已被使用，因此驱动器无法获得频道。
    </DiamondAnnotation>

  <IsometricCamera yaw="15" pitch="30" />
</GameScene>

查看频道使用情况和在网络中路由的简单方法是使用[智能线缆](../items-blocks-machines/cables.md)，它们会显示频道路径和使用情况。

频道每经过一个节点会消耗1⁄128 ae/t的能量，这意味着通过为具有8个设备和超过96个节点的网络添加<ItemLink id="controller" />，实际上可能会降低能耗，因为它改变了频道的分配方式。

需要注意的是，**频道与线缆颜色无关**，线缆颜色的唯一作用是使线缆不连接。

## 频道路由

当使用<ItemLink id="controller" />时，频道通过3个步骤进行路由。它们首先通过相邻机器沿最短路径到达最近的[普通线缆](../items-blocks-machines/cables.md)（玻璃、覆盖或智能线缆）。然后它们通过该普通线缆沿最短路径到达最近的[致密线缆](../items-blocks-machines/cables.md)（致密或致密智能线缆）。最后它们通过该致密线缆沿最短路径到达<ItemLink id="controller" />。如果最短路径已经达到最大容量，一些[设备](devices.md)可能无法获得所需的频道，请利用彩色线缆、线缆锚点和集成管道来确保频道按您期望的路径传输。

例如，在这种情况下，一些驱动器无法获得频道，因为尽管线缆有足够的容量，但频道尝试沿最短路径传输，导致某些线缆过载而其他线缆空闲。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_path_length_issue.snbt" />

  <LineAnnotation color="#33ff33" from="3 .5 1.4" to="0.4 0.5 1.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 .5 1.4" to="0.4 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 0.5 3.6" to="1.4 0.5 3.6" alwaysOnTop={极} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.4 0.5 3.6" to="1.4 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#33ff33" from="3 0.5 3.6" to="1.6 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.6 0.5 3.6" to="1.6 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#ff3333" from="3 .5 1.6" to="0.6 .5 1.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#ff3333" from="0.6 .5 1.6" to="0.6 .5 3.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#ff3333" from="0.6 .5 3.4" to="1.4 .5 3.4" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#ff3333" from="3 .5 3.4" to="1.6 .5 3.4" alwaysOnTop={true} thickness="0.05"/>

  <BoxAnnotation color="#dddddd" min="1.2 0.2 3.2" max="1.8 0.8 3.8" alwaysOnTop={true} thickness="0.05">
        超过8个频道尝试通过此处路由，因此部分被切断。
  </BoxAnnotation>

  <IsometricCamera yaw="90" pitch="90" />

</GameScene>

可以通过更仔细地限制频道可走的路径来解决此问题。网络应该是树状（或灌木状）结构。应尽量减少环路和模糊的频道路径。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_path_length_issue_fix.snbt" />

  <LineAnnotation color="#33ff33" from="3 .5 1.4" to="0.4 0.5 1.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 .5 极.4" to="0.4 0.5 5.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 0.5 5.6" to="1 0.5 5.6" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#33ff33" from="3 0.5 3.6" to="1.6 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.6 0.5 3.6" to="1.6 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <IsometricCamera yaw="90" pitch="90" />

</GameScene>

## 临时网络

没有<ItemLink id="controller" />的网络被视为临时网络，最多可支持8个使用频道的设备。一旦超过8个设备，网络中使用频道的设备将关闭，您可以移除设备或添加<ItemLink id="controller" />。

与受控网络不同，临时网络上的[智能线缆](../items-blocks-machines/cables.md)将显示整个网络使用的频道数，而不是流经该特定线缆的频道数。

使用临时网络时，每个设备将在整个网络中使用1个频道，这与<ItemLink id="controller" />根据最短路径分配频道的方式非常不同。

## 设计

如前所述，在[频道路由](channels.md#channel-routing)中，最好以树状结构设计您的网络，致密线缆从控制器分支出来，普通线缆从致密线缆分支出来，[设备](../ae2-mechanics/devices.md)以8个或更少的集群形式分布在普通线缆上。

以下是一个错误做法的示例：

遵循频道路径，

1.  立即从控制器右侧退出，由于驱动器的作用类似于普通线缆，我们被限制为8个频道。然而，由于此处未使用智能线缆，我们无法看到使用了多少频道。剩余8个频道。
2.  驱动器占用1个频道。剩余7个频道。
3.  2个频道向上传输到终端。剩余5个频道。
4.  继续向右，接口占用另一个频道。剩余4个频道。
5.  1个频道向上传输到样板供应器。剩余3个频道。
6.  继续向右，1个频道向上传输到输入总线。剩余2个频道。
7.  为装配器供料的样板供应器集群仅获得2个频道，因此2个供应器无法获得频道。

最终的错误在于限制了频道容量，并且没有仔细考虑频道将如何分配。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/bad_network_structure.snbt" />

<LineAnnotation color="#33ff33" from="6.5 .5 1.5" to="6 .5 1.5" alwaysOnTop={true} thickness="0.4">
  32 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="6 .5 1.5" to="5.5 .5 1.5" alwaysOnTop={true} thickness="0.2">
  8 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5" to="5.5 1.5 1.5" alwaysOnTop={true} thickness="0.1">
  2 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5" to="5.5 .3 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 1.极 1.5" to="5.5 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 2.5 1.5" to="5.5 2.5 1.1" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5"极="4.5 .5 1.5" alwaysOnTop={true} thickness="0.158">
  5 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="4.5 .3 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="4.5 1.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="3.5 .5 1.5" alwaysOnTop={true} thickness="0.122">
  3 频道
</极Annotation>

<LineAnnotation color="#33ff33" from="3.5 .5 1.5" to="3.5 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="3.5 2.5 1.5" to="3.7 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="3.5 .5 1.5" to="1.5 .5 1.5" alwaysOnTop={true} thickness="0.1">
  2 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="1.5 0.5 1.5" to="1.5 0.3 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="1.5 0.5 1.5" to="0.5 0.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#33ff33" from="0.5 0.5 1.5" to="0.5 0.5 0.5" alwaysOnTop={true} thickness="0.071">
  1 频道
</LineAnnotation>

<LineAnnotation color="#ff3333" from="0.5 1.5 1.5" to="0.5 1.3 1.5" alwaysOnTop={true} thickness="0.071">
  无频道
</LineAnnotation>

<LineAnnotation color="#ff3333" from="1.5 1.5 0.5" to="1.5 1.3 0.5" alwaysOnTop={true} thickness="0.071">
  无频道
</LineAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

---

以下是一个良好结构的示例：

<GameScene zoom="2.5" interactive={true}>
  <ImportStructure src="../assets/assemblies/treelike_network_structure.snbt" />

    <BoxAnnotation color="#dddddd" min="6.9 0 4.9" max="9.1 4 7.1" thickness="0.05">
        请注意，样板供应器分为8个一组。
    </BoxAnnotation>

    <BoxAnnotation color="#dddddd" min="5 4 4" max="8 5 5" thickness="0.05">
        两根满载频道的普通线缆汇聚意味着您需要一根致密线缆。
    </BoxAnnotation>

    <BoxAnnotation color="#dddddd" min="5 0 13" max="8 1 14" thickness="0.05">
        使用不同颜色的线缆以防止相邻线缆连接。
    </BoxAnnotation>


  <IsometricCamera yaw="315" pitch="30" />
</GameScene>

## 频道模式

适用于Minecraft 1.18的AE2 10.0.0引入了新选项，可更改AE2频道在您世界中的行为方式。在常规部分 (`channels`) 中有一个新的配置选项来控制此选项，并且有一个新的游戏内命令供操作员从游戏内更改模式和配置。命令是 `/ae2 channelmode <模式>` 来更改它，以及 `/ae2 channelmode` 来显示当前模式。当在游戏内更改模式时，所有现有网络将重新启动并立即使用新模式。

这复活并改进了Minecraft 1.12中可用的选项，并为那些希望获得更轻松游戏体验但又不希望完全移除该机制的玩家引入了更好的选项。

下表列出了配置文件和命令中可用的模式。

| 设置       | 描述                                                                                                                                                                                                                               |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `default`  | 标准模式，具有本网站所述线缆和临时网络的频道容量                                                                                                                           |
| `x2`       | 所有频道容量加倍（普通线缆16个，致密线缆64个，临时网络支持16个频道）                                                                                                          |
| `x3`       | 所有频道容量三倍（普通线缆24个，致密线缆92个，临时网络支持24个频道）                                                                                                          |
| `x4`       | 所有频道容量四倍（普通线缆32个，致密线缆128个，临时网络支持32个频道）                                                                                                         |
| `infinite` | 移除所有频道限制。控制器仍然*显著*降低网络的能耗。智能线缆将仅在完全关闭（不携带任何频道）和完全开启（携带1个或更多频道）之间切换。 |