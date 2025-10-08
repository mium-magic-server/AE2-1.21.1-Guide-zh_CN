---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 压印器
  icon: inscriber
  position: 310
categories:
- 机器
item_ids:
- ae2:inscriber
---

# 压印器

<BlockImage id="inscriber" scale="8" />

压印器用于使用[压印模板](presses.md)来压印电路和[处理器](processors.md)，并将各种物品粉碎成粉末。
它可以接受AE2能量（AE）或Fabric/Forge Energy（E/FE）。它可以进行侧面配置，以便从不同侧面放入物品到其物品栏的不同槽位。为此，可以使用<ItemLink id="certus_quartz_wrench" />来旋转它。
它还可以设置为将合成结果推入相邻的物品栏。

输入缓冲区的大小可以调整。例如，如果你想从一个物品栏向一个大型压印器阵列供应材料，你会希望使用较小的缓冲区，这样材料可以在压印器之间更优化地分配（而不是第一个压印器填满64个物品而其他压印器却是空的）。

4种电路压印模板用于合成[处理器](processors.md)

<Row>
  <ItemImage id="silicon_press" scale="4" />

  <ItemImage id="logic_processor_press" scale="4" />

  <ItemImage id="calculation_processor_press" scale="4" />

  <ItemImage id="engineering_processor_press" scale="4" />
</Row>

而名称压印模板可用于像铁砧一样为方块命名，这在<ItemLink id="pattern_access_terminal" />中标记物品时非常有用。

<ItemImage id="name_press" scale="4" />

## 设置

*   压印器可以设置为侧面配置模式（如下所述），或者允许从任何侧面将物品放入任何槽位，由内部过滤器决定物品的去向。在非侧面配置模式下，无法从顶部和底部槽位提取物品。
*   压印器可以设置为将物品推入相邻的物品栏。
*   输入缓冲区的大小可以调整，大缓冲区选项适用于手动供料的独立压印器，小缓冲区选项则使大型并行化设置更具可行性。

## 界面与侧面配置

在侧面配置模式下，压印器根据你放入或提取物品的侧面来过滤物品的去向。

![压印器界面](../assets/diagrams/inscriber_gui.png) ![压印器侧面](../assets/diagrams/inscriber_sides.png)

A. **顶部输入** 通过压印器的顶部面访问（可向此槽位推入和从中提取物品）

B. **中部输入** 通过压印器的左、右、前、后面放入物品（只能向此槽位推入物品，不能从中提取）

C. **底部输入** 通过压印器的底部面访问（可向此槽位推入和从中提取物品）

D. **输出** 通过压印器的左、右、前、后面提取物品（只能从此槽位提取物品，不能推入）

## 简单自动化

例如，侧面配置和可旋转性意味着你可以像这样半自动化压印器：

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/inscriber_hopper_automation.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

或者在非侧面配置模式下，直接通过管道向压印器输入和输出物品。

## 升级

压印器支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="speed_card" />

## 配方

<RecipeFor id="inscriber" />