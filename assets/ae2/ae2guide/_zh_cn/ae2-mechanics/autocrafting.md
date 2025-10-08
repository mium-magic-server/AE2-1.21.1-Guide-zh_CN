---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 自动合成
  icon: pattern_provider
---

# 自动合成

### 核心功能

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/autocraft_setup_greebles.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

自动合成是 AE2 的主要功能之一。你无需像*普通人*那样手动合成每个子配方的正确数量并辛苦劳作，而是可以请求你的 ME 系统为你完成。或者自动合成物品并将其输出到某处。或者通过巧妙的涌现行为自动保持特定数量的物品库存。它同样适用于流体，并且，如果你安装了某些为额外模组材料类型（如 Mekanism 的气体）提供支持的插件，那么这些材料也可以自动合成。这非常棒。

这是一个相当复杂的话题，所以请做好准备，让我们开始吧。

一个自动合成装置包含 3 个部分：
- 发送合成请求的东西
- 合成 CPU
- <ItemLink id="pattern_provider" />（样板供应器）。

以下是其工作流程：

1.  某物创建了一个合成请求。这可以是你自己在终端点击某个可自动合成的物品，也可以是一个输出总线或接口，它们配备了合成卡，请求它们设定要输出/储备的物品之一。

*   (**重要：** 使用你绑定给“选取方块”（通常是鼠标中键）的按键来请求合成你已经拥有的物品，这可能会与库存整理模组冲突），

2.  ME 系统计算完成请求所需的原料和先决合成步骤，并将它们存储在选定的合成 CPU 中。

3.  拥有相关[样板](../items-blocks-machines/patterns.md)的 <ItemLink id="pattern_provider" /> 将样板中指定的原料推送到任何相邻的容器中。
    如果是工作台配方（“合成样板”），这将是 <ItemLink id="molecular_assembler" />（分子装配室）。
    如果是非合成配方（“处理样板”），这将是其他方块、机器或复杂的红石控制装置。

4.  合成结果以某种方式返回到系统，无论是通过输入总线、接口，还是将结果推回样板供应器。
    **请注意，必须发生“物品进入系统”的事件，你不能只是用管道将结果输入到一个带有 <ItemLink id="storage_bus" />（存储总线）的箱子中。**

5.  如果该合成是请求中另一个合成的先决条件，则物品会存储在该合成 CPU 中，然后用于该合成。

## 递归配方

<ItemImage id="minecraft:netherite_upgrade_smithing_template" scale="4" />

自动合成算法*无法*处理的一件事是递归配方。例如，像“1 个红石粉 = 2 个红石粉”这样的复制配方，来自将红石扔进植物魔法的魔力池中。另一个例子是原版 Minecraft 中的锻造模板。但是，有[一种方法可以处理这些配方](../example-setups/recursive-crafting-setup.md)。

# 样板

<ItemImage id="crafting_pattern" scale="4" />

样板是在 <ItemLink id="pattern_encoding_terminal" />（样板编码终端）中用空白样板制作的。

有几种不同类型的样板用于不同用途：

*   <ItemLink id="crafting_pattern" />（合成样板）编码由工作台制作的配方。它们可以直接放入 <ItemLink id="molecular_assembler" /> 中，使其在获得原料时制作结果，但它们的主要用途是放在分子装配室旁边的 <ItemLink id="pattern_provider" /> 中。
    在这种情况下，样板供应器具有特殊行为，会将相关样板连同原料一起发送到相邻的装配室。
    由于装配室会自动将合成结果弹出到相邻的容器中，因此一个位于样板供应器上的装配室就是自动化合成样板所需的全部。

***

*   <ItemLink id="smithing_table_pattern" />（锻造台样板）与合成样板非常相似，但它们编码锻造台配方。它们也由样板供应器和分子装配室自动化，并且以完全相同的方式运作。事实上，合成、锻造和切石样板可以在同一个装置中使用。

***

*   <ItemLink id="stonecutting_pattern" />（切石机样板）与合成样板非常相似，但它们编码切石机配方。它们也由样板供应器和分子装配室自动化，并且以完全相同的方式运作。事实上，合成、锻造和切石样板可以在同一个装置中使用。

***

*   <ItemLink id="processing_pattern" />（处理样板）是自动合成中大量灵活性的来源。它们是最通用的类型，简单地说就是“如果样板供应器将这些原料推送到相邻的容器中，ME 系统将在不久的将来或遥远的未来某个时间点收到这些物品”。你将通过它们用几乎任何模组机器、熔炉等来自动合成。因为它们的使用非常通用，并且不关心在推送原料和接收结果之间发生了什么，所以你可以做一些非常奇特的事情，比如将原料输入到整个复杂的工厂生产链中，该生产链会分拣东西，从无限生产的农场获取其他原料，打印整部《蜜蜂总动员》的剧本，只要 ME 系统得到样板指定的结果，它就不在乎。事实上，它甚至不关心原料是否与结果有任何关系。你可以告诉它“1 个樱桃木木板 = 1 个下界之星”，并让你的凋灵农场在收到樱桃木木板时杀死一个凋灵，这也能工作。

支持多个具有相同样板的 <ItemLink id="pattern_provider" />，并且它们可以并行工作。此外，你可以让一个样板指定，例如，8 个圆石 = 8 个石头，而不是 1 个圆石 = 1 个石头，这样样板供应器每次操作都会将 8 个圆石插入你的熔炼装置中，而不是一次一个。

## 最通用的“样板”形式

实际上，还有一种比处理样板更“通用”的“样板”形式。带有合成卡的 <ItemLink id="level_emitter" />（等级发射器）可以设置为发出红石信号以合成某物。这种“样板”不定义，甚至不关心原料。
它只是说“如果你从这个等级发射器发出红石信号，ME 系统将在不久的将来或遥远的未来某个时间点收到此物品”。这通常用于激活和停免不需要输入原料的无限农场，或者用于激活处理递归配方（标准自动合成无法理解）的系统，例如，如果你有一台复制圆石的机器，可以处理“1 个圆石 = 2 个圆石”这样的配方。

# 合成 CPU

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/crafting_cpus.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

合成 CPU 管理合成请求/任务。它们在执行多步骤的合成任务时存储中间原料，并影响任务的大小，以及在某种程度上影响它们的完成速度。它们是多方块结构，必须是矩形棱柱，并且至少包含 1 个合成存储器。

合成 CPU 由以下部分组成：

*   （必需）[合成存储器](../items-blocks-machines/crafting_cpu_multiblock.md)，提供所有标准单元尺寸（1k、4k、16k、64k、256k）。它们存储合成中涉及的原料和中间原料，因此需要更大或更多的存储器才能使 CPU 处理具有更多原料的合成任务。
*   （可选）<ItemLink id="crafting_accelerator" />（合成加速器），它们使系统更频繁地从样板供应器发送原料批次。
    这允许，例如，一个被 6 个分子装配室包围的样板供应器可以一次将原料发送给（从而使用）所有 6 个装配室，而不是只使用一个。
*   （可选）<ItemLink id="crafting_monitor" />（合成监控器），它们显示 CPU 当前正在处理的任务。可以通过 <ItemLink id="color_applicator" />（颜色应用器）为其上色。
*   （可选）<ItemLink id="crafting_unit" />（合成单元），它们只是填充空间以使 CPU 成为矩形棱柱。

每个合成 CPU 处理 1 个请求或任务，因此如果你想同时请求一个计算处理器和 256 个平滑石头，你需要 2 个 CPU 多方块结构。

它们可以设置为处理来自玩家、自动化（输出总线和接口）或两者的请求。

# 样板供应器

<Row>
<BlockImage id="pattern_provider" scale="4" />

<BlockImage id="pattern_provider" p:push_direction="up" scale="4" />

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/blocks/cable_pattern_provider.snbt" />
</GameScene>
</Row>

<ItemLink id="pattern_provider" /> 是你的自动合成系统与世界交互的主要方式。它们将其[样板](../items-blocks-machines/patterns.md)中的原料推送到相邻的容器中，并且可以将物品插入它们以将物品插入网络。通常，通过将机器的输出用管道接回附近的样板供应器（通常是推送原料的那个），而不是使用 <ItemLink id="import_bus" />（输入总线）将机器的输出拉入网络，可以节省一个频道。

值得注意的是，由于它们直接从合成 CPU 中的[合成存储器](../items-blocks-machines/crafting_cpu_multiblock.md#crafting-storage)推送原料，所以它们的库存中实际上从不包含这些原料，因此你无法从它们那里用管道输出。你必须让供应器推送到另一个容器（如桶），然后从那里用管道输出。

同样值得注意的是，供应器必须一次推送 ALL 的原料，它不能推送半批。这一点可以利用。

样板供应器与[子网络](../ae2-mechanics/subnetworks.md)上的接口有特殊的交互：如果接口未被修改（请求槽位中没有任何东西），供应器将完全跳过该接口，直接推送到该子网络的[存储](../ae2-mechanics/import-export-storage.md)，跳过接口且不用配方批次填充它，更重要的是，在存储中有空间之前不会插入下一批。

支持多个具有相同样板的样板供应器，并且它们可以并行工作。

样板供应器将尝试以轮询方式将其批次发送到其所有面，从而并行使用所有连接的机器。

## 变体

样板供应器有 3 种不同的变体：普通型、定向型和扁平型。这影响了它们向哪些特定面推送原料、从哪些面接收物品以及提供网络连接。

*   普通样板供应器向所有面推送原料，从所有面接收输入，并且像大多数 AE2 机器一样，充当电缆向所有面提供网络连接。

*   定向样板供应器是通过在普通样板供应器上使用 <ItemLink id="certus_quartz_wrench" />（赛特斯石英扳手）改变其方向制成的。它们只向选定的面推送原料，从所有面接收输入，并且特意不在选定的面上提供网络连接。这允许它们在推送到 AE2 机器时不会连接网络，如果你想创建一个子网络的话。

*   扁平样板供应器是一个[线缆子部件](../ae2-mechanics/cable-subparts.md)，因此可以在同一根线缆上放置多个，从而实现紧凑的装置。
    它们的行为类似于定向样板供应器上的选定面，提供样板、接收输入，并且不在其面上提供网络连接。

样板供应器可以在合成网格中在普通型和扁平型之间切换。

## 设置

样板供应器有多种模式：

*   **阻塞模式 (Blocking Mode)** 如果机器中已有原料，则阻止供应器推送新批次的原料。
*   **锁定合成 (Lock Crafting)** 可以根据各种红石条件锁定供应器，或者直到上一次合成的结果被插入到该特定样板供应器中。
*   供应器可以在 <ItemLink id="pattern_access_terminal" />（样板访问终端）上显示或隐藏。

## 优先级

可以通过点击 GUI 右上角的扳手来设置优先级。在多个[样板](../items-blocks-machines/patterns.md)对应同一物品的情况下，优先级较高的供应器中的样板将优先于优先级较低的供应器中的样板被使用，除非网络没有高优先级样板所需的原料。

# 分子装配室

<BlockImage id="molecular_assembler" scale="4" />

<ItemLink id="molecular_assembler" /> 接收输入其中的物品，并执行由相邻 <ItemLink id="pattern_provider" /> 或插入的 <ItemLink id="crafting_pattern" />、<ItemLink id="smithing_table_pattern" /> 或 <ItemLink id="stonecutting_pattern" /> 定义的操作，然后将结果推送到相邻的容器中。

它们的主要用途是放在 <ItemLink id="pattern_provider" /> 旁边。在这种情况下，样板供应器具有特殊行为，会将相关样板的信息连同原料一起发送到相邻的装配室。由于装配室会自动将合成结果弹出到相邻的容器中（从而进入样板供应器的返回槽），因此一个位于样板供应器上的装配室就是自动化合成样板所需的全部。

<GameScene zoom="4" background="transparent">
<ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>