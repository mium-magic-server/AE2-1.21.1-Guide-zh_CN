---
navigation:
  parent: example-setups/example-setups-index.md
  title: 递归合成配置
  icon: minecraft:netherite_upgrade_smithing_template
---

# 递归合成配置

如[自动合成](../ae2-mechanics/autocrafting.md)中所述，自动合成规划算法无法处理主输出物是输入物之一的配方。例如，它无法处理克隆<ItemLink id="minecraft:netherite_upgrade_smithing_template" />。

一种解决方案是利用<ItemLink id="level_emitter" />的能力来模拟[样板](../items-blocks-machines/patterns.md)。

这将被用来启动一个持续执行合成的小型装置。在本例中，我们将研究一个用于克隆<ItemLink id="minecraft:netherite_upgrade_smithing_template" />的装置。

<RecipeFor id="minecraft:netherite_upgrade_smithing_template" />

***

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/recursive_recipe_setup.snbt" />

  <BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) 接口：设置为库存所需的额外材料：钻石和下界岩。
        <Row><ItemImage id="minecraft:diamond" scale="2" /> <ItemImage id="minecraft:netherrack" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 1 0.3" max="2.7 1.3 0.7">
        (2) 等级发射器：配置为“下界合金锻造模板”，设置为“发出红石信号以合成物品”。
        <Row><ItemImage id="minecraft:netherite_upgrade_smithing_template" scale="2" /> <ItemImage id="crafting_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 0 0" max="2.3 1 1">
        (3) 输入总线 #1：过滤为接口库存的物品。带有一张红石卡。红石模式设置为“有信号时激活”。
        <Row>
        <ItemImage id="minecraft:diamond" scale="2" />
        <ItemImage id="minecraft:netherrack" scale="2" />
        <ItemImage id="redstone_card" scale="2" />
        </Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 1" max="4 1.3 2">
        (4) 存储总线 #1：设置为比另一个存储总线更高的优先级。非常重要。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 0 1" max="4 1 2">
        (5) 分子装配室：内含复制锻造模板的样板。

        ![样板](../assets/diagrams/smithing_template_pattern_small.png)

        当你首次建造时，还需要手动放入一个锻造模板。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 0 1" max="3 1 2">
        (6) 输入总线 #2：保持默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 0 1" max="2 1 1.3">
        (7) 存储总线 #2：过滤为“下界合金锻造模板”。设置为比另一个存储总线更低的优先级。
        <ItemImage id="minecraft:netherite_upgrade_smithing_template" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="15" pitch="30" />
</GameScene>

## 配置

* <ItemLink id="interface" /> (1) 设置为库存所需的额外材料：钻石和下界岩。
* <ItemLink id="level_emitter" /> (2) 配置为“下界合金锻造模板”，并设置为“发出红石信号以合成物品”。
* 第一个<ItemLink id="import_bus" /> (3) 过滤为接口库存的物品。它带有一张红石卡。红石模式设置为“有信号时激活”。
* 第一个<ItemLink id="storage_bus" /> (4) 设置为比第二个存储总线更高的[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)。
* <ItemLink id="molecular_assembler" /> (5) 含有复制锻造模板的样板，并且已手动插入了一个锻造模板。

  ![样板](../assets/diagrams/smithing_template_pattern.png)

* 第二个<ItemLink id="import_bus" /> (6) 保持默认配置。
* 第二个<ItemLink id="storage_bus" /> (7) 过滤为“下界合金锻造模板”。它拥有比第一个存储总线更低的[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)。

## 工作原理

1. 由于插入了<ItemLink id="crafting_card" />并设置为“发出红石信号以合成物品”，<ItemLink id="level_emitter" />模拟了一个[样板](../items-blocks-machines/patterns.md)。因此，“下界合金锻造模板”在[终端](../items-blocks-machines/terminals.md)中显示为可[自动合成](../ae2-mechanics/autocrafting.md)的有效物品。
2. 当收到来自玩家或系统自身的合成该物品的请求时，等级发射器启动。
3. 第一个<ItemLink id="import_bus" />被等级发射器激活，并从<ItemLink id="interface" />中提取库存的材料。
4. 网络中唯一能够存储这些材料的<ItemLink id="storage_bus" />是装配室上的那个。
5. <ItemLink id="molecular_assembler" />接收材料（内部已有一个锻造模板），并执行合成，产生2个锻造模板。
6. 第二个<ItemLink id="import_bus" />提取1个锻造模板。
7. 第一个存储总线具有更高的优先级，因此该锻造模板会回到装配室中。
8. 第二个<ItemLink id="import_bus" />提取1个锻造模板。
9. 装配室无法接收另一个锻造模板，因此第二个锻造模板进入优先级较低的存储总线，插入到接口中。
10. <ItemLink id="interface" />未设置为库存锻造模板，因此将其插入到网络中。