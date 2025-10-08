---
navigation:
  parent: example-setups/example-setups-index.md
  title: 自动矿石时运处理装置
  icon: minecraft:raw_iron
---

# 自动化矿石时运处理

<ItemLink id="annihilation_plane" /> 可以附魔任何镐子附魔，包括时运，因此一个明显的用例是给几个破坏面板附上时运，并用 <ItemLink id="formation_plane" /> 和 <ItemLink id="annihilation_plane" /> 快速放置和破坏矿石。

请注意，由于 <ItemLink id="import_bus" /> 需要“加速启动”，该装置启动时会较慢，几秒钟后才会达到全速。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/ore_fortuner.snbt" />

  <BoxAnnotation color="#dddddd" min="2.7 0 2" max="3 1 3">
        (1) 输入总线：内置有几张加速卡。
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 2" max="2 1 2.3">
        (2) 成型面板：保持默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 0.7" max="2 1 1">
        (3) 破坏面板：无需配置图形用户界面，但已附魔时运。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 0 0" max="3 1 1">
        (4) 存储总线：保持默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="3.5 0.5 2.5" color="#00ff00">
        输入
    </DiamondAnnotation>

<DiamondAnnotation pos="3.5 0.5 0.5" color="#00ff00">
        输出
    </DiamondAnnotation>

<DiamondAnnotation pos="4 0.5 1.5" color="#00ff00">
        连接主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

*   <ItemLink id="import_bus" /> (1) 内置有几张 <ItemLink id="speed_card" />。成型面板阵列规模越大，所需的加速卡就越多，因为它们会使输入总线一次性拉取更多物品。
*   <ItemLink id="formation_plane" />s (2) 保持默认配置。
*   <ItemLink id="annihilation_plane" />s (3) 没有图形用户界面且无法配置，但已附魔时运。
*   <ItemLink id="storage_bus" /> (4) 保持默认配置。

## 工作原理

1.  绿色子网络上的 <ItemLink id="import_bus" /> 将方块从第一个桶中导入至 [网络存储](../ae2-mechanics/import-export-storage.md)。
2.  绿色子网络上唯一的存储是 <ItemLink id="formation_plane" />，它会放置这些方块。
3.  橙色子网络上的 <ItemLink id="annihilation_plane" /> 破坏这些方块，并对它们应用时运效果。
4.  橙色子网络上的 <ItemLink id="storage_bus" /> 将破坏后的产物存储到第二个桶中。