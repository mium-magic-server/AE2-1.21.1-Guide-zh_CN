---
navigation:
  parent: example-setups/example-setups-index.md
  title: 存储类型与网络整洁性
  icon: drive
---

# 多种存储类型与保持网络整洁

通过使用过滤器、[分区](../items-blocks-machines/cell_workbench.md)和[存储优先级](../ae2-mechanics/import-export-storage.md#storage-priority)，
你可以为不同类型的物品设置多个层级的存储。

常见的存储类型包括：
* **通用存储**：用于存放数量从几个到几千个不等的各种杂项物品。通常使用小型[存储元件](../items-blocks-machines/storage_cells.md)，
  如4k或16k。
* **批量存储**：用于存放数量超过数千的物品，如圆石或铁锭。使用大型存储元件，如256k
  或来自MEGA附加模组的元件。
* **农场本地存储**：如[专用本地存储](specialized-local-storage.md)和
  [各种](simple-certus-farm.md) [石英](semiauto-certus-farm.md) [农场](advanced-certus-farm.md)中所述。

优先级设置的原则是：当物品被输入到主网络时，系统会首先尝试将它们存入专用的
批量或本地存储中，如果无法存入（由于过滤器和分区限制），则会放入通用存储。
这意味着物品**不会主动地**从一个存储移动到另一个存储，而是会在进出网络时自然“迁移”。
若要主动移动物品，请使用<ItemLink id="io_port" />。

<GameScene zoom="3" interactive={true}>
  <ImportStructure src="../assets/assemblies/network_storage_types.snbt" />

    <BoxAnnotation color="#33dd33" min="11 0 1" max="12 1.3 2" thickness="0.05">
        批量存储。此处是一个连接在大容量存储（如抽屉）上的过滤型存储总线。该存储总线被设置为仅过滤
        煤炭。它具有高优先级，因此每当煤炭进入网络时，都会存入此存储总线；而每当从网络中提取煤炭时，
        会从*除此处之外的所有地方*提取，因此煤炭会“迁移”到这个抽屉中。

        重要提示：像抽屉这样经过优化的大容量库存可以这样使用，但像巨型箱子这样具有许多槽位的*未优化*大容量库存，
        在与存储总线一起使用时会对性能造成严重影响。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="11 0 3" max="12 1 4" thickness="0.05">
        批量存储。此处是一个位于驱动器中的已分区256k存储元件，具有高优先级。该元件被分区为仅存放
        圆石和铁锭。它装有一张均分卡，因此不会被圆石完全填满，从而为铁锭留出空间。
        该驱动器具有高优先级，因此每当圆石或铁锭进入网络时，都会存入此处；
        而每当从网络中提取圆石或铁锭时，会从*除此处之外的所有地方*提取，因此圆石和铁锭会“迁移”到这个元件中。
    </BoxAnnotation>

    <BoxAnnotation color="#33dddd" min="11 0 5" max="12 1 6" thickness="0.05">
        通用存储。此处是一个装满16k存储元件的驱动器。这些元件未进行分区。该驱动器具有中性优先级
        （此处为0），因此当有物品进入网络时，会优先存入专用的批量或本地存储；
        而当从网络中提取物品时，会优先从此处提取，因此那些拥有专用存储的物品会自然地
        从通用存储中“迁移”出去。
    </BoxAnnotation>

    <BoxAnnotation color="#88ff88" min="11 0 8" max="12 1 9" thickness="0.05">
        这个I/O端口在保持网络整洁方面扮演着重要角色。因为存储优先级不会*主动*
        移动物品，所以用于通用存储的存储元件应定期通过I/O端口进行“整理”，
        将那些本应存入专用存储的物品移动到对应的专用存储中。这种“碎片整理”操作
        能确保物品不会分散存储在多个地方。
    </BoxAnnotation>

    <BoxAnnotation color="#dd3333" min="14 0 11" max="15 1 12" thickness="0.05">
        怪物农场的本地存储。此驱动器中的存储元件被分区为只存放你想要保留的掉落物，如骨头和箭。
        驱动器本身未设置优先级，因为影响优先级的是从主网络访问此子网的存储总线。
        这些存储元件装有均分卡和溢出销毁卡。
    </BoxAnnotation>

    <BoxAnnotation color="#dd3333" min="14 1 10" max="15 2.3 11" thickness="0.05">
        怪物农场的本地存储。这个存储总线-接口的设置允许主网络访问此子网的存储。
        该存储总线被设置为高优先级，并过滤为只允许访问子网存储元件中存放的物品。

        重要提示：由于子网中设置了垃圾桶，请务必对此存储总线进行过滤，否则它会开始销毁
        *进入网络的每一种物品、流体等一切东西*！
    </BoxAnnotation>

    <BoxAnnotation color="#dd3333" min="14 0 9" max="15 1.3 10" thickness="0.05">
        怪物农场的本地存储。这个连接在物质聚合器上的存储总线被设置为比驱动器更低的优先级。这意味着
        无法存入驱动器中存储元件的怪物掉落物会溢出到这里并被处理掉。这一点很重要，
        可以防止子网被各种随机垃圾（如几乎损坏的弓）塞满。
    </BoxAnnotation>

    <BoxAnnotation color="#dd33dd" min="8 1 11.7" max="9 2.3 13" thickness="0.05">
        西瓜农场的本地存储。此设置使用了在各种石英农场示例中类似的方法。子网上的一个存储总线
        将种植的产物输入到一个桶中。主网络上的另一个存储总线（过滤为西瓜片且具有高优先级）
        使主网络能够访问这些种植产物。
    </BoxAnnotation>

  <IsometricCamera yaw="270" pitch="30" />
</GameScene>