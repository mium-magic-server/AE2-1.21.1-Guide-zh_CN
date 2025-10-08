---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 元件清空与填充装置
  icon: io_port
---

# 元件清空与填充装置

或许有人会问："如何快速将存储元件内容清空至箱子、抽屉阵列或背包中？或者反过来，如何将容器中的物品快速填充至存储元件？"

答案是使用 <ItemLink id="io_port" /> 并设置子网限制其物品存取范围。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/cell_dumper_filler.snbt" />

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 2 1">
        (1) I/O端口：可通过GUI中央的箭头按钮设置为"从元件导入网络"或"传输数据到存储元件"模式。
        配备3个加速卡。
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 0.7 0" max="1 1 1">
        (2) 存储总线：保持默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#33dd33" min="0 1 0" max="1 2 1">
        在此处放置需要填充或清空的容器。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 0.35 0.35" max="2.3 0.65 0.65">
        石英纤维：仅当能量源来自其他网络时需要。
  </BoxAnnotation>

<DiamondAnnotation pos="3 0.5 0.5" color="#00ff00">
        连接至能量源（其他网络或能源接收器）。
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置说明

* <ItemLink id="io_port" /> (1) 可通过GUI中央的箭头按钮设置为"从元件导入网络"或"传输数据到存储元件"模式，配备3个加速卡以实现最大传输速度
* <ItemLink id="storage_bus" /> (2) 保持默认配置

## 工作原理

### "从元件导入网络"模式

1. <ItemLink id="io_port" /> 尝试将插入的[存储元件](../items-blocks-machines/storage_cells.md)内容导入至[网络存储](../ae2-mechanics/import-export-storage.md)
2. 子网中唯一的存储设备是 <ItemLink id="storage_bus" />，它会将物品/流体等存入前方连接的容器
* <ItemLink id="energy_cell" /> 提供充足的[能量](../ae2-mechanics/energy.md)缓冲，确保网络不会因每游戏刻大量传输操作而耗尽能量

### "传输数据到存储元件"模式

1. <ItemLink id="io_port" /> 尝试将[网络存储](../ae2-mechanics/import-export-storage.md)内容导出至插入的[存储元件](../items-blocks-machines/storage_cells.md)
2. 子网中唯一的存储设备是 <ItemLink id="storage_bus" />，它会从前方连接的容器中提取物品/流体等
* <ItemLink id="energy_cell" /> 提供充足的[能量](../ae2-mechanics/energy.md)缓冲，确保网络不会因每游戏刻大量传输操作而耗尽能量