---
navigation:
  parent: example-setups/example-setups-index.md
  title: 半自动赛特斯农场
  icon: certus_quartz_crystal
  position: 115
---

# 半自动赛特斯农场

遗憾的是，[简易赛特斯农场](simple-certus-farm.md)需要一个 <ItemLink id="flawless_budding_quartz" /> 才能完全自动化运行。这需要借助 [空间IO](../ae2-mechanics/spatial-io.md) 或在 [陨石](../ae2-mechanics/meteorites.md) 上建造农场。

然而，AE2 可以放置和破坏方块，因此你的农场或许可以 *为你替换赛特斯石英母岩*。（你需要定期向输入桶中放入一些 <ItemLink id="flawed_budding_quartz" />，并从已耗尽的石英母岩桶中取出 <ItemLink id="quartz_block" />）

要实现完全自动化，请参阅 [高级赛特斯农场](advanced-certus-farm.md)。

这个农场比 [简易赛特斯农场](simple-certus-farm.md) 稍微复杂一些，因为它实际上是三个独立的装置挤在一起。

关于预计速度，请参阅 [赛特斯石英生长](../ae2-mechanics/certus-growth.md)。

**这是一个复杂的构建，部分结构隐藏在其它部件后面，请旋转视角从各个角度查看**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/semiauto_certus_farm.snbt" />

  <BoxAnnotation color="#ddaaaa" min="3.7 2 1" max="4 3 2">
        (1) 破坏面板 #1：无配置界面，但可附魔时运。
  </BoxAnnotation>

  <BoxAnnotation color="#ddaaaa" min="2 2 1" max="2.3 3 2">
        (2) 存储总线 #1：过滤设置为赛特斯石英水晶。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 2.5 1.5" color="#ff0000">
    晶簇破除子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#aaddaa" min="3.7 1 1" max="4 2 2">
        (3) 破坏面板 #2：无配置界面，但需附魔精准采集。
  </BoxAnnotation>

  <BoxAnnotation color="#aaddaa" min="2 1 1" max="2.3 2 2">
        (4) 存储总线 #2：过滤设置为赛特斯石英块。
        <BlockImage id="quartz_block" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 1.5 1.5" color="#00ff00">
    石英块破除子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#ffddaa" min="4 0.7 1" max="5 1 2">
        (5) 成型面板：保持默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#ffddaa" min="2 0 1" max="2.3 1 2">
        (6) 输入总线：保持默认配置。
  </BoxAnnotation>

  <DiamondAnnotation pos="3 0.5 1.5" color="#ddcc00">
    母岩放置子网络
  </DiamondAnnotation>

  <BoxAnnotation color="#aaaadd" min="0.7 2 1" max="1 3 2">
        (7) 存储总线 #3：过滤设置为赛特斯石英水晶。其优先级设置高于主存储器。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

    <DiamondAnnotation pos="1.5 0.5 1.5" color="#00ff00">
        手动放入有瑕的赛特斯石英母岩。
        <BlockImage id="flawed_budding_quartz" scale="2" />
    </DiamondAnnotation>

    <DiamondAnnotation pos="1.5 1.5 1.5" color="#00ff00">
        手动取出赛特斯石英块。
        <BlockImage id="quartz_block" scale="2" />
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="165" pitch="5" />
</GameScene>

## 配置

### 晶簇破除器：

* 第一个 <ItemLink id="annihilation_plane" /> (1) 无配置界面，但可附魔时运。
* 第一个 <ItemLink id="storage_bus" /> (2) 过滤设置为 <ItemLink id="certus_quartz_crystal" />。

### 石英块破除器：

* 第二个 <ItemLink id="annihilation_plane" /> (3) 无配置界面，但必须附魔精准采集。
* 第二个 <ItemLink id="storage_bus" /> (4) 过滤设置为 <ItemLink id="quartz_block" />。

### 母岩放置器：

* <ItemLink id="formation_plane" /> (5) 保持默认配置。
* <ItemLink id="import_bus" /> (6) 保持默认配置。

### 在主网络上：

* 第三个 <ItemLink id="storage_bus" /> (7) 过滤设置为 <ItemLink id="certus_quartz_crystal" />，并将其 [优先级](../ae2-mechanics/import-export-storage.md#storage-priority) 设置得高于你的主存储器。

## 工作原理

### 晶簇破除器：

晶簇破除子网络的工作原理与 [简易赛特斯农场](simple-certus-farm.md) 中的子网络非常相似。

1. <ItemLink id="annihilation_plane" /> 尝试破坏其前方的方块，但由于子网络上唯一的存储器是过滤了 <ItemLink id="certus_quartz_crystal" /> 的 <ItemLink id="storage_bus" />，因此只能破坏 <ItemLink id="quartz_cluster" />。
2. <ItemLink id="storage_bus" /> 将赛特斯石英水晶存储到桶中。

### 石英块破除器

石英块破除子网络用于在耗尽的母岩方块变为普通的 <ItemLink id="quartz_block" /> 后将其破坏。其工作原理与晶簇破除器类似。

1. <ItemLink id="annihilation_plane" /> 尝试破坏其前方的方块，但由于子网络上唯一的存储器是过滤了 <ItemLink id="quartz_block" /> 的 <ItemLink id="storage_bus" />，因此只能破坏 <ItemLink id="quartz_block" />。该面板需要附魔精准采集，这样母岩方块在被破坏时不会降级，面板也就不会过早地破坏它。
2. <ItemLink id="storage_bus" /> 将赛特斯石英块存储到已耗尽的母岩桶中，你需要手动将其与 <ItemLink id="charged_certus_quartz_crystal" /> 一起放入水中以刷新它。

### 母岩放置器

母岩放置子网络用于在破除子网络破坏掉旧的耗尽母岩后，放置一个新的 <ItemLink id="flawed_budding_quartz" />。

1. <ItemLink id="import_bus" /> 从输入桶中导入一个母岩方块。
2. 子网络上唯一的存储器是 <ItemLink id="formation_plane" />，它会放置母岩方块。

### 在主网络上

* <ItemLink id="storage_bus" /> 让主网络（以及 [充能自动化](charger-automation.md)）能够访问桶中所有的赛特斯石英水晶。它被设置为高 [优先级](../ae2-mechanics/import-export-storage.md#storage-priority)，以便赛特斯石英水晶优先被放回桶中，而不是存入你的主存储器。