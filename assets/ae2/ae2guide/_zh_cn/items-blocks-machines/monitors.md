---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 显示器
  icon: storage_monitor
  position: 210
categories:
- 设备
item_ids:
- ae2:storage_monitor
- ae2:conversion_monitor
---

# 显示器

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/assemblies/monitors.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

显示器允许在不打开图形界面的情况下，可视化并交互单个物品或流体类型。

显示器会继承其所依附[线缆](cables.md)的颜色。

如果显示器位于地板或天花板上，可以使用<ItemLink id="certus_quartz_wrench" />进行旋转。

它们是[线缆子部件](../ae2-mechanics/cable-subparts.md)。

# 存储监控器

可显示一种物品或流体及其数量。将它们放置在农场或其他设施旁边...

*不*需要[频道](../ae2-mechanics/channels.md)。

按键绑定：

*   手持物品右键点击或手持流体容器双击右键，可将显示器设置为该物品/流体。
*   空手右键点击可清除显示器设置。
*   空手Shift+右键点击可锁定显示器。

## 合成配方

<RecipeFor id="storage_monitor" />

# 交换监控器

交换监控器类似于存储监控器，但允许你存入或提取其配置的物品。

如果配置的物品是[可自动合成](../ae2-mechanics/autocrafting.md)的且库存中没有，尝试提取物品将改为打开一个界面以指定要合成的数量。

*需要*[频道](../ae2-mechanics/channels.md)。

额外按键绑定：

*   左键点击可提取一组配置的物品，若库存中没有则请求合成该物品。
*   手持任意物品右键点击可存入该物品。
*   空手右键点击可存入物品栏中所有配置的物品。

## 合成配方

<RecipeFor id="conversion_monitor" />