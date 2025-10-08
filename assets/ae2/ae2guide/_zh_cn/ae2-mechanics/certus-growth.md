---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 赛特斯石英培育
  icon: quartz_cluster
---

# 赛特斯石英培育

## 基本内容摘自入门指南页面

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/budding_certus_1.snbt" />
</GameScene>

赛特斯石英芽会从[赛特斯芽点方块](../items-blocks-machines/budding_certus.md)上萌发，类似紫水晶的生长机制。若在石英芽未完全成熟时将其破坏，
将掉落一个<ItemLink id="certus_quartz_dust" />，此掉落不受时运附魔影响。若破坏完全成熟的石英簇，则会掉落四个
<ItemLink id="certus_quartz_crystal" />，此时时运附魔可增加掉落数量。

赛特斯芽点方块共分4个等级：无瑕、有瑕、开裂、受损，最初可在[陨石](../ae2-mechanics/meteorites.md)中发现它们。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_blocks.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

每次石英芽生长一个阶段，芽点方块都有概率降低一个等级，最终会退化为普通的赛特斯石英块。可通过将芽点方块（或
赛特斯石英块）与一个或多个<ItemLink id="charged_certus_quartz_crystal" />共同投入水中进行修复（也可创造新的芽点方块）。

<RecipeFor id="damaged_budding_quartz" />

无瑕赛特斯芽点方块不会退化，可无限生成赛特斯石英。但它们无法被合成或用镐子移动（即使附有精准采集）。（但可通过[空间存储](../ae2-mechanics/spatial-io.md)移动）

赛特斯石英芽自然生长极为缓慢。幸运的是，当<ItemLink id="growth_accelerator" />被放置在芽点方块相邻位置时，能大幅
加速这一过程。你应优先建造若干此类设备。

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_certus_2.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

复杂的交互机制意味着芽点方块每个被覆盖的面都会减缓其累计生长速率，
最终会抵消更多加速器的增益效果。经验测试表明：

![产量/分钟对应比例](../assets/diagrams/certus_farm_speed_chart_1.png)

![常见配置](../assets/diagrams/certus_farm_speed_chart_2.png)

若你没有足够石英来制作<ItemLink id="energy_acceptor" />或<ItemLink id="vibration_chamber" />，
可制作<ItemLink id="crank" />并将其安装在加速器末端。

自动收割赛特石英的方法[在此处说明](../example-setups/simple-certus-farm.md)。