---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 接口
  icon: interface
  position: 210
categories:
- 设备
item_ids:
- ae2:interface
- ae2:cable_interface
---

# 接口

<Row gap="20">
<BlockImage id="interface" scale="8" />
<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/cable_interface.snbt" />
</GameScene>
</Row>

接口就像一个小的物品栏和流体储罐，它会根据你在其槽位中设置的库存量，从[网络存储](../ae2-mechanics/import-export-storage.md)中填充或清空自身。
它试图在一个游戏刻内完成此操作，因此每个游戏刻最多可以填充或清空 9 组物品，如果你有快速的物品管道，这将是一种快速的导入或导出方法。

另一个有用的特性是，虽然大多数流体储罐只能存储 1 种流体，但接口最多可以存储 9 种流体以及物品。
它们本质上就是带有一些额外功能的箱子/多流体储罐，你可以通过将它们与任何网络断开连接来禁用这些额外功能。
因此，在一些你想要存储少量多种不同物品的特殊情况下，它们会很有用。

## 接口的内部工作原理

如前所述，接口本质上是一个带有一些超级<ItemLink id="import_bus" />和<ItemLink id="export_bus" />的箱子/储罐，并附带一堆<ItemLink id="level_emitter" />。

<GameScene zoom="3" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_internals.snbt" />

  <BoxAnnotation color="#dddddd" min="1.3 0.3 1.3" max="9.7 1 1.7">
        一堆用于控制请求库存数量的等级发射器
        <GameScene zoom="4" background="transparent">
        <ImportStructure src="../assets/blocks/level_emitter.snbt" />
        </GameScene>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1.3 4 1.3" max="9.7 4.7 1.7">
        一堆用于控制请求库存数量的等级发射器
        <GameScene zoom="4" background="transparent">
        <ImportStructure src="../assets/blocks/level_emitter.snbt" />
        </GameScene>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1.3 1.3 1.3" max="9.7 2 1.7">
        一堆超级输入总线，每个游戏刻可以传输 1 组物品
        <GameScene zoom="4" background="transparent">
        <ImportStructure src="../assets/blocks/import_bus.snbt" />
        </GameScene>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1.3 3 1.3" max="9.7 3.7 1.7">
        一堆超级输出总线，每个游戏刻可以传输 1 组物品
        <GameScene zoom="4" background="transparent">
        <ImportStructure src="../assets/blocks/export_bus.snbt" />
        </GameScene>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 2 1" max="10 3 2">
        9 个独立的内部槽位
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="15" />
</GameScene>

## 特殊交互

接口与其他 AE2 [设备](../ae2-mechanics/devices.md)还有一些特殊功能：

一个<ItemLink id="storage_bus" />连接到一个未配置的接口时，会将其网络的整个[网络存储](../ae2-mechanics/import-export-storage.md)呈现给存储总线的网络，就好像接口的网络是一个大箱子，而存储总线就放在上面一样。
在接口的过滤槽位中设置要库存的物品会禁用此功能。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_storage.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

样板供应器与[子网络](../ae2-mechanics/subnetworks.md)上的接口有特殊交互：如果接口未配置，供应器将完全跳过该接口，直接推送到该子网络的[存储](../ae2-mechanics/import-export-storage.md)中，跳过接口且不会用配方批次填充它，更重要的是，只有在存储中有空间时才会插入下一批次。

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/provider_interface_storage.snbt" />

<BoxAnnotation color="#dddddd" min="2.7 0 1" max="3 1 2">
        接口（必须是平坦变体，非完整方块）
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 4">
        存储总线
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 0 0" max="1 1 4">
        你想要供应样板的目标位置（多个机器，或一个机器的多个面）
  </BoxAnnotation>

<IsometricCamera yaw="185" pitch="30" />
</GameScene>

## 变体

接口有两种不同的变体：普通型和扁平型/[线缆子部件](../ae2-mechanics/cable-subparts.md)。这影响了它们的物品栏可以从哪些面被访问以及它们提供网络连接的方式。

*   普通接口允许从所有面推入、拉出和访问其物品栏，并且像大多数 AE2 机器一样，其行为类似于一根电缆，向所有面提供网络连接。

*   扁平接口是[线缆子部件](../ae2-mechanics/cable-subparts.md)，因此可以在同一根线缆上放置多个，从而实现紧凑的设置。
    它们允许从其正面推入、拉出和访问其物品栏，但不在其正面提供网络连接。

接口可以在合成网格中在普通型和扁平型之间切换。

## 设置

接口上方的槽位决定了接口自身设置的库存物品。当在其中放置物品或从 JEI/REI 拖入物品时，会出现一个扳手图标，允许你设置数量。

使用流体容器（如桶或流体储罐）右键单击，可以将该流体设置为过滤器，而不是桶或储罐物品本身。

当你将一个槽位设置为库存模式时，它也会阻止外部机器向该槽位插入任何其他物品。

## 升级

接口支持以下[升级](upgrade_cards.md)：

*   <ItemLink id="fuzzy_card" /> 允许总线根据损坏程度进行过滤和/或忽略物品 NBT 数据
*   <ItemLink id="crafting_card" /> 允许接口向你的[自动合成](../ae2-mechanics/autocrafting.md)系统发送合成请求以获取其所需的物品。它会尽可能先从存储中提取物品，然后再请求合成新物品。

## 优先级

可以通过点击 GUI 右上角的扳手来设置优先级。优先级较高的接口将比优先级较低的接口优先获得物品。

## 配方

<Recipe id="network/blocks/interfaces_interface" />

<RecipeFor id="cable_interface" />