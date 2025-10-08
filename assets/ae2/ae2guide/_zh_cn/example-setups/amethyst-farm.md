---
navigation:
  parent: example-setups/example-setups-index.md
  title: 紫水晶农场
  icon: minecraft:amethyst_shard
---

# 紫水晶种植

虽然<ItemLink id="growth_accelerator" />对紫水晶有效，但使用<ItemLink id="annihilation_plane" />过滤[赛特斯芽](../items-blocks-machines/budding_certus.md)的常规方法对紫水晶芽无效。与掉落<ItemLink id="certus_quartz_dust" />的未成熟赛特斯芽不同，未成熟的紫水晶芽不会掉落任何物品，因此破坏面板总是会破坏它们，因为网络总是可以存储“无物品”。

解决方法是给破坏面板附魔精准采集。这样未成熟的紫水晶芽*会*掉落物品（即各个生长阶段的实体芽方块），从而可以被过滤。

然后需要通过<ItemLink id="formation_plane" />重新放置<ItemLink id="minecraft:amethyst_cluster" />，再由未附魔精准采集的<ItemLink id="annihilation_plane" />再次破坏，以获得<ItemLink id="minecraft:amethyst_shard" />。

注意：由于紫水晶簇具有方向性，成型面板正对面必须有一个实心方块。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/amethyst_farm.snbt" />

  <BoxAnnotation color="#dddddd" min="2.7 1 1" max="3 2 2">
        (1) 破坏面板 #1：无配置界面，但附魔了精准采集。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 1 1" max="2.3 2 2">
        (2) 成型面板：过滤设置为紫水晶簇。
        <ItemImage id="minecraft:amethyst_cluster" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1.3 0.7 1" max="2 1 2">
        (3) 破坏面板 #2：无配置界面，但可附魔时运。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 0 1" max="1.3 1 2">
        (4) 存储总线 #1：过滤设置为紫水晶碎片。
        <ItemImage id="minecraft:amethyst_shard" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 .7" max="1 1 1">
        (5) 存储总线 #2：过滤设置为紫水晶碎片。优先级设置高于主网络存储。
        <ItemImage id="minecraft:amethyst_shard" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        连接主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置说明

* 第一个<ItemLink id="annihilation_plane" /> (1) 无配置界面，但必须附魔精准采集。
* <ItemLink id="formation_plane" /> (2) 过滤设置为<ItemLink id="minecraft:amethyst_cluster" />。
* 第二个<ItemLink id="annihilation_plane" /> (3) 无配置界面，但可附魔时运。
* 第一个<ItemLink id="storage_bus" /> (4) 过滤设置为<ItemLink id="minecraft:amethyst_shard" />。
* 第二个<ItemLink id="storage_bus" /> (5) 过滤设置为<ItemLink id="minecraft:amethyst_shard" />，且其[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)设置高于主网络存储。

## 运作原理

1. 第一个<ItemLink id="annihilation_plane" />尝试破坏其前方的方块，但由于子网络中唯一的存储器是过滤设置为紫水晶簇的<ItemLink id="formation_plane" />，因此只能破坏<ItemLink id="minecraft:amethyst_cluster" />。这仅在该面板附魔了精准采集时才有效，否则它将能够破坏未成熟的芽（因为它们不掉落任何物品）。
2. <ItemLink id="formation_plane" />将紫水晶簇放置在其对面的方块上。
3. 第二个<ItemLink id="annihilation_plane" />破坏紫水晶簇，产生<ItemLink id="minecraft:amethyst_shard" />。
4. 第一个<ItemLink id="storage_bus" />将碎片存入木桶。严格来说此处无需设置过滤，因为第二个破坏面板应仅会遇到完全成熟的紫水晶簇。
5. 第二个<ItemLink id="storage_bus" />使主网络能够访问木桶中的所有紫水晶碎片。其设置为高[优先级](../ae2-mechanics/import-export-storage.md#storage-priority)，以确保紫水晶碎片优先存回木桶而非主存储。