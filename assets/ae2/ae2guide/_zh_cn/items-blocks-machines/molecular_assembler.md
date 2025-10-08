---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 分子装配室
  icon: molecular_assembler
  position: 310
categories:
- 机器
item_ids:
- ae2:molecular_assembler

# 分子装配室

<BlockImage id="molecular_assembler" scale="8" />

分子装配室接收输入其中的物品，并根据相邻的<ItemLink id="pattern_provider" />、或插入的<ItemLink id="crafting_pattern" />、<ItemLink id="smithing_table_pattern" />或<ItemLink id="stonecutting_pattern" />所定义的操作进行合成，随后将产物输出至相邻的容器中。

此装配器内置了一个指定“1个橡木原木 = 4个橡木木板”配方的合成样板。当橡木原木从上方漏斗输入时，装配器会进行合成并将橡木木板从下方漏斗输出。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/standalone_assembler.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 分子装配室的主要用途

然而，它们的主要用途是与<ItemLink id="pattern_provider" />相邻放置。在这种情况下，样板供应器具有特殊行为，会将相关样板的信息连同原料一起发送给相邻的装配器。由于装配器会自动将合成产物弹出至相邻容器（从而进入样板供应器的回收槽），因此只需在样板供应器旁放置装配器即可实现合成样板的自动化。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 升级

分子装配室支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="speed_card" />

## 配方

<RecipeFor id="molecular_assembler" />

## 注意

Optifine 会破坏“向相邻容器输出物品”的功能，因此大多数使用装配器的合成装置将无法正常工作。