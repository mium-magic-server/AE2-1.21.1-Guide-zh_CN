---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 升级卡
  icon: speed_card
  position: 410
categories:
- 工具
item_ids:
- ae2:basic_card
- ae2:advanced_card
- ae2:redstone_card
- ae2:capacity_card
- ae2:void_card
- ae2:fuzzy_card
- ae2:speed_card
- ae2:inverter_card
- ae2:crafting_card
- ae2:equal_distribution_card
- ae2:energy_card
---

# 升级卡

<Row>
  <ItemImage id="redstone_card" scale="2" />

  <ItemImage id="capacity_card" scale="2" />

  <ItemImage id="void_card" scale="2" />

  <ItemImage id="fuzzy_card" scale="2" />

  <ItemImage id="speed_card" scale="2" />

  <ItemImage id="inverter_card" scale="2" />

  <ItemImage id="crafting_card" scale="2" />

  <ItemImage id="equal_distribution_card" scale="2" />

  <ItemImage id="energy_card" scale="2" />
</Row>

升级卡可以改变AE2[设备](../ae2-mechanics/devices.md)和机器的行为，例如提高它们的速度、增加过滤器容量、启用红石控制等。

## 卡基

<Row>
  <ItemImage id="basic_card" scale="2" />

  <ItemImage id="advanced_card" scale="2" />
</Row>

升级卡使用基础卡基或高级卡基制作。

<Row>
  <RecipeFor id="basic_card" />

  <RecipeFor id="advanced_card" />
</Row>

## 红石卡

<ItemImage id="redstone_card" scale="2" />

红石卡可为设备添加红石控制功能，在其GUI中添加一个切换按钮，用于在不同红石信号条件下切换工作模式。

<RecipeFor id="redstone_card" />

## 容量卡

<ItemImage id="capacity_card" scale="2" />

容量卡可以增加输入总线、输出总线、存储总线和成型面板中的过滤器槽位数量。

<RecipeFor id="capacity_card" />

## 溢出销毁卡

<ItemImage id="void_card" scale="2" />

溢出销毁卡可在<ItemLink id="cell_workbench" />中应用于[存储元件](storage_cells.md)，当元件存满时，新进入的物品将被销毁。（请务必为元件设置[分区](cell_workbench.md)！）若与均分卡配合使用，当元件中特定物品的分区存满时，即使其他分区仍有空间，该物品也会被销毁。

<RecipeFor id="void_card" />

## 模糊卡

<ItemImage id="fuzzy_card" scale="2" />

模糊卡允许带有过滤功能的设备和工具根据耐久度进行过滤，和/或忽略物品的NBT标签。这使你可以导出所有铁斧（无论其耐久度和附魔如何），或者仅导出受损的钻石剑，而非完全修复的。

下方表格展示了模糊耐久度比较模式的工作原理，左侧为总线配置，顶部为被比较的物品。

| 25%                    | 10% 损坏的镐 | 30% 损坏的镐 | 80% 损坏的镐 | 完全修复的镐 |
| ---------------------- | ----------- | ----------- | ----------- | ---------- |
| 几乎损坏的镐           | ✅           | \*\*\*\*    | \*\*\*\*    | \*\*\*\*   |
| 完全修复的镐           | \*\*\*\*    | ✅           | ✅           | ✅          |

| 50%                    | 10% 损坏的镐 | 30% 损坏的镐 | 80% 损坏的镐 | 完全修复的镐 |
| ---------------------- | ----------- | ----------- | ----------- | ---------- |
| 几乎损坏的镐           | ✅           | ✅           | \*\*\*\*    | \*\*\*\*   |
| 完全修复的镐           | \*\*\*\*    | \*\*\*\*    | ✅           | ✅          |

| 75%                    | 10% 损坏的镐 | 30% 损坏的镐 | 80% 损坏的镐 | 完全修复的镐 |
| ---------------------- | ----------- | ----------- | ----------- | ---------- |
| 几乎损坏的镐           | ✅           | ✅           | \*\*\*\*    | \*\*\*\*   |
| 完全修复的镐           | \*\*\*\*    |             | ✅           | ✅          |

| 99%                    | 10% 损坏的镐 | 30% 损坏的镐 | 80% 损坏的镐 | 完全修复的镐 |
| ---------------------- | ----------- | ----------- | ----------- | ---------- |
| 几乎损坏的镐           | ✅           | ✅           | ✅           | \*\*\*\*   |
| 完全修复的镐           | \*\*\*\*    | \*\*\*\*    | \*\*\*\*    | ✅          |

| 忽略                   | 10% 损坏的镐 | 30% 损坏的镐 | 80% 损坏的镐 | 完全修复的镐 |
| ---------------------- | ----------- | ----------- | ----------- | ---------- |
| 几乎损坏的镐           | ✅           | ✅           | ✅           | **✅**      |
| 完全修复的镐           | **✅**       | **✅**       | **✅**       | ✅          |

<RecipeFor id="fuzzy_card" />

## 加速卡

<ItemImage id="speed_card" scale="2" />

加速卡可以提升设备运行速度，使输入和输出总线每次操作移动更多物品，并加快压印器和组装器的运作速度。

<RecipeFor id="speed_card" />

## 反相卡

<ItemImage id="inverter_card" scale="2" />

反相卡可将设备和工具中的过滤器模式从白名单切换为黑名单。

<RecipeFor id="inverter_card" />

## 合成卡

<ItemImage id="crafting_card" scale="2" />

合成卡允许设备向你的[自动合成](../ae2-mechanics/autocrafting.md)系统发送合成请求，以获取其所需的物品。

<RecipeFor id="crafting_card" />

## 均分卡

<ItemImage id="equal_distribution_card" scale="2" />

均分卡可在<ItemLink id="cell_workbench" />中应用于[存储元件](storage_cells.md)，并根据其[分区](cell_workbench.md)设置将元件划分为大小相等的多个分区。这可以防止单一物品类型完全占满整个元件。

<RecipeFor id="equal_distribution_card" />

## 能量卡

<ItemImage id="energy_card" scale="2" />

能量卡可为某些工具（如便携终端）增加能量存储容量，并提高<ItemLink id="vibration_chamber" />（谐振仓）的效率。

<RecipeFor id="energy_card" />