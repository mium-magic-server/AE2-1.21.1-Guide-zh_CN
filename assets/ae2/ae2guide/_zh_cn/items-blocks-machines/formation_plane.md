---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 成型面板
  icon: formation_plane
  position: 210
categories:
- 设备
item_ids:
- ae2:formation_plane

---

# 成型面板

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/formation_plane.snbt" />
</GameScene>

成型面板用于放置方块和掉落物品。其工作方式类似于一个仅存入的<ItemLink id="storage_bus" />，
当物品通过[设备](../ae2-mechanics/devices.md)（如<ItemLink id="import_bus" />和<ItemLink id="interface" />）输入到[网络存储](../ae2-mechanics/import-export-storage.md)中并被“存储”时，它会执行放置/掉落操作。

<GameScene zoom="8" interactive={true}>
  <ImportStructure src="../assets/assemblies/formation_plane_demonstration.snbt" />
  <IsometricCamera yaw="255" pitch="30" />
</GameScene>

请注意，这类似于[管道子网络](../example-setups/pipe-subnet.md)中的输入总线 -> 存储总线和接口 -> 存储总线的管道结构。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/import_storage_pipe.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_storage_pipe.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

该[设备](../ae2-mechanics/devices.md)利用了存储总线在诸如[管道子网络](../example-setups/pipe-subnet.md)等场景中的工作机制，
如果你希望掉落物品/放置方块而不是传输物品，它可以替代这些设置中的存储总线。

它们是[线缆子部件](../ae2-mechanics/cable-subparts.md)。

**请记住在你的区块声明中启用假玩家**

## 过滤

默认情况下，成型面板会放置/掉落任何物品。将其过滤槽中放入物品将作为白名单，仅允许放置这些特定物品。

即使你实际上没有某种物品，也可以从 JEI/REI 中将物品和流体拖入过滤槽。

使用流体容器（如桶或流体储罐）右键点击，可以设置该流体作为过滤器，而不是桶或储罐物品本身。

## 优先级

可以通过点击图形用户界面右上角的扳手来设置优先级。
进入网络的物品将优先存入优先级最高的存储设备。

## 设置

*   成型面板可以设置为在世界中放置方块或掉落物品

## 升级

成型面板支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="capacity_card" />增加过滤槽的数量
*   <ItemLink id="fuzzy_card" />允许面板根据损坏等级进行过滤和/或忽略物品NBT
*   <ItemLink id="inverter_card" />将过滤器从白名单切换为黑名单

## 配方

<RecipeFor id="formation_plane" />