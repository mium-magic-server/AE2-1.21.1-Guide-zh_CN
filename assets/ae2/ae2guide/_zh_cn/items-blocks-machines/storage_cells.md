---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 存储元件
  icon: item_storage_cell_1k
  position: 410
categories:
- 工具
item_ids:
- ae2:item_cell_housing
- ae2:fluid_cell_housing
- ae2:cell_component_1k
- ae2:cell_component_4k
- ae2:cell_component_16k
- ae2:cell_component_64k
- ae2:cell_component_256k
- ae2:item_storage_cell_1k
- ae2:item_storage_cell_4k
- ae2:item_storage_cell_16k
- ae2:item_storage_cell_64k
- ae2:item_storage_cell_256k
- ae2:fluid_storage_cell_1k
- ae2:fluid_storage_cell_4k
- ae2:fluid_storage_cell_16k
- ae2:fluid_storage_cell_64k
- ae2:fluid_storage_cell_256k
---

# 存储元件

<Column>
  <Row>
    <ItemImage id="item_storage_cell_1k" scale="4" />

    <ItemImage id="item_storage_cell_4k" scale="4" />

    <ItemImage id="item_storage_cell_16k" scale="4" />

    <ItemImage id="item_storage_cell_64k" scale="4" />

    <ItemImage id="item_storage_cell_256k" scale="4" />
  </Row>

  <Row>
    <ItemImage id="fluid_storage_cell_1k" scale="4" />

    <ItemImage id="fluid_storage_cell_4k" scale="4" />

    <ItemImage id="fluid_storage_cell_16k" scale="4" />

    <ItemImage id="fluid_storage_cell_64k" scale="4" />

    <ItemImage id="fluid_storage_cell_256k" scale="4" />
  </Row>
</Column>

存储元件是应用能源中的主要存储方式之一。它们可放入<ItemLink id="drive" />或<ItemLink id="chest" />中。

关于其以字节和类型计算的容量说明，请参阅[字节与类型](../ae2-mechanics/bytes-and-types.md)。

如果元件为空，手持元件时按住Shift+右键点击可以从中取出存储组件。

<Row>
    <Recipe id="upgrade/item_storage_cell_1k_to_4k" />

    你可以在工作台中将其与更高等级的存储组件合成来升级存储元件。其内容将被保留，并返还低等级的组件。
</Row>

## 不同物品类型数量下的存储容量

[类型的初始开销](../ae2-mechanics/bytes-and-types.md)使得存储1种类型的元件容量是存储全部63种类型时的2倍。

| 元件                                     | 存储1种类型时的总容量 | 存储63种类型时的总容量 |
| ---------------------------------------- | -------------------: | --------------------: |
| <ItemLink id="item_storage_cell_1k" />   |                8,128 |                 4,160 |
| <ItemLink id="item_storage_cell_4k" />   |               32,512 |                16,640 |
| <ItemLink id="item_storage_cell_16k" />  |              130,048 |                66,560 |
| <ItemLink id="item_storage_cell_64k" />  |              520,192 |               266,240 |
| <ItemLink id="item_storage_cell_256k" /> |            2,080,768 |             1,064,960 |


## 分区

元件可以设置过滤器以仅接受特定物品，类似于<ItemLink id="storage_bus" />的过滤功能。这需要在<ItemLink id="cell_workbench" />中完成。

即使你实际上没有某种物品，也可以从JEI/REI将其拖入槽位。

## 升级

存储元件支持以下[升级卡](upgrade_cards.md)，通过<ItemLink id="cell_workbench" />插入：

*   <ItemLink id="fuzzy_card" />（不适用于流体元件）允许元件按损坏程度分区和/或忽略物品NBT
*   <ItemLink id="inverter_card" />将过滤器从白名单切换为黑名单
*   <ItemLink id="equal_distribution_card" />为每种类型分配相同的元件字节空间，防止单一类型占满整个元件
*   <ItemLink id="void_card" />在元件已满时（或在使用均分卡时特定类型的分配空间已满）销毁放入的物品，可用于防止农场堵塞。使用时务必设置好分区！
*   便携元件可以接受<ItemLink id="energy_card" />以增加其电池容量

