---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 导入、导出与存储
---

# 导入、导出与存储

**你的 ME 系统与世界**

AE2 中的一个重要概念是网络存储。这是网络中存储内容的地方，
通常是[存储元件](../items-blocks-machines/storage_cells.md)或 <ItemLink id="storage_bus" />
所连接的任意物品栏。大多数 AE2 [设备](../ae2-mechanics/devices.md) 都以某种方式与其交互。

例如，

*   <ItemLink id="import_bus" /> 将物品推入网络存储
*   <ItemLink id="export_bus" /> 从网络存储中拉取物品
*   <ItemLink id="interface" /> 既从网络存储拉取物品，也向网络存储推送物品
*   当你放入或取出物品，或为合成槽补充物品时，[终端](../items-blocks-machines/terminals.md) 会同时向网络存储推送和从中拉取物品
*   <ItemLink id="storage_bus" /> 并不真正向存储推送或从中拉取物品，它们向所连接的物品栏推送或从中拉取物品，
    以将其用作网络存储（因此实际上是其他设备向*它们*推送或从中拉取物品）

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/import_export_storage.snbt" />

  <BoxAnnotation color="#dddddd" min="8 1 1" max="9 1.3 2">
        输入总线将其指向的物品栏中的物品导入到网络存储中
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="8 2 1" max="9 3 1.3">
        从你的物品栏向终端放入物品，视为网络导入了该物品
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="7 0 1" max="8 1 2">
        如果接口的内部物品栏槽位未配置为存放任何物品，或者该槽位中的物品数量超过了配置的存放量，
        接口会从其内部物品栏导入物品，因此可以将物品推入接口以插入网络
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="6 0 1" max="7 1 2">
        样板供应器会从其内部返还槽物品栏导入物品，因此可以将物品推入其中以插入网络
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 1 1" max="5 2 2">
        驱动器将插入的存储元件提供为网络存储
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 1" max="4 1.3 2">
        存储总线将其指向的物品栏用作网络存储
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 1 1" max="2 1.3 2">
        输出总线将物品从网络存储导出到其指向的物品栏中
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 2 1" max="2 3 1.3">
        从终端取出物品，视为网络导出了该物品
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 1 1" max="1 2 2">
        如果接口的内部物品栏槽位配置为存放物品，
        接口会向其内部物品栏导出物品，因此可以从中拉取物品以从网络提取
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

在设计自动化和物流设置时，牢记向网络存储推送和从中拉取物品的动作/事件非常重要。

## 存储优先级

可以通过点击某些 GUI 界面右上角的扳手图标来设置优先级。
进入网络的物品将首先前往最高优先级的存储，作为其第一目的地。如果两个存储具有相同的优先级，
且其中一个已包含该物品，则物品会优先选择该存储。当白名单存储元件与其他存储处于同一优先级组时，
它们将被视为已包含该物品。从存储中移除物品时，将从优先级最低的存储中移除。
这种优先级系统意味着，随着物品被插入和移出网络存储，较高优先级的存储将被填满，而较低优先级的存储将被清空。