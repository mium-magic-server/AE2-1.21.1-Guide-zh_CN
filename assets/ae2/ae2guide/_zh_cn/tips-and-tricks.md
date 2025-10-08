---
navigation:
  title: 技巧与窍门
  position: 20
---

# 技巧与窍门

一些零散的小建议

* 移除 Optifine
* 你可以旋转和缩放指南书中带有缩放及注释隐藏/显示按钮的场景
* 保持网络呈树状结构，避免环路
* 除非你深刻理解[频道](ae2-mechanics/channels.md)在网络中的路由方式，否则请将完整方块的[设备](ae2-mechanics/devices.md)控制在每组8个或更少
* 选择一种木材并坚持用于所有[样板](items-blocks-machines/patterns.md)。是的，在样板中启用替换有时有效，但各处使用相同木材类型能大大减少麻烦
* 在<ItemLink id="pattern_access_terminal" />中垂直排列[样板](items-blocks-machines/patterns.md)/在[供应器](items-blocks-machines/pattern_provider.md)之间分配样板，以便配方可以并行执行
* 添加[能量电池](items-blocks-machines/energy_cells.md)使你的网络能够处理能量尖峰
* 你可以在<ItemLink id="condenser" />中使用水
* 保持网络整洁的最佳方式是不要放入随机生物战利品，如剑和盔甲。每个附魔和耐久度的独特组合都是另一个[类型](ae2-mechanics/bytes-and-types.md)
* 当返回[处理样板](items-blocks-machines/patterns.md)的结果时，必须发生"物品进入系统"事件，例如通过<ItemLink id="import_bus" />、<ItemLink id="interface" />或<ItemLink id="pattern_provider" />返回槽，你不能简单地将结果通过管道输入带有<ItemLink id="storage_bus" />的箱子
* 别忘了可以旋转和缩放指南书中带有缩放及注释隐藏/显示按钮的场景
* <ItemLink id="pattern_provider" />只会推送完整的配方批次，且仅通过单侧推送。这对于确保机器不会收到部分批次很有用，但有时你希望材料送往多个位置。你可以使用<ItemLink id="interface" />实现这一点，无论是作为["管道"子网](example-setups/pipe-subnet.md)还是利用其同时容纳多种不同物品堆叠、流体、化学品等的能力，将其用作某种中间箱子/储罐
* 你可以缩放和旋转指南书中带有缩放及注释隐藏/显示按钮的场景