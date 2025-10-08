---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 处理器
  icon: logic_processor
  position: 010
categories:
- 杂项材料方块
item_ids:
- ae2:logic_processor
- ae2:calculation_processor
- ae2:engineering_processor
- ae2:printed_silicon
- ae2:printed_logic_processor
- ae2:printed_calculation_processor
- ae2:printed_engineering_processor
- ae2:silicon
---

# 处理器

<Row>
  <ItemImage id="logic_processor" scale="4" />

  <ItemImage id="calculation_processor" scale="4" />

  <ItemImage id="engineering_processor" scale="4" />
</Row>

处理器是 AE2 [设备](../ae2-mechanics/devices.md)和机器的主要材料之一，也是你面临的第一个大型自动化挑战。共有三种类型的处理器，分别使用金、<ItemLink id="certus_quartz_crystal" />（赛特斯石英水晶）和钻石制成。它们需要在<ItemLink id="inscriber" />（压印器）中使用[压印模板](presses.md)，通过多步骤流程（通常通过一系列压印器和过滤管道）制作完成。

## 生产步骤

<Column gap="5">
  1.  收集/制作所需材料：硅、红石、金、<ItemLink id="certus_quartz_crystal" />（赛特斯石英水晶）、钻石。

  <RecipeFor id="silicon" />

  <br />

  2.  压印所需的印刷电路组件

  <Row>
    <RecipeFor id="printed_silicon" />

    <RecipeFor id="printed_logic_processor" />
  </Row>

  <Row>
    <RecipeFor id="printed_calculation_processor" />

    <RecipeFor id="printed_engineering_processor" />
  </Row>

  <br />

  3.  最终组装

  <Row>
    <RecipeFor id="logic_processor" />

    <RecipeFor id="calculation_processor" />
  </Row>

  <RecipeFor id="engineering_processor" />
</Column>