---
navigation:
  title: 新手入门 (1.20+)
  position: 10
---

<div class="notification is-info">
  以下信息仅适用于 Minecraft 1.20 及更新版本中的应用能源 2。
</div>

# 新手入门

## 获取初始材料

<GameScene zoom="4" background="transparent">
  <ImportStructure src="assets/assemblies/meteor_interior.snbt" />
</GameScene>

要开始使用应用能源 2，你首先需要找到一颗[陨石](ae2-mechanics/meteorites.md)。它们相当常见，并且往往在地形上留下巨大的坑洞，所以你可能在旅途中已经遇到过一颗。
如果还没有，你可以制作一个<ItemLink id="meteorite_compass" />，它会指向最近的<ItemLink id="mysterious_cube" />。

找到陨石后，挖掘至其中心。你会发现赛特斯石英簇、赛特斯石英芽、各种类型的[赛特斯芽块](items-blocks-machines/budding_certus.md)，以及中心的一个神秘方块。

挖掘赛特斯石英簇和你找到的任何赛特斯石英块。你也可以拾取赛特斯芽块，但如果没有精准采集附魔，它们会降低 1 级品质。

不要破坏任何无瑕的赛特斯芽块，因为即使使用精准采集，它们也会降级为有瑕的赛特斯芽块，并且无法修复回无瑕品质。

同时挖掘陨石中心的神秘方块，以获得全部 4 种压印模板。

## 培育赛特斯石英

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_certus_1.snbt" />
</GameScene>

赛特斯石英芽会从[赛特斯芽块](items-blocks-machines/budding_certus.md)中长出，类似于紫水晶。如果你破坏一个未完全生长的芽，它会掉落一个<ItemLink id="certus_quartz_dust" />，不受时运附魔影响。如果你破坏一个完全生长的簇，它会掉落四个<ItemLink id="certus_quartz_crystal" />，时运附魔会增加这个数量。

赛特斯芽块有 4 个品质等级：无瑕、有瑕、开裂、受损。

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_blocks.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

每次芽生长一个阶段，芽块都有几率降低一级品质，最终变成一个普通的赛特斯石英块。可以通过将芽块（或一个赛特斯石英块）与一个或多个<ItemLink id="charged_certus_quartz_crystal" />一起扔进水中来修复它们（或创建新的芽块）。

<RecipeFor id="damaged_budding_quartz" />

无瑕的赛特斯芽块不会降级，并且会无限生成赛特斯石英。然而，它们无法被合成或用镐移动，即使有精准采集附魔。（但它们*可以*通过[空间存储](ae2-mechanics/spatial-io.md)移动）

赛特斯石英芽本身生长非常缓慢。幸运的是，当<ItemLink id="growth_accelerator" />放置在芽块相邻位置时，会极大地加速这个过程。你应该优先制作一些这样的加速器。

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_certus_2.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

如果你没有足够的石英来制作<ItemLink id="energy_acceptor" />或<ItemLink id="vibration_chamber" />，你可以制作一个<ItemLink id="crank" />并将其安装在加速器的末端。

自动收获赛特斯石英的方法[在此处描述](example-setups/simple-certus-farm.md)。

## 关于福鲁伊克斯水晶的简短说明

你需要的另一种材料是福鲁伊克斯水晶，你在制作生长加速器时已经接触过它。它通过将充能赛特斯石英、红石和下界石英扔进水中制成。如何自动化完成这个过程“留给读者作为练习”。

如果你还没有制作，那么生产<ItemLink id="charged_certus_quartz_crystal" />需要<ItemLink id="charger" />。

## 压印一些处理器

在掠夺陨石的过程中，你会从破坏神秘方块中获得四个“压印模板”。这些模板在<ItemLink id="inscriber" />中用于制作三种类型的处理器。

<ItemGrid>
  <ItemIcon id="silicon_press" />

  <ItemIcon id="logic_processor_press" />

  <ItemIcon id="calculation_processor_press" />

  <ItemIcon id="engineering_processor_press" />
</ItemGrid>

压印器是一个有朝向的机器，很像原版的熔炉。从顶部或底部放入物品会将其放入顶部或底部槽位，从侧面或背面放入会放入中心槽位。结果可以从侧面或背面取出。

为了方便使用漏斗自动化（并可能减少管道混乱），可以使用<ItemLink id="certus_quartz_wrench" />旋转压印器。

