---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 等级发射器
  icon: level_emitter
  position: 220
categories:
- 设备
item_ids:
- ae2:level_emitter
- ae2:energy_level_emitter
---

# 等级发射器

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/level_emitter.snbt" />
</GameScene>

等级发射器会根据[网络存储](../ae2-mechanics/import-export-storage.md)中某物品的数量发出红石信号。

此外还有一种版本，会根据网络中存储的[能量](../ae2-mechanics/energy.md)来发出红石信号。

即使你实际上没有某种物品，也可以从 JEI/REI 将其拖拽到插槽中。

对发射器使用流体容器（如桶或流体储罐）右键点击，可以设置该流体作为过滤器，而不是桶或储罐物品本身。

它们是[线缆子部件](../ae2-mechanics/cable-subparts.md)。

与其他[设备](../ae2-mechanics/devices.md)不同，等级发射器*不需要*[频道](../ae2-mechanics/channels.md)。

## 设置

*   等级发射器可设置为“大于/等于”或“小于”模式
*   当插入<ItemLink id="crafting_card" />（合成卡）时，可设置为“当物品合成时发出红石信号”或
    “发出红石信号以合成物品”

## 升级

等级发射器支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="fuzzy_card" />（模糊卡）允许发射器按损伤值过滤和/或忽略物品NBT
*   <ItemLink id="crafting_card" />（合成卡）启用合成功能

## 合成功能

如果插入了<ItemLink id="crafting_card" />（合成卡），发射器将切换到合成模式。

此模式提供两个选项：

第一个选项“当物品合成时发出红石信号”，使发射器在你的[自动合成](../ae2-mechanics/autocrafting.md)通过<ItemLink id="pattern_provider" />（样板供应器）合成特定物品时发出红石信号。这对于仅在特定耗电自动化设备实际使用时才将其开启非常有用。

第二个选项“发出红石信号以合成物品”，对于特定用例（如无限农场和仅有概率产出而非保证产出的自动化设备）极其有用。
此设置会为发射器过滤槽中的物品创建一个虚拟[样板](patterns.md)，供[自动合成](../ae2-mechanics/autocrafting.md)使用。
（为正确运作，你的<ItemLink id="pattern_provider" />中**不应存在**同一物品的实际样板）

此“样板”不定义、甚至不关心合成材料。
它只表示“如果从此等级发射器发出红石信号，ME系统将在不久或遥远的未来收到此物品”。这通常用于激活和停用无需输入材料的无限农场，或用于激活[处理递归配方的系统](../example-setups/recursive-crafting-setup.md)（这是标准自动合成无法理解的），例如，如果你有一台复制圆石的机器，则可以设置“1圆石=2圆石”。

## 配方

<RecipeFor id="level_emitter" />

<RecipeFor id="energy_level_emitter" />