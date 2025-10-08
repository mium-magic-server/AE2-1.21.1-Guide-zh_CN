---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 充电器自动化
  icon: charger
---

# 充电器自动化

请注意，由于使用了 <ItemLink id="pattern_provider" />，此配置旨在集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。
如果您只想独立自动化 <ItemLink id="charger" />，请使用漏斗、箱子等设备。

自动化 <ItemLink id="charger" /> 相当简单。<ItemLink id="pattern_provider" /> 将原料推入充电器，然后一个[管道子网](pipe-subnet.md)
或其他物品管道将结果推回供应器。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/charger_automation.snbt" />

<BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) 样板供应器：默认配置，带有相关的处理样板。同时为充电器提供能量。

        ![充电器样板](../assets/diagrams/charger_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 0" max="1 1.3 1">
        (2) 输入总线：默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (3) 存储总线：默认配置。
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        连接到主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

*   <ItemLink id="pattern_provider" /> (1) 处于默认配置，带有相关的 <ItemLink id="processing_pattern" />。
    它还为 <ItemLink id="charger" /> 提供[能量](../ae2-mechanics/energy.md)，因为它本身就像一个[线缆](../items-blocks-machines/cables.md)。

    ![充电器样板](../assets/diagrams/charger_pattern.png)

*   <ItemLink id="import_bus" /> (2) 处于默认配置。
*   <ItemLink id="storage_bus" /> (3) 处于默认配置。

## 工作原理

1.  <ItemLink id="pattern_provider" /> 将原料推入 <ItemLink id="charger" />。
2.  充电器进行充电操作。
3.  绿色子网上的 <ItemLink id="import_bus" /> 将结果从充电器中取出，并尝试将其存入[网络存储](../ae2-mechanics/import-export-storage.md)。
4.  绿色子网上唯一的存储设备是 <ItemLink id="storage_bus" />，它将结果物品存入样板供应器，从而将其返回到主网络。