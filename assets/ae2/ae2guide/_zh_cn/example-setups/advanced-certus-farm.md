---
navigation:
  parent: 示例设置/示例设置索引.md
  title: 高级赛特斯石英农场
  icon: certus_quartz_crystal
  position: 120
---

# 高级赛特斯石英农场

这基本上就是[半自动赛特斯石英农场](semiauto-certus-farm.md)，只不过它已经完全集成到了你的ME系统中。

这个设置不再需要大量堆积母岩方块并时不时手动刷新它们，而是使用[充能自动化](charger-automation.md)和[投水自动化](throw-in-water-automation.md)来自动完成。

预计速度请参见[赛特斯石英生长](../ae2-mechanics/certus-growth.md)。

**这是一个复杂的构建，部分结构被其他部件遮挡，请旋转视角从各个角度查看**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/advanced_certus_farm.snbt" />

  <BoxAnnotation color="#ddaaaa" min="3.7 2 1" max="4 3 2">
        (1) 破坏面板 #1：无配置界面，但可附魔时运。
  </BoxAnnotation>

  <BoxAnnotation color="#ddaaaa" min="2 2 1.7" max="3 3 2">
        (2) 存储总线 #1：过滤设置为赛特斯石英水晶。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 2.5 1.5" color="#ff0000">
    晶簇破除子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#aaddaa" min="3.7 1 1" max="4 2 2">
        (3) 破坏面板 #2：无配置界面，但附魔了精准采集。
  </BoxAnnotation>

  <BoxAnnotation color="#aaddaa" min="2 1 1.7" max="3 2 2">
        (4) 存储总线 #2：过滤设置为赛特斯石英块。
        <BlockImage id="quartz_block" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 1.5 1.5" color="#00ff00">
    赛特斯方块破除子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#ffddaa" min="4 0.7 1" max="5 1 2">
        (5) 成型面板：保持默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#ffddaa" min="2 0.7 2" max="3 1 3">
        (6) 输入总线：过滤设置为有瑕的赛特斯石英母岩。
        <BlockImage id="flawed_budding_quartz" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 0.5 1.5" color="#ddcc00">
    母岩放置子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#aaaadd" min="1.7 2 2" max="2 3 3">
        (7) 存储总线 #3：过滤设置为赛特斯石英水晶。优先级设置高于你的主存储。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#aaaadd" min="2 1 2" max="3 2 3">
        (8) 接口：设置为自身保持 1 个有瑕的赛特斯石英母岩，并装有合成卡。
        <Row><BlockImage id="flawed_budding_quartz" scale="2" /> <ItemImage id="crafting_card" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="1.5 0.5 0" color="#00ff00">
        连接至主网络、充能自动化及投水自动化
        <Row>
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/charger_automation.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/throw_in_water.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
        </Row>
    </DiamondAnnotation>

  <IsometricCamera yaw="165" pitch="5" />
</GameScene>

## 配置

### 晶簇破除子网络：

* 第一个<ItemLink id="annihilation_plane" /> (1) 无配置界面且无法配置，但可附魔时运。
* 第一个<ItemLink id="storage_bus" /> (2) 过滤设置为<ItemLink id="certus_quartz_crystal" />。

### 赛特斯方块破除子网络：

* 第二个<ItemLink id="annihilation_plane" /> (3) 无配置界面且无法配置，但必须附魔精准采集。
* 第二个<ItemLink id="storage_bus" /> (4) 过滤设置为<ItemLink id="quartz_block" />。

### 母岩放置子网络：

* <ItemLink id="formation_plane" /> (5) 保持默认配置。
* <ItemLink id="import_bus" /> (6) 过滤设置为<ItemLink id="flawed_budding_quartz" />。

### 主网络上：

* 第三个<ItemLink id="storage_bus" /> (7) 过滤设置为<ItemLink id="certus_quartz_crystal" />，并且其[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)设置高于你的主存储。
* <ItemLink id="interface" /> (8) 设置为自身保持 1 个有瑕的赛特斯石英母岩，并装有<ItemLink id="crafting_card" />。

## 工作原理

### 晶簇破除子网络：

晶簇破除子网络的工作方式与[简易赛特斯石英农场](simple-certus-farm.md)中的子网络非常相似。

1. <ItemLink id="annihilation_plane" /> 尝试破坏其前方的方块，但由于子网络上唯一的存储是过滤设置为<ItemLink id="certus_quartz_crystal" />的<ItemLink id="storage_bus" />，因此它只能破坏<ItemLink id="quartz_cluster" />。
2. <ItemLink id="storage_bus" /> 将赛特斯石英水晶存储到木桶中。

### 赛特斯方块破除子网络

赛特斯方块破除子网络用于在耗尽的母岩方块转变为普通的<ItemLink id="quartz_block" />后将其破坏。其工作原理与晶簇破除子网络相似。

1. <ItemLink id="annihilation_plane" /> 尝试破坏其前方的方块，但由于子网络上唯一的存储是过滤设置为<ItemLink id="quartz_block" />的<ItemLink id="storage_bus" />，因此它只能破坏<ItemLink id="quartz_block" />。该面板需要附魔精准采集，这样母岩方块在被破坏时不会降级，从而避免面板过早地破坏它。
2. <ItemLink id="storage_bus" /> 将赛特斯石英块存储到<ItemLink id="interface" />中，使得[投水自动化](throw-in-water-automation.md)能够使用它来制作新的<ItemLink id="flawed_budding_quartz" />。

### 母岩放置子网络

母岩放置子网络用于在破除子网络破坏掉旧的耗尽方块后，放置一个新的<ItemLink id="flawed_budding_quartz" />。

1. <ItemLink id="import_bus" /> 从<ItemLink id="interface" />导入一个母岩方块到[网络存储](../ae2-mechanics/import-export-storage.md)中。
2. 子网络上唯一的存储是<ItemLink id="formation_plane" />，它会将母岩方块放置出来。

### 在主网络上

* <ItemLink id="storage_bus" /> 让主网络（以及[充能自动化](charger-automation.md)）能够访问木桶中的所有赛特斯石英水晶。它被设置为高[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)，以便赛特斯石英水晶优先被放回木桶，而不是放入你的主存储。
* <ItemLink id="interface" /> 为母岩放置子网络提供一个<ItemLink id="flawed_budding_quartz" />，并为赛特斯方块破除子网络提供一种将耗尽的方块送回主网络的方式。<ItemLink id="crafting_card" /> 允许该接口向主网络的[自动合成](../ae2-mechanics/autocrafting.md)请求新的母岩方块。