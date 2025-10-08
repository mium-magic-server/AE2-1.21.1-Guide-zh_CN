---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 投掷入水自动化
  icon: fluix_crystal

# 投掷入水配方自动化

请注意，由于此装置使用了<ItemLink id="pattern_provider" />（样板供应器），其设计目的是集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。

部分配方需要将物品投入水中（不过类似装置也可用于将物品投掷到其他位置）。
这可以通过<ItemLink id="formation_plane" />（成型面板）、<ItemLink id="annihilation_plane" />（破坏面板）以及一些辅助基础设施实现（本质上是两个经过修改的[管道子网络](pipe-subnet.md)）。

此装置旨在与[充能器自动化](charger-automation.md)配合使用，以提供<ItemLink id="charged_certus_quartz_crystal" />（充能赛特斯石英水晶）。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/throw_in_water.snbt" />

<BoxAnnotation color="#dddddd" min="2 0 1" max="3 1 2">
        (1) 样板供应器：保持默认配置，并载入相关处理样板。

        ![福鲁伊克斯水晶配方](../assets/diagrams/fluix_pattern_small.png) ![有瑕母岩配方](../assets/diagrams/flawed_budding_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1.7 0 1" max="2 1 2">
        (2) 接口：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 .7 1" max="2 1 2">
        (3) 成型面板：设置为将输入物品以掉落物形式抛出。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 2 1" max="2 2.3 2">
        (4) 破坏面板：无配置界面。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 1 1" max="3 1.3 2">
        (5) 存储总线：设置为过滤配方输出物品
        <Row><ItemImage id="fluix_crystal" scale="2" /><BlockImage id="flawless_budding_quartz" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="3.9 0.5 1.5" color="#00ff00">
        连接至主网络与充能器自动化系统
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/charger_automation.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
    </DiamondAnnotation>

  <IsometricCamera yaw="180" pitch="0" />
</GameScene>

## 配置与样板

* <ItemLink id="pattern_provider" />（样板供应器）(1) 保持默认配置，并载入相关<ItemLink id="processing_pattern" />（处理样板）
  * 对于<ItemLink id="fluix_crystal" />（福鲁伊克斯水晶），使用JEI/REI显示的默认配方即可：

    ![福鲁伊克斯水晶配方](../assets/diagrams/fluix_pattern.png)

  * 对于<ItemLink id="flawed_budding_quartz" />（有瑕的赛特斯石英母岩），最好直接使用<ItemLink id="quartz_block" />（石英块）合成，
    这样可以避免因某个配方的输入物品是另一个配方的输出物品而导致存储总线无法正确过滤的问题：

    ![有瑕母岩配方](../assets/diagrams/flawed_budding_pattern.png)

* <ItemLink id="interface" />（接口）(2) 保持默认配置。
* <ItemLink id="formation_plane" />（成型面板）(3) 设置为将输入物品以掉落物形式抛出。
* <ItemLink id="annihilation_plane" />（破坏面板）(4) 无配置界面，无法进行设置。
* <ItemLink id="storage_bus" />（存储总线）(5) 设置为仅允许配方输出物品存入。

## 工作原理

1.  <ItemLink id="pattern_provider" />（样板供应器）将合成材料推送至其侧面的<ItemLink id="interface" />（接口）中，该接口位于绿色子网络
2.  接口（默认配置为不存储任何物品）会尝试将其内容物推送至[网络存储](../ae2-mechanics/import-export-storage.md)中
3.  绿色子网络上唯一的存储设备是<ItemLink id="formation_plane" />（成型面板），它会将接收到的物品以掉落物形式投入水中
4.  橙色子网络上的<ItemLink id="annihilation_plane" />（破坏面板）会尝试拾取刚被抛出的物品，但无法成功，因为
    位于样板供应器顶部的<ItemLink id="storage_bus" />（存储总线）（橙色子网络上唯一的存储设备）被设置为仅允许可能的合成产物存入
5.  物品在世界中完成其转化过程
6.  此时破坏面板可以拾取其前方的物品，因为存储总线已允许存储这些物品
7.  存储总线将最终产物存入样板供应器，使其返回主网络