为下一步制作一个非常基础的 ME 系统做准备，生产一些每种类型的处理器。自动化处理器生产“[留给读者作为练习](example-setups/processor-automation.md)”。

## 物质能源科技：ME 网络与存储

### 什么是 ME 存储？

它的发音是 Emm-Eee，代表 Matter Energy（物质能源）。

物质能源是应用能源 2 的主要组成部分，它就像一个疯狂科学家版本的多方块箱子，它可以彻底改变你的存储状况。ME 与 Minecraft 中的其他存储系统截然不同，可能需要一些跳出框框的思考来适应；但一旦你开始使用，在微小空间内拥有海量存储和多个访问终端只是其可能性的冰山一角。

### 入门需要了解什么？

首先，ME 将物品存储在称为[存储元件](items-blocks-machines/storage_cells.md)的其他物品内部；有 5 个等级，存储量不断增加。为了使用存储元件，必须将其放入<ItemLink id="chest" />或<ItemLink id="drive" />中。

<ItemLink id="chest" />在放入元件后会立即显示其内容，你可以像操作<ItemLink id="minecraft:chest" />一样添加和移除物品，不同之处在于物品实际上存储在存储元件中，而不是<ItemLink id="chest" />本身。

<ItemLink id="chest" />的效用相当有限且依赖特定情况。要真正利用 AE2 的优势，你需要建立一个[ME 网络](ae2-mechanics/me-network-connections.md)。

## 你的第一个 ME 系统

既然你已经拥有了应用能源 2 的所有基础材料和机器，你可以制作你的第一个 ME（物质能源）系统。这将是一个非常基础的系统，没有自动合成，没有物流，只有美观、简单、可搜索的存储。

<GameScene zoom="6" interactive={true}>
<ImportStructure src="assets/assemblies/tiny_me_system.snbt" />

</GameScene>

*   你的材料清单：
    * 1x <ItemLink id="drive" />
    * 1x <ItemLink id="terminal" /> 或 <ItemLink id="crafting_terminal" />
    * 1x <ItemLink id="energy_acceptor" />
    * 一些[线缆](items-blocks-machines/cables.md)，玻璃、包层或智能线缆均可，但不能是致密线缆
    * 一些[存储元件](items-blocks-machines/storage_cells.md)，推荐使用 4k 类型的，以在容量和类型数量之间取得良好平衡（[分区](items-blocks-machines/cell_workbench.md)混合使用 4k 和 1k 元件会更高效，但这是我们现在不会涉及的复杂性）
---
1.  放下驱动器。
2.  能源接收器（以及 AE2 的其他几种[设备](ae2-mechanics/devices.md)）有两种模式，立方体和平板。它们可以在合成网格中切换。如果你的能源接收器是立方体，将其放在驱动器旁边。如果它是扁平的正方形，则在驱动器上放一根线缆，然后将接收器放在线缆上。
3.  用你最喜欢的能源生成模组提供的线缆/管道/导管将能量输入能源接收器。
4.  在驱动器顶部（或大约视线高度）放置一根线缆，并将你的终端或合成终端放在上面。
5.  将你的存储元件放入驱动器
6.  享受成果
7.  调整终端的设置
8.  沉浸在你终极的力量和能力中
9.  意识到这个网络，从大局来看，相当小

### 扩展你的网络

所以你已经有了一些基础存储，并且可以访问这些存储，这是一个好的开始，但你可能会希望自动化一些处理过程。

一个很好的例子是在熔炉顶部放置一个<ItemLink id="export_bus" />来倒入矿石，并在熔炉底部放置一个<ItemLink id="import_bus" />来提取熔炼好的矿石。

<ItemLink id="export_bus" />让你从网络中将物品输出到附着的容器中，而<ItemLink id="import_bus" />则从附着的容器中将物品导入网络。

### 克服限制

此时你可能接近 8 个左右的[设备](ae2-mechanics/devices.md)，一旦达到 9 个设备，你将不得不开始管理[频道](ae2-mechanics/channels.md)。许多设备（但并非全部）需要一个频道才能运作。

默认情况下，一个网络可以支持 8 个频道，一旦突破这个限制，你将必须在你的网络中添加一个<ItemLink id="controller" />。这允许你极大地扩展你的网络。
[智能线缆](items-blocks-machines/cables.md)可以让你看到频道是如何在你的网络中路由的。在开始时广泛使用它们来了解频道的行为，或者如果你有很多红石和荧石的话。