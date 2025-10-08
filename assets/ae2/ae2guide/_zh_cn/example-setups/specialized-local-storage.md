---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 专用本地存储
  icon: drive
---

# 专用本地存储

利用[物品传输接口的特殊行为](../items-blocks-machines/interface.md#特殊交互)，一个[子网络](../ae2-mechanics/subnetworks.md)可以将其存储内容呈现给主网络，而无法查看主网络的存储内容，且仅占用1个[频道](../ae2-mechanics/channels.md)。

这对于某些农场的本地存储非常有用，可以防止物品溢出到主存储中。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/local_storage.snbt" />

<BoxAnnotation color="#dddddd" min="4 0 0" max="5 2 1">
        (1) 某种物品输入方式（此处为物品传输接口）
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 0 0" max="4 1 1">
        (2) 驱动器：内含若干存储元件。元件应设置为筛选农场产出物品。
        元件可安装均分卡和溢出销毁卡。
        <Row><ItemImage id="item_storage_cell_4k" scale="2" /> <ItemImage id="equal_distribution_card" scale="2" /> <ItemImage id="void_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1 0" max="4 2 0.3">
        (3) 合成终端：可查看子网络上驱动器内容，但无法查看主网络存储内容。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 0 0" max="2.3 1 1">
        (4) 物品传输接口 #2：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1.7 0 0" max="2 1 1">
        (5) 存储总线：优先级设置高于主存储，可设置为筛选农场产出物品。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 2 0.3">
        合成终端：可同时查看主网络存储内容*和*子网络内容。
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        连接主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置说明

* 第一个<ItemLink id="interface" /> (1) 直接接收农场产出的物品并将其推入子网络。
* <ItemLink id="drive" /> (2) 内含若干[存储元件](../items-blocks-machines/storage_cells.md)。元件应通过[元件工作台](../items-blocks-machines/cell_workbench.md)设置为筛选农场产出物品。
  元件可安装<ItemLink id="equal_distribution_card" />和<ItemLink id="void_card" />。
* 第二个<ItemLink id="interface" /> (4) 保持默认配置。
* <ItemLink id="storage_bus" /> 的[优先级](../ae2-mechanics/import-export-storage.md#存储优先级)设置高于主存储。可设置为筛选农场产出物品。

## 工作原理

* 子网络上的<ItemLink id="interface" />向主网络的<ItemLink id="storage_bus" />显示<ItemLink id="drive" />的内容。这意味着存储总线可以直接从驱动器元件中存取物品。
* 存储总线设置为高[优先级](../ae2-mechanics/import-export-storage.md#存储优先级)，使物品优先存回子网络而非主存储。
* 重要的是，如果子网络中的元件已满，物品不会溢出到主网络。若农场类型在堵塞时会停止运作，可使用<ItemLink id="void_card" />删除多余物品。
* 若农场产出多种物品，<ItemLink id="equal_distribution_card" />可防止单一物品占满所有元件导致其他物品无法存储。