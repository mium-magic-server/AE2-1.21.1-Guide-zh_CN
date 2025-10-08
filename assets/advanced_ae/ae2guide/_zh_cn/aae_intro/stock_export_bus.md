---

navigation:

  parent: aae_intro/aae_intro-index.md

  title: 库存输出总线

  icon: advanced_ae:stock_export_bus_part

categories:

  - 高级物品

item_ids:

  - advanced_ae:stock_export_bus_part

---



# 库存输出总线



<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/cable_stock_export_bus.snbt"></ImportStructure>

</GameScene>



库存输出总线可配置为导出精确数量的过滤物品堆叠。它会持续追踪目标容器中当前存在的数量，且不会插入超过设定数值的物品。配置时需打开界面，将所需物品拖入过滤槽位，并通过中键点击来设定数量。请注意，它不会调节输出，这意味着当物品/流体超过配置数量时，它不会从容器中提取多余的物品/流体。