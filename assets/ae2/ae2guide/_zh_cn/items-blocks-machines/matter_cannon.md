---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 物质炮
  icon: matter_cannon
  position: 410
categories:
- 工具
item_ids:
- ae2:matter_cannon
---

# 物质炮

<ItemImage id="matter_cannon" scale="4" />

物质炮是一种便携式磁轨炮，能够发射小型物品作为弹药，例如<ItemLink id="matter_ball" />和金属粒。造成的伤害取决于发射的物品，"较重"的物品（如金粒，10点伤害）比轻型物品（如物质球，2点伤害）造成的伤害更高。
每发射一次消耗1600 AE的基础能量。

当配置选项"matterCannonBlockDamage"为true时，物质炮会根据方块的硬度和弹药的伤害值来破坏方块。

其能量可通过<ItemLink id="charger" />进行补充。

物质炮的功能类似于[存储元件](storage_cells.md)，最方便的装填方式是将它放入<ItemLink id="chest" />的存储元件插槽中。

## 升级

物质炮支持通过<ItemLink id="cell_workbench" />安装以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="fuzzy_card" />允许根据损伤值划分存储单元和/或忽略物品NBT
*   <ItemLink id="inverter_card" />将过滤器从白名单切换为黑名单
*   <ItemLink id="speed_card" />增加每次射击的能量消耗，从而提高射击威力
*   <ItemLink id="void_card" />在存储单元已满时销毁插入的物品。注意设置分区！
*   <ItemLink id="energy_card" />可增加电池容量

## 配方

<RecipeFor id="matter_cannon" />