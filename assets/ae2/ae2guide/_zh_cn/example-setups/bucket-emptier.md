---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 桶清空装置
  icon: minecraft:bucket
---

# 桶清空装置

另请参阅[桶填充装置](bucket-filler.md)。

请注意，由于此装置使用了<ItemLink id="pattern_provider" />，它旨在集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。

有时候，生活不太方便，您需要的是流体本身，但您只能制作装在桶里的流体。有时机器可以为您完成此操作（例如热力膨胀的流体转置机），但您可能并不总是拥有能方便地做到这一点的模组。幸运的是，原版 Minecraft 提供了一种稍欠便捷的方式，即<ItemLink id="minecraft:dispenser" />。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/bucket_emptier.snbt" />

<BoxAnnotation color="#dddddd" min="2 1 0" max="3 2 1">
        (1) 样板供应器：设置为“有红石信号时”锁定合成并开启阻塞模式，并包含相关的处理样板。

        <Row>
        ![填充样板](../assets/diagrams/water_empty_pattern_small.png)
        ![填充样板](../assets/diagrams/lava_empty_pattern_small.png)
        </Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2.1 2 0.1" max="2.9 2.2 0.9">
        (2) 接口：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.1 2 1.1" max="3.9 2.2 1.9">
        (3) 存储总线 #1：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="4.05 1.05 0.8" max="4.95 1.95 1">
        (4) 破坏面板：无配置界面。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.2 1.2 0.8" max="3.8 1.8 1">
        (5) 输入总线：过滤设置为桶。
        <ItemImage id="minecraft:bucket" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1.1 0.1" max="3.2 1.9 0.9">
        (6) 存储总线 #2：保持默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="0 1.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="225" pitch="45" />
</GameScene>

## 配置

*   <ItemLink id="pattern_provider" /> (1) 设置为“有红石信号时”锁定合成并开启阻塞模式，并包含相关的<ItemLink id="processing_pattern" />。

    ![填充样板](../assets/diagrams/water_empty_pattern.png)
    ![填充样板](../assets/diagrams/lava_empty_pattern.png)

*   <ItemLink id="interface" /> (2) 保持默认配置。
*   第一个<ItemLink id="storage_bus" /> (3) 保持默认配置。
*   <ItemLink id="annihilation_plane" /> (4) 无配置界面，无法配置。
*   <ItemLink id="import_bus" /> (5) 过滤设置为桶。
    <ItemImage id="minecraft:bucket" scale="2" />
*   第二个<ItemLink id="storage_bus" /> (6) 保持默认配置。

## 工作原理

1.  <ItemLink id="pattern_provider" /> 将材料推入<ItemLink id="interface" />。
    （实际上，作为一种优化，它通过存储总线直接推送，就好像它是供应器面的延伸。物品实际上从未进入接口。）
2.  通过[管道子网](pipe-subnet.md#providing-to-multiple-places)中描述的机制，桶最终进入<ItemLink id="minecraft:dispenser" />。
3.  <ItemLink id="minecraft:comparator" /> 检测到发射器中的桶，从而同时激活发射器并锁定<ItemLink id="pattern_provider" />。
4.  发射器将桶中的流体倒出，自身现在剩下一个空桶。
5.  <ItemLink id="import_bus" /> 将空桶从发射器中抽出，并通过<ItemLink id="storage_bus" />将其存入样板供应器，使其返回主网络。
6.  比较器检测到发射器已空，解锁供应器。