---

navigation:

  title: "附加件：AE2 导入导出卡"

  icon: ae2importexportcard:export_card

  position: 150

categories:

  - 工具

item_ids:

- ae2importexportcard:export_card

- ae2importexportcard:import_card

---



# AE2 导入导出卡



<Row>

  <ItemImage id="ae2importexportcard:export_card" scale="2" />



  <ItemImage id="ae2importexportcard:import_card" scale="2" />

</Row>



导入卡和导出卡允许你从物品栏中导入/导出物品。



## 导入卡



<ItemImage id="ae2importexportcard:import_card" scale="2" />



导入卡会从你物品栏的特定槽位中取出物品，并将其存入你的 ME 系统。



![导入卡](diagrams/import_card.png)



点击槽位会标记对勾。任何带有对勾标记的槽位中的物品都会被导入到你的 ME 系统。将物品从物品栏拖拽到顶部区域可以更改过滤器设置。



### 升级



导入卡支持以下[升级卡](items-blocks-machines/upgrade_cards.md)：



*   <ItemLink id="fuzzy_card" /> 按损伤等级过滤 和/或 忽略物品 NBT 标签

*   <ItemLink id="inverter_card" /> 将过滤器从白名单切换为黑名单



### 配方



<RecipeFor id="ae2importexportcard:import_card" />



## 导出卡



<ItemImage id="ae2importexportcard:export_card" scale="2" />



导出卡的工作方式完全相同，但会将物品从你的 ME 系统拉取到你的物品栏中。



![导出卡](diagrams/export_card.png)



要指定导出哪些物品，请将物品从物品栏拖拽到顶部的某个槽位，并点击物品栏中的一个槽位以将其更改为所需的数量。右键点击可将其清除回 X 状态。



### 升级



导出卡支持以下[升级卡](items-blocks-machines/upgrade_cards.md)：



*   <ItemLink id="fuzzy_card" /> 按损伤等级过滤 和/或 忽略物品 NBT 标签

*   <ItemLink id="speed_card" /> 将传输速度从 1 个物品提升至整组物品

*   <ItemLink id="crafting_card" /> 自动请求并合成当前不可用的物品



### 配方



<RecipeFor id="ae2importexportcard:export_card" />