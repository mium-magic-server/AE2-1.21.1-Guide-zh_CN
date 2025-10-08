---
navigation:
  parent: 示例配置/示例配置索引.md
  title: 接口自动补货
  icon: interface
---

# 接口自动补货

有人可能会问："我该如何保持各种物品的库存量，并在需要时自动合成更多？"

一种解决方案是使用<ItemLink id="interface" />和<ItemLink id="crafting_card" />，从你的网络[自动合成](../ae2-mechanics/autocrafting.md)中自动请求新物品。此配置更适合维持少量多种物品的库存。

此演示配置进行了截断以避免过宽，最优方案可能是使用4个<ItemLink id="interface" />和4个<ItemLink id="storage_bus" />，以利用常规[线缆](../items-blocks-machines/cables.md)中的所有8个[频道](../ae2-mechanics/channels.md)。

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_autostocking.snbt" />

<BoxAnnotation color="#dddddd" min="0 0 0" max="2 1 1">
        (1) 接口：设置为保持所需物品在其中。它们装有合成卡。
        <ItemImage id="crafting_card" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 0" max="2 1.3 1">
        (2) 存储总线："输入/输出模式"设置为"仅取出"。
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## 配置

* <ItemLink id="interface" />（1）设置为在其中保持所需物品，通过将所需物品点击放入其顶部槽位或从JEI拖入顶部槽位，然后点击槽位上方的扳手图标设置数量。它们装有<ItemLink id="crafting_card" />。
* <ItemLink id="storage_bus" />（2）设置为将"输入/输出模式"设置为"仅取出"。

## 工作原理

1. 如果<ItemLink id="interface" />无法从[网络存储](../ae2-mechanics/import-export-storage.md)中获取足够数量的已配置物品（且其装有<ItemLink id="crafting_card" />），它将请求网络的[自动合成](../ae2-mechanics/autocrafting.md)来制作更多该物品。
2. <ItemLink id="storage_bus" />允许网络访问接口中的内容。