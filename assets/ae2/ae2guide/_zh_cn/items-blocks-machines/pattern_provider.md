---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 样板供应器
  icon: pattern_provider
  position: 210
categories:
- 设备
item_ids:
- ae2:pattern_provider
- ae2:cable_pattern_provider
---

# 样板供应器

<Row gap="20">
<BlockImage id="pattern_provider" scale="8" />
<BlockImage id="pattern_provider" p:push_direction="up" scale="8" />
<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/cable_pattern_provider.snbt" />
</GameScene>
</Row>

样板供应器是您的[自动合成](../ae2-mechanics/autocrafting.md)系统与世界交互的主要方式。它们将其[样板](patterns.md)中的材料推入相邻的容器，并且可以向其中插入物品以将其输入网络。
通常，通过将机器的输出导回附近的样板供应器（通常是推送材料的那个），而不是使用<ItemLink id="import_bus" />将机器的输出拉入网络，可以节省一个频道。

值得注意的是，由于它们直接从合成CPU中的[合成存储器](crafting_cpu_multiblock.md#crafting-storage)推送材料，它们的物品栏中实际上从不包含这些材料，因此您无法从中导出物品。您必须让供应器推送到另一个容器（如桶），然后从那里导出。

同样值得注意的是，供应器必须一次性推送所有材料，不能分批推送。这一点可以利用。

样板供应器与[子网络](../ae2-mechanics/subnetworks.md)上的接口有特殊的交互：如果接口未被修改（请求槽位中没有任何物品），供应器将完全跳过该接口，直接推送到该子网络的[存储器](../ae2-mechanics/import-export-storage.md)，跳过接口且不会用配方批次填充它，更重要的是，只有在机器内有空间时才会插入下一批材料。这在阻塞模式下也能正常工作，供应器将监视机器内的材料槽位，而不是接口内的槽位。

例如，此设置将把要熔炼的物品和燃料直接推送到熔炉的相应槽位中。您可以使用它来将样板供应到机器的多个侧面或多个机器。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/furnace_automation.snbt" />

<BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) 样板供应器：通过使用赛特斯石英扳手调整方向后的定向变体，带有相关的处理样板。

        ![铁锭样板](../assets/diagrams/furnace_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (2) 接口：默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="1.3 2 1">
        (3) 存储总线 #1：过滤为煤炭。
        <ItemImage id="minecraft:coal" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 2 0" max="1 2.3 1">
        (4) 存储总线 #2：使用反相卡过滤为黑名单模式（排除煤炭）。
        <Row><ItemImage id="minecraft:coal" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        连接到主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

这是一个向多个机器供应的通用示意图

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/provider_interface_storage.snbt" />

<BoxAnnotation color="#dddddd" min="2.7 0 1" max="3 1 2">
        接口（必须是扁平变体，非完整方块）
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 4">
        存储总线
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 0 0" max="1 1 4">
        您想要进行样板供应的位置
  </BoxAnnotation>

<IsometricCamera yaw="185" pitch="30" />
</GameScene>

支持多个具有相同样板的样板供应器，并且它们可以并行工作。

样板供应器会尝试以轮询方式将其批次推送到所有面，从而并行使用所有连接的机器。

## 变体

样板供应器有3种不同的变体：普通、定向和扁平/[线缆子部件](../ae2-mechanics/cable-subparts.md)。这影响了它们向哪些特定面推送材料、从哪些面接收物品以及提供网络连接。

*   普通样板供应器向所有面推送材料，从所有面接收输入，并且像大多数AE2机器一样，其行为类似于线缆，向所有面提供[网络连接](../ae2-mechanics/me-network-connections.md)。

*   定向样板供应器是通过在普通样板供应器上使用<ItemLink id="certus_quartz_wrench" />改变其方向制成的。它们只向选定面推送材料，从所有面接收输入，并且特意不在选定面提供[网络连接](../ae2-mechanics/me-network-connections.md)。这允许它们在推送到AE2机器时不会连接网络，如果您想创建子网络的话。

*   扁平样板供应器是[线缆子部件](../ae2-mechanics/cable-subparts.md)，因此可以在同一根线缆上放置多个，从而实现紧凑的设置。它们的行为类似于定向样板供应器的选定面，提供样板、接收输入，并且在其面上**不**提供[网络连接](../ae2-mechanics/me-network-connections.md)。

样板供应器可以在工作台中在普通和扁平变体之间切换。

## 设置

样板供应器有多种模式：

*   **阻塞模式**：如果机器中已有材料，则阻止供应器推送新一批材料。
*   **锁定合成**：可以在各种红石条件下锁定供应器，或者直到上一次合成的结果被插入到该特定样板供应器中。
*   供应器可以在<ItemLink id="pattern_access_terminal" />上显示或隐藏。

## 优先级

可以通过点击GUI右上角的扳手来设置优先级。在多个[样板](patterns.md)对应同一物品的情况下，具有较高优先级的供应器中的样板将优先于具有较低优先级的供应器中的样板被使用，除非网络没有足够材料来执行高优先级样板。

## 常见误解

出于某种原因，人们总是这样做，我不明白为什么，但我把它放在这里希望能有所帮助。（也许人们误以为<ItemLink id="export_bus" />是物品离开网络的唯一方式，不知道样板供应器也能输出物品）

这不会达到您想要的效果。如[线缆](cables.md)中所述，线缆不是物品管道，它们没有内部物品栏，供应器不会向其中推送物品。

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/assemblies/provider_misconception_1.snbt" />

  <BoxAnnotation color="#dddddd" min="1 0 3" max="2 1 4">
        不是高炉
  </BoxAnnotation>

  <IsometricCamera yaw="95" pitch="5" />
</GameScene>

由于供应器没有可以推送的目标，它将无法工作。它在这里所做的只是像一根线缆一样，将<ItemLink id="export_bus" />连接到网络。

供应器也不会以某种方式告诉<ItemLink id="export_bus" />要输出什么，输出总线只会输出您放入其过滤器中的所有东西。

我们在这里所做的本质上是这样：

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/assemblies/provider_misconception_2.snbt" />

  <BoxAnnotation color="#dddddd" min="1 0 3" max="2 1 4">
        不是高炉
  </BoxAnnotation>

  <IsometricCamera yaw="95" pitch="5" />
</GameScene>

您可能真正想做的是这样，样板供应器可以将其样板的内容导出到相邻的机器：

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/assemblies/provider_misconception_3.snbt" />

  <BoxAnnotation color="#dddddd" min="1 0 3" max="2 1 4">
        不是高炉
  </BoxAnnotation>

  <IsometricCamera yaw="95" pitch="5" />
</GameScene>

## 与分子装配室配合使用

<ItemLink id="molecular_assembler" />基本上就像任何其他机器一样。它们有一个可以插入物品的物品栏，然后对物品栏中的物品执行操作，之后，像许多机器一样，它们将结果推送到相邻的容器。因此，它们应该像任何其他机器一样与供应器一起使用，但有一个补充：

装配室可以直接接受插入其中的<ItemLink id="crafting_pattern" />、<ItemLink id="smithing_table_pattern" />或<ItemLink id="stonecutting_pattern" />所指定的样板。
这在装配线中很有用，但为每个合成配方配备一个专用的装配室会很烦人。

因此，样板供应器与装配室有一个特殊的功能，它们可以将样板数据与材料一起发送。这样，您只需将装配室放在样板供应器旁边，供应器就可以将该装配室用于其所有的合成、锻造和切石样板。

就这么简单，只需将样板放入供应器中：

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

*请注意，这里正好有8个供应器，这是可以通过单个装配室、供应器或非致密线缆路由的最大频道数。*

## 合成配方

<RecipeFor id="pattern_provider" />

<RecipeFor id="cable_pattern_provider" />