---

navigation:

    parent: epp_intro/epp_intro-index.md

    title: ME阈值电平发射器

    icon: extendedae:threshold_level_emitter

categories:

- 扩展设备

item_ids:

- extendedae:threshold_level_emitter

---



# ME阈值电平发射器



<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/cable_threshold_level_emitter.snbt"></ImportStructure>

</GameScene>



其工作原理类似于复位-置位锁存器。当网络中物品数量低于下限阈值时，它会关闭红石信号；当数量超过上限阈值时，它会激活红石信号。



例如，设定下限阈值为100，上限阈值为150。



初始状态下网络为空，发射器将保持未激活状态。



随着物品数量增长并超过150时，发射器将发出红石信号。



当物品数量下降但仍高于150时，发射器仍会保持信号输出。



最终当物品数量低于100时，发射器将会关闭信号输出。