---
navigation:
  parent: example-setups/example-setups-index.md
  title: 物品/流体“管道”子网络
  icon: storage_bus
---

# 物品/流体“管道”子网络

一种使用AE2[设备](../ae2-mechanics/devices.md)模拟物品和/或流体管道的方法，适用于任何您会用到物品或流体管道的场景。
这包括将合成结果返回到<ItemLink id="pattern_provider" />（样板供应器）。

通常有两种不同的方法可以实现此功能：

## 输入总线 -> 存储总线

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/import_storage_pipe.snbt" />

<BoxAnnotation color="#dddddd" min="3.7 0 0" max="4 1 1">
        (1) 输入总线：可设置过滤器。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 1">
        (2) 存储总线：可设置过滤器。此总线（以及您希望作为目的地的其他存储总线）
        必须是网络中唯一的存储设备。
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 0.5" color="#00ff00">
        来源
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0.5" color="#00ff00">
        目的地
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

源物品栏上的<ItemLink id="import_bus" />（1）（输入总线）会导入物品或流体，并尝试将其存入[网络存储](../ae2-mechanics/import-export-storage.md)。
由于网络中唯一的存储设备是<ItemLink id="storage_bus" />（2）（存储总线）（这就是为什么这是一个子网络而非您的主网络），物品或流体
会被放入目标物品栏，从而完成传输。能量由<ItemLink id="quartz_fiber" />（石英纤维）提供。
输入总线和存储总线都可以设置过滤器，但如果不应用任何过滤器，此设置将传输所有它能访问的内容。
此设置也适用于多个输入总线和多个存储总线。

## 存储总线 -> 输出总线

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/storage_export_pipe.snbt" />

<BoxAnnotation color="#dddddd" min="3.7 0 0" max="4 1 1">
        (1) 存储总线：可设置过滤器。此总线（以及您希望作为来源的其他存储总线）
        必须是网络中唯一的存储设备。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 1">
        (2) 输出总线：必须设置过滤器。
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 0.5" color="#00ff00">
        来源
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0.5" color="#00ff00">
        目的地
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

目标物品栏上的<ItemLink id="export_bus" />（输出总线）会尝试从其过滤器中拉取物品，这些物品来自[网络存储](../ae2-mechanics/import-export-storage.md)。
由于网络中唯一的存储设备是<ItemLink id="storage_bus" />（存储总线）（这就是为什么这是一个子网络而非您的主网络），物品或流体
会从源物品栏中拉取，从而完成传输。能量由<ItemLink id="quartz_fiber" />（石英纤维）提供。
因为输出总线必须设置过滤器才能工作，所以此设置仅在您为输出总线设置过滤器时运行。
此设置也适用于多个存储总线和多个输出总线。

## 无效的设置（输入总线 -> 输出总线）

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/import_export_pipe.snbt" />

<BoxAnnotation color="#dd3333" min="3.7 0 0" max="4