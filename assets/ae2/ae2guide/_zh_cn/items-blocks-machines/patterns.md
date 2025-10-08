---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 样板
  icon: crafting_pattern
  position: 410
categories:
- 工具
item_ids:
- ae2:blank_pattern
- ae2:crafting_pattern
- ae2:processing_pattern
- ae2:smithing_table_pattern
- ae2:stonecutting_pattern
---

# 样板

<ItemImage id="crafting_pattern" scale="4" />

样板在<ItemLink id="pattern_encoding_terminal" />（样板编码终端）中使用空白样板制作而成，并可插入<ItemLink id="pattern_provider" />（样板供应器）
或<ItemLink id="molecular_assembler" />（分子装配室）中。

针对不同用途，有几种不同类型的样板：

*   <ItemLink id="crafting_pattern" />（合成样板）用于编码工作台的合成配方。它们可以直接放入<ItemLink id="molecular_assembler" />（分子装配室）中，使其在获得材料时自动合成产物，但它们的主要用途是放在与分子装配室相邻的<ItemLink id="pattern_provider" />（样板供应器）中。
    在这种情况下，样板供应器具有特殊行为，会将相关样板连同材料一起发送给相邻的装配室。
    由于装配室会自动将合成产物弹出到相邻的容器中，因此一个连接到样板供应器的装配室就足以实现合成样板的自动化。

***

*   <ItemLink id="smithing_table_pattern" />（锻造台样板）与合成样板非常相似，但它们编码的是锻造台的配方。它们同样通过样板供应器和分子装配室实现自动化，并且工作方式完全相同。实际上，合成、锻造和切石样板可以
    在同一个装置中使用。

***

*   <ItemLink id="stonecutting_pattern" />（切石机样板）与合成样板非常相似，但它们编码的是切石机的配方。它们同样通过样板供应器和分子装配室实现自动化，并且工作方式完全相同。实际上，合成、锻造和切石样板可以
    在同一个装置中使用。

***

*   <ItemLink id="processing_pattern" />（处理样板）是自动合成灵活性的主要来源。它们是最通用的类型，简单地
    声明“如果样板供应器将这些材料推送到相邻的容器中，ME系统将在不久的将来或遥远的未来某个时间点收到这些物品”。
    它们是你用几乎所有模组机器、熔炉等实现自动合成的方式。因为它们用途非常
    通用，并且不关心从推送材料到接收结果之间发生了什么，所以你可以做一些非常奇特的事情，比如将
    材料输入到整个复杂的工厂生产链中，该生产链会分拣物品，从无限生产的
    农场获取其他材料，打印整部《蜜蜂总动员》的剧本，只要ME系统得到样板指定的结果，它就不关心过程。事实上，
    它甚至不关心材料是否与结果有任何关系。你可以告诉它“1个樱桃木板 = 1个下界之星”，并让你的凋灵农场在收到一个樱桃木板时杀死一个凋灵，这也能正常工作。

支持多个具有相同样板的<ItemLink id="pattern_provider" />（样板供应器）并行工作。此外，你可以让一个样板指定，
例如，8个圆石 = 8个石头，而不是1个圆石 = 1个石头，这样样板供应器每次操作都会将8个圆石插入
你的熔炼装置中，而不是一次一个。

## 配方

<RecipeFor id="blank_pattern" />