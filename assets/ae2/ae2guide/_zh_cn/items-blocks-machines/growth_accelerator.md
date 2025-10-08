---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 生长加速器
  icon: growth_accelerator
  position: 310
categories:
- 机器
item_ids:
- ae2:growth_accelerator
---

# 生长加速器

<BlockImage id="growth_accelerator" p:powered="true" scale="8"/>

生长加速器在毗邻晶芽块放置时，能大幅加速[赛特斯石英或紫水晶](../ae2-mechanics/certus-growth.md)的生长过程。

有趣的是，它*同样*能够加速各种植物的生长。

其原理是通过向毗邻方块施加"随机刻"，这是在自然发生的随机刻之外的额外作用。
理论上这意味着1个加速器能使生长速度提升至约正常速度的90倍，且效果可叠加。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/growth_accelerator.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

可通过顶部或底部供电，支持使用AE2的[线缆](cables.md)或其他模组的能源线缆。
可接受AE2能源（AE）或Forge Energy（FE）。

若要手动供能，可在顶部或底部放置<ItemLink id="crank" />并右键点击。

顶部和底部可通过其上的粉色通量装饰件进行识别。

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/accelerator_connections.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配方

<RecipeFor id="growth_accelerator" />