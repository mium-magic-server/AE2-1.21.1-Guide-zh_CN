---

导航:

    上级: epp_intro/epp_intro-index.md

    标题: ME标签存储总线

    图标: extendedae:tag_storage_bus

分类:

- 扩展设备

物品ID:

- extendedae:tag_storage_bus

---



# ME标签存储总线



<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/cable_tag_storage_bus.snbt"></ImportStructure>

</GameScene>



ME标签存储总线是一种可通过物品或流体标签进行过滤的<ItemLink id="ae2:storage_bus" />，并支持一些基本逻辑运算符。



以下是一些示例：



- 仅接受原矿



c:raw_materials/*



- 接受所有锭和宝石



c:ingots/* | c:gems/*