## 染色

便携物品和流体元件可以通过与染料合成来染色，类似于皮革盔甲的染色方式。

# 元件外壳

存储元件可以由存储组件和外壳制成，或者将存储组件放在合成格中央并用外壳材料环绕来合成：

<Row>
  <Recipe id="network/cells/item_storage_cell_1k" />

  <Recipe id="network/cells/item_storage_cell_1k_storage" />
</Row>

外壳本身的合成方式如下：

<Row>
  <RecipeFor id="item_cell_housing" />

  <RecipeFor id="fluid_cell_housing" />
</Row>

# 存储组件

存储组件是所有AE2元件的核心，决定了元件的容量。每提升一级，容量增加4倍，并需要3个前一级的组件。

<Column>
  <Row>
    <RecipeFor id="cell_component_1k" />

    <RecipeFor id="cell_component_4k" />

    <RecipeFor id="cell_component_16k" />
  </Row>

  <Row>
    <RecipeFor id="cell_component_64k" />

    <RecipeFor id="cell_component_256k" />
  </Row>
</Column>

# 物品存储元件

物品存储元件最多可容纳63种不同类型的物品，并提供所有标准容量。

<Column>
  <Row>
    <Recipe id="network/cells/item_storage_cell_1k_storage" />

    <Recipe id="network/cells/item_storage_cell_4k_storage" />

    <Recipe id="network/cells/item_storage_cell_16k_storage" />
  </Row>

  <Row>
    <Recipe id="network/cells/item_storage_cell_64k_storage" />

    <Recipe id="network/cells/item_storage_cell_256k_storage" />
  </Row>
</Column>

## 便携物品存储

这些元件如同口袋里的微型<ItemLink id="chest" />，或是一种背包。它们可以在<ItemLink id="charger" />中充电。

与标准存储元件不同，这些元件的类型容量会随着字节容量的增加而*减少*，并且总字节容量只有标准的一半。

除了所有元件都能接受的升级卡之外，这些元件还可以接受<ItemLink id="energy_card" />来升级其内部电池。

<Column>
  <Row>
    <RecipeFor id="portable_item_cell_1k" />

    <RecipeFor id="portable_item_cell_4k" />

    <RecipeFor id="portable_item_cell_16k" />
  </Row>

  <Row>
    <RecipeFor id="portable_item_cell_64k" />

    <RecipeFor id="portable_item_cell_256k" />
  </Row>
</Column>

# 流体存储元件

流体存储元件最多可容纳5种不同类型的流体，并提供所有标准容量。

<Column>
  <Row>
    <Recipe id="network/cells/fluid_storage_cell_1k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_4k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_16k_storage" />
  </Row>

  <Row>
    <Recipe id="network/cells/fluid_storage_cell_64k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_256k_storage" />
  </Row>
</Column>

## 便携流体存储

这些元件如同口袋里的微型<ItemLink id="chest" />，或是一种背包。它们可以在<ItemLink id="charger" />中充电。

与标准存储元件不同，这些元件的类型容量会随着字节容量的增加而*减少*，并且总字节容量只有标准的一半。

除了所有元件都能接受的升级卡之外，这些元件还可以接受<ItemLink id="energy_card" />来升级其内部电池。

<Column>
  <Row>
    <RecipeFor id="portable_fluid_cell_1k" />

    <RecipeFor id="portable_fluid_cell_4k" />

    <RecipeFor id="portable_fluid_cell_16k" />
  </Row>

  <Row>
    <RecipeFor id="portable_fluid_cell_64k" />

    <RecipeFor id="portable_fluid_cell_256k" />
  </Row>
</Column>

# 创造存储元件

<Row>
  <ItemImage id="creative_storage_cell" scale="2" />
</Row>

创造元件**不提供无限存储**。相反，它们会作为你所[分区](cell_workbench.md)设置的物品或流体的无限来源与接收端。