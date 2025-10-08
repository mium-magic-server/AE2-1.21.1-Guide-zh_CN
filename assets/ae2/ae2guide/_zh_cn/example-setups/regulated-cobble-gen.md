---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 自动调控圆石生成器
  icon: minecraft:cobblestone
---

# 自动调控圆石生成器

自动化圆石生成器很简单，只需将 <ItemLink id="annihilation_plane" /> 朝向一个标准的原版手动圆石生成器即可。然而，这样做最终会导致你的网络被圆石堵塞，因此需要进行一些调控。

由于歼灭面板的工作原理（它们的行为类似于 <ItemLink id="import_bus" />），我们不能简单地将一个配置了 <ItemLink id="redstone_card" /> 的 <ItemLink id="level_emitter" /> 指向一个 <ItemLink id="export_bus" />（因为你不能在没有中间存储的情况下直接从输入到输出）。我们必须采用更迂回的方法。

<ItemLink id="toggle_bus" /> 允许你用红石信号连接和断开网络的各个部分，但这样做会导致网络每次都会重启。有一个简单的解决方法：将触发总线放在一个[子网络](../ae2-mechanics/subnetworks.md)上，这样它只会重启子网。

我们可以有一个独立的 <ItemLink id="annihilation_plane" /> 和 <ItemLink id="storage_bus" /> [子网络](../ae2-mechanics/subnetworks.md)，将物品推入主网络上的一个 <ItemLink id="interface" />。触发总线将通过 <ItemLink id="quartz_fiber" /> 连接和断开子网，切断面板的能源供应。

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/regulated_cobble_gen.snbt" />

<BoxAnnotation color="#dddddd" min="3 2 2" max="7 2.3 3">
        (1) 歼灭面板：没有可配置的 GUI，但可以用效率和耐久附魔来降低能耗。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 2 2" max="2.3 3 3">
        (2) 存储总线：保持默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 2.3 2" max="2.7 2.7 2.3">
        (3) 触发总线：非常重要的是，触发总线必须在子网络一侧，而不是主网络上。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 3 2.3" max="2.7 3.3 2.7">
        (4) 等级发射器：配置为圆石和所需数量，设置为“当数量小于设定数值时发出红石信号”。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 2 3" max="2 3 2">
        (5) 接口：保持默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="0 2.5 1.5" color="#00ff00">
        连接到主网络
    </DiamondAnnotation>

<DiamondAnnotation pos="5 1.5 3.5" color="#00ff00">
        含水楼梯可以防止水流动并将熔岩变成黑曜石。
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

* <ItemLink id="annihilation_plane" /> (1) 没有可配置的 GUI，但可以用效率和耐久附魔来降低能耗。
* <ItemLink id="storage_bus" /> (2) 保持默认配置。
* <ItemLink id="toggle_bus" /> (3) 必须在石英纤维的子网络一侧，而不是主网络上，否则主网络每次切换时都会重启。
* <ItemLink id="level_emitter" /> (4) 配置为所需物品和数量，并设置为“当数量小于设定数值时发出红石信号”。
* <ItemLink id="interface" /> (5) 保持默认配置。

## 工作原理

1.  圆石生成器生成圆石。
2.  <ItemLink id="annihilation_plane" /> 破坏圆石。
3.  <ItemLink id="storage_bus" /> 将圆石存储在 <ItemLink id="interface" /> 中，将其发送到主网络。
4.  当主网络中的圆石数量超过设定值时，<ItemLink id="level_emitter" /> 停止发送信号，关闭 <ItemLink id="toggle_bus" />。
5.  这会切断子网络的能源供应，使歼灭面板停止工作。