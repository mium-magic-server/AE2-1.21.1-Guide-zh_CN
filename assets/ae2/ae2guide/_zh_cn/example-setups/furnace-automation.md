---
navigation:
  parent: example-setups/example-setups-index.md
  title: 熔炉自动化
  icon: minecraft:furnace
---

# 熔炉自动化

请注意，由于此设置使用了<ItemLink id="pattern_provider" />，它旨在集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。
如果您只想独立自动化熔炉，请使用漏斗和箱子等物品。

自动化<ItemLink id="minecraft:furnace" />比自动化更简单的机器（如[充电器](../example-setups/charger-automation.md)）要复杂一些。
熔炉需要从两个不同的侧面输入，并从第三个侧面输出。需要熔炼的物品必须从顶部面推入，
燃料必须从侧面推入，而结果必须从底部拉出。

这可以通过顶部的<ItemLink id="pattern_provider" />、侧面的<ItemLink id="export_bus" />持续推入燃料以及底部的<ItemLink id="import_bus" />
将结果导入网络来实现。然而，这会使用3个[频道](../ae2-mechanics/channels.md)。

以下是如何仅用1个频道实现的方法：

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/furnace_automation.snbt" />

<BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) 样板供应器：通过使用赛特斯石英扳手使其变为定向变体，并配置相关的处理样板。

        ![铁锭样板](../assets/diagrams/furnace_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (2) 接口：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="1.3 2 1">
        (3) 存储总线 #1：过滤设置为煤炭。
        <ItemImage id="minecraft:coal" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 2 0" max="1 2.3 1">
        (4) 存储总线 #2：使用反相卡过滤设置为黑名单煤炭。
        <Row><ItemImage id="minecraft:coal" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        连接主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置说明

* <ItemLink id="pattern_provider" /> (1) 保持默认配置，并配置相关的<ItemLink id="processing_pattern" />。
    通过使用<ItemLink id="certus_quartz_wrench" />使其变为定向输出。

  ![铁锭样板](../assets/diagrams/furnace_pattern.png)

* <ItemLink id="interface" /> (2) 保持默认配置。
* 第一个<ItemLink id="storage_bus" /> (3) 过滤设置为煤炭，或您想要使用的任何燃料。
* 第二个<ItemLink id="storage_bus" /> (4) 使用<ItemLink id="inverter_card" />过滤设置为黑名单您正在使用的燃料。

## 工作原理

1. <ItemLink id="pattern_provider" />将原料推入<ItemLink id="interface" />。
   （实际上，作为一种优化，它直接通过存储总线推送，就好像它们是供应器面的延伸。物品实际上从未进入接口。）
2. 接口设置为不存储任何物品，因此它尝试将原料推入[网络存储](../ae2-mechanics/import-export-storage.md)。
3. 绿色子网络上唯一的存储是<ItemLink id="storage_bus" />。过滤设置为煤炭的总线通过侧面将煤炭放入熔炉的燃料槽。
    过滤设置为非煤炭的总线通过顶面将待熔炼的物品放入顶部槽。
4. 熔炉执行其熔炼过程。
5. 漏斗从熔炉底部拉出结果，并将其放入供应器的返回槽，将它们返回到主网络。