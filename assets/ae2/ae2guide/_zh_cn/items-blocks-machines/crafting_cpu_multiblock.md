---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 合成CPU多方块结构（存储器、协处理器、监控器、单元）
  icon: 1k_crafting_storage
  position: 210
categories:
- 设备
item_ids:
- ae2:1k_crafting_storage
- ae2:4k_crafting_storage
- ae2:16k_crafting_storage
- ae2:64k_crafting_storage
- ae2:256k_crafting_storage
- ae2:crafting_accelerator
- ae2:crafting_monitor
- ae2:crafting_unit
---

# 合成CPU

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/crafting_cpus.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<Row>
  <BlockImage id="1k_crafting_storage" scale="4" />

  <BlockImage id="crafting_accelerator" scale="4" />

  <BlockImage id="crafting_monitor" scale="4" />

  <BlockImage id="crafting_unit" scale="4" />
</Row>

合成CPU负责管理合成请求/任务。它们存储多步骤合成任务中涉及的中间材料，并影响可处理任务的大小，以及在一定程度上影响任务完成的速度。更多详情请参阅[自动合成](../ae2-mechanics/autocrafting.md)。

每个合成CPU处理1个请求或任务，因此如果你想同时请求一个运算处理器和256个平滑石，你需要2个CPU多方块结构。

它们可以被设置为处理来自玩家、自动化（输出总线和接口）或两者的请求。

右键单击其中一个会打开合成状态界面，你可以在其中查看CPU正在处理的合成任务进度。

## 设置

*   CPU可以设置为仅接受来自玩家的请求、仅接受来自自动化（如带有<ItemLink id="crafting_card" />的<ItemLink id="export_bus" />）的请求，或两者都接受。

## 结构

合成CPU是多方块结构，必须是实心的矩形棱柱，不能有间隙。它们由几个组件构成。

每个CPU必须包含至少1个合成存储块（实际上最小的可行CPU就是单个1k合成存储器）。

# 合成单元

<BlockImage id="crafting_unit" scale="4" />

（可选）如果你没有足够的其他组件，合成单元可以简单地填充CPU中的空间，使其成为一个实心的矩形棱柱。它们也是其他组件的基础材料。

<RecipeFor id="crafting_unit" />

# 合成存储器

<Row>
  <BlockImage id="1k_crafting_storage" scale="4" />

  <BlockImage id="4k_crafting_storage" scale="4" />

  <BlockImage id="16k_crafting_storage" scale="4" />

  <BlockImage id="64k_crafting_storage" scale="4" />

  <BlockImage id="256k_crafting_storage" scale="4" />
</Row>

（必需）合成存储器提供所有标准存储元件规格（1k、4k、16k、64k、256k）。它们存储合成过程中涉及的原料和中间材料，因此需要更大或更多的存储器，CPU才能处理包含更多材料的合成任务。

<Column>
  <Row>
    <RecipeFor id="1k_crafting_storage" />

    <RecipeFor id="4k_crafting_storage" />

    <RecipeFor id="16k_crafting_storage" />
  </Row>

  <Row>
    <RecipeFor id="64k_crafting_storage" />

    <RecipeFor id="256k_crafting_storage" />
  </Row>
</Column>

# 合成协处理单元

<BlockImage id="crafting_accelerator" scale="4" />

（可选）合成协处理器通过加快CPU的运算速度（tick），使系统更频繁地从<ItemLink id="pattern_provider" />发送原料批次。
这使它们能够跟上快速处理的机器。一个例子是，一个被<ItemLink id="molecular_assembler" />包围的样板供应器能够比单个装配器处理得更快地推送原料，从而将原料批次分配到周围的装配器之间。

一些复杂的配方有多个可以并行执行的步骤，例如在制作书架时同时制作木板和书。
在合成状态界面（通过右键单击CPU或通过[终端](terminals.md)中的锤子图标可见），这些步骤都将显示为“计划中”。每个额外的协处理器允许再并行执行一个这样的步骤（并因此显示为“合成中”）。
然而，这并不那么重要，因为你通常会有比配方中可能并行执行的步骤更多的协处理器，纯粹是为了提高输入速度。

<RecipeFor id="crafting_accelerator" />

# 合成监控器

<BlockImage id="crafting_monitor" scale="4" />

（可选）合成监控器显示CPU当前正在处理的任务。
屏幕可以使用<ItemLink id="color_applicator" />进行染色。

<RecipeFor id="crafting_monitor" />