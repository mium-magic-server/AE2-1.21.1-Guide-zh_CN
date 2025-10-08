---
navigation:
  parent: example-setups/example-setups-index.md
  title: 简易赛特斯农场
  icon: certus_quartz_crystal
  position: 110
---

# 简易赛特斯农场

正如[培育赛特斯石英](../ae2-mechanics/certus-growth.md)中所述，自动化收获<ItemLink id="certus_quartz_crystal" />
需要使用<ItemLink id="annihilation_plane" />和<ItemLink id="storage_bus" />。
<ItemLink id="growth_accelerator" />用于大幅加速赛特斯石英芽的生长，然后破坏面板会破坏完全成熟的<ItemLink id="quartz_cluster" />。
它们通过利用一个非常幸运的特性进行过滤：未成熟的赛特斯石英芽会掉落<ItemLink id="certus_quartz_dust" />，而不是什么都不掉落。

这个农场使用<ItemLink id="flawless_budding_quartz" />可以完全自动化运行，但如果使用有瑕、开裂或受损的
赛特斯石英母岩，你将需要手动更换母岩方块。或者，如[半自动赛特斯农场](semiauto-certus-farm.md)
和[高级赛特斯农场](advanced-certus-farm.md)所述，实现自动化更换。

预估速度请参见[培育赛特斯石英](../ae2-mechanics/certus-growth.md)。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/simple_certus_farm.snbt" />

  <BoxAnnotation color="#dddddd" min="3.7 1 1" max="4 2 2">
        (1) 破坏面板：无需配置 GUI，但可以用时运附魔。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 1" max="3.3 2 2">
        (2) 存储总线 #1：过滤设置为赛特斯石英水晶。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 .7" max="2 2 1">
        (3) 存储总线 #2：过滤设置为赛特斯石英水晶。优先级设置得比主存储器高。
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="1 0.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

*   第一个<ItemLink id="annihilation_plane" /> (1) 没有 GUI，无法配置，但可以用时运附魔。
*   第一个<ItemLink id="storage_bus" /> (2) 过滤设置为<ItemLink id="certus_quartz_crystal" />。
*   第二个<ItemLink id="storage_bus" /> (3) 过滤设置为<ItemLink id="certus_quartz_crystal" />，并且其
    [优先级](../ae2-mechanics/import-export-storage.md#storage-priority)设置得比主存储器高。

## 工作原理

1.  <ItemLink id="annihilation_plane" />会尝试破坏其前方的方块，但只能破坏<ItemLink id="quartz_cluster" />，
    因为子网络上唯一的存储器是过滤设置为<ItemLink id="certus_quartz_crystal" />的<ItemLink id="storage_bus" />。
4.  第一个<ItemLink id="storage_bus" />将赛特斯石英水晶存储到木桶中。
5.  第二个<ItemLink id="storage_bus" />让主网络能够访问木桶中的所有赛特斯石英水晶。它被设置为高
    [优先级](../ae2-mechanics/import-export-storage.md#storage-priority)，以便赛特斯石英水晶会优先
    被放回木桶中，而不是进入你的主存储器。