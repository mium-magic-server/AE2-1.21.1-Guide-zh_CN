---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 充电器
  icon: charger
  position: 310
categories:
- 机器
item_ids:
- ae2:charger
---

# 充电器

<BlockImage id="charger" scale="8" />

充电器可以为支持的物品以及<ItemLink id="certus_quartz_crystal" />进行充能。

可通过顶部或底部输入能量，支持AE2的[线缆](cables.md)或其他模组的能量线缆。可接受AE2能量（AE）或Forge Energy（FE）。物品可从任意面放入或取出。只有完成充能的物品才能被取出，因此无需使用过滤器来防止误取未充能的赛特斯石英水晶。可使用<ItemLink id="certus_quartz_wrench" />旋转方向以配合自动化生产。

可用于将<ItemLink id="certus_quartz_crystal" />转化为<ItemLink id="charged_certus_quartz_crystal" />，或将<ItemLink id="minecraft:compass" />转化为<ItemLink id="meteorite_compass" />。

如需手动供能，可在顶部或底部放置<ItemLink id="crank" />并右键点击转动，直至物品完成充能。

同时也可作为[福鲁伊克斯研究员](fluix_researcher.md)的工作站使用。

## 简易自动化

举例来说，其可旋转特性允许你实现如下半自动化设置：

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/charger_hopper.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配方

<RecipeFor id="charger" />