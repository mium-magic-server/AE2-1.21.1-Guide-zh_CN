---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 装桶装置
  icon: minecraft:water_bucket
---

# 装桶装置

另请参阅[倒桶装置](bucket-emptier.md)。

请注意，由于此装置使用了<ItemLink id="pattern_provider" />，它旨在集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。

有时，生活并不方便，您需要的是装在桶里的流体而非流体本身。有时机器可以为您完成此操作（例如来自热力扩展（Thermal Expansion）的流体转置机），但您可能并不总是拥有能方便地做到这一点的模组。幸运的是，原版 Minecraft 提供了一种稍欠便利的方式，即<ItemLink id="minecraft:dispenser" />。

**请注意，您通常不需要这样做，因为在[样板编码终端](../items-blocks-machines/terminals.md#pattern-encoding-terminal)中的流体替换功能允许您在合成配方中直接使用流体本身，而不是桶装的流体。**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/bucket_filler.snbt" />

<BoxAnnotation color="#dddddd" min="2 1 0" max="3 2 1">
        (1) 样板供应器：设置为“有红石信号时”锁定合成，并包含相关的处理样板。

        <Row>
        ![装填样板](../assets/diagrams/water_fill_pattern_small.png)
        ![装填样板](../assets/diagrams/lava_fill_pattern_small.png)
        </Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1.1 0.1" max="3.2 1.9 0.9">
        (2) 接口：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.1 1.1 0.8" max="3.9 1.9 1">
        (3) 存储总线 #1：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="4.05 1.05 0.8" max="4.95 1.95 1">
        (4) 成型面板：使用反相卡设置为黑名单模式，过滤桶。
        <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.2 2 1.2" max="3.8 2.2 1.8">
        (5) 输入总线：使用反相卡设置为黑名单模式，过滤桶。
        <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2.1 2 0.1" max="2.9 2.2 0.9">
        (6) 存储总线 #2：保持默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="0 1.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="225" pitch="45" />
</GameScene>

## 配置

* <ItemLink id="pattern_provider" /> (1) 设置为“有红石信号时”锁定合成，并包含相关的<ItemLink id="processing_pattern" />。
  
    ![装填样板](../assets/diagrams/water_fill_pattern.png)
    ![装填样板](../assets/diagrams/lava_fill_pattern.png)

* <ItemLink id="interface" /> (2) 保持默认配置。
* 第一个<ItemLink id="storage_bus" /> (3) 保持默认配置。
* <ItemLink id="formation_plane" /> (4) 使用反相卡设置为黑名单模式，过滤桶。
  <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
* <ItemLink id="import_bus" /> (5) 使用反相卡设置为黑名单模式，过滤桶。
  <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
* 第二个<ItemLink id="storage_bus" /> (6) 保持默认配置。

## 工作原理

1. <ItemLink id="pattern_provider" /> 将合成材料推入<ItemLink id="interface" />。
   （实际上，作为一种优化，它会直接通过存储总线和成型面板推送，就好像它们是供应器面的延伸。物品实际上从未进入接口。）
2. 通过[管道子网](pipe-subnet.md#providing-to-multiple-places)和<ItemLink id="formation_plane" />中描述的机制，桶最终进入<ItemLink id="minecraft:dispenser" />，并且流体由成型面板放置。
3. <ItemLink id="minecraft:comparator" /> 检测到发射器中的桶，从而同时激活发射器并锁定<ItemLink id="pattern_provider" />。
4. 发射器用桶舀起流体，其内部现在有一个装满流体的桶。
5. <ItemLink id="import_bus" /> 将装满的桶从发射器中拉出，并通过<ItemLink id="storage_bus" />将其存储到样板供应器中，从而将其返回到主网络。
6. 比较器检测到发射器为空，从而解锁供应器。