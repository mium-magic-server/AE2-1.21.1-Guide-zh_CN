---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 赛特斯石英母岩
  icon: flawless_budding_quartz
  position: 010
categories:
- 杂项材料方块
item_ids:
- ae2:flawless_budding_quartz
- ae2:flawed_budding_quartz
- ae2:chipped_budding_quartz
- ae2:damaged_budding_quartz
- ae2:small_quartz_bud
- ae2:medium_quartz_bud
- ae2:large_quartz_bud
- ae2:quartz_cluster
---

# 赛特斯石英母岩

（另请参阅[赛特斯石英生长](../ae2-mechanics/certus-growth.md)）

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_blocks.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

赛特斯石英芽会从赛特斯石英母岩中萌发，类似于紫水晶。这些母岩可在[陨石](../ae2-mechanics/meteorites.md)中找到。
赛特斯石英母岩共有4个等级：无瑕、有瑕、开裂和损坏。它们可以最方便地通过诸如 HWYLA、Jade、The One Probe 等模组（或 F3 屏幕）进行识别。

对于有瑕、开裂和损坏的赛特斯石英母岩，每当其上的石英芽生长一个阶段时，母岩方块都有几率降低一个等级，最终变为普通的<ItemLink id="quartz_block" />。

无瑕的赛特斯石英母岩不会因石英芽的生长而降低等级，可作为无限资源。

如果使用普通的镐破坏，赛特斯石英母岩会降低1个等级。如果使用附有精准采集的镐破坏，它们则不会降级，除非它们原本就是无瑕的。**这意味着无瑕的赛特斯石英母岩无法通过镐拾取和移动**。作为替代，可以使用[空间存储](../ae2-mechanics/spatial-io.md)来剪切并粘贴无瑕的母岩方块。

## 配方

有瑕、开裂和损坏的赛特斯石英母岩可以通过将上一等级的母岩方块（或一个<ItemLink id="quartz_block" />）与一个或多个<ItemLink id="charged_certus_quartz_crystal" />一起投入水中来合成。

无瑕的赛特斯石英母岩无法合成，只能在世界中找到。

<Row>
  <RecipeFor id="damaged_budding_quartz" />

  <RecipeFor id="chipped_budding_quartz" />

  <RecipeFor id="flawed_budding_quartz" />
</Row>