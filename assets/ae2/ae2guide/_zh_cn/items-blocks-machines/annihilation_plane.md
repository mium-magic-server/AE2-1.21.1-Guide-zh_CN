---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 破坏面板
  icon: annihilation_plane
  position: 210
categories:
- 设备
item_ids:
- ae2:annihilation_plane
---

# 破坏面板

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/annihilation_plane.snbt" />
</GameScene>

破坏面板能够破坏方块并拾取物品。其功能类似于<ItemLink id="import_bus" />，将物品输送至[网络存储](../ae2-mechanics/import-export-storage.md)中。物品必须与面板表面发生碰撞才能被拾取，它不会在区域内自动拾取物品。

破坏面板可附加任何镐类附魔，因此若模组包允许，您可以为多个面板添加极高等级的时运附魔，从而实现[自动化矿石处理](../example-setups/ore-fortuner.md)。此外，精准采集附魔会如预期般生效，效率附魔可降低破坏方块的能量消耗，耐久附魔则有一定几率不消耗能量。

它们属于[线缆子部件](../ae2-mechanics/cable-subparts.md)。

**请务必在您的区块声明中启用假玩家权限**

## 过滤功能

只有当破坏面板能将破坏方块或拾取物品所产生的掉落物存入其所属网络时，它才会执行相应操作。这意味着要实现过滤功能，*必须限制其网络可存储的物品类型*，最常用的方法是将其接入[子网络](../ae2-mechanics/subnetworks.md)。可通过为<ItemLink id="storage_bus" />或[存储元件](../items-blocks-machines/storage_cells.md)设置[分区](cell_workbench.md)来实现此目的。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/annihilation_filtering.snbt" />

  <DiamondAnnotation pos="1 0.5 0.5" color="#00ff00">
        过滤设置为目标破坏物的所有掉落物
  </DiamondAnnotation>

  <DiamondAnnotation pos=".5 0.5 2.5" color="#00ff00">
        分区设置为目标破坏物的所有掉落物
  </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

需要再次强调的是，其过滤机制*基于物品掉落物*。例如，若要过滤<ItemLink id="minecraft:amethyst_cluster" />（紫水晶簇）的破坏，必须使用带有精准采集附魔的面板。否则，由于每个生长阶段都不会产生掉落物（即"无物品"），而网络始终可以存储"无物品"，面板将不受限制地破坏所有生长阶段的紫水晶簇。

## 配方

<RecipeFor id="annihilation_plane" />