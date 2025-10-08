---
navigation:
  parent: example-setups/example-setups-index.md
  title: 处理器自动化
  icon: logic_processor
---

# 处理器生产自动化

自动化生产[处理器](../items-blocks-machines/processors.md)的方法有很多种，这是其中之一。

这种通用布局可以使用任何类型的物品物流管道、导管或任何模组所称的传输方式来实现，只要能够进行过滤即可。

![工艺流程示意图](../assets/diagrams/processor_flow_diagram.png)

以下将详细介绍如何仅使用 AE2 和["管道"子网络](pipe-subnet.md)来实现。

请注意，由于此设置使用了<ItemLink id="pattern_provider" />，其目的是集成到您的[自动合成](../ae2-mechanics/autocrafting.md)系统中。如果您只想独立自动化处理器生产，请将样板供应器替换为另一个桶，并直接将原料放入上方的桶中。

这个设计恰好与旧版 AE2 向后兼容，因为即使<ItemLink id="inscriber" />具有面朝向性，管道子网络仍然可以从正确的面插入和提取物品。

## 关于样板编码的说明

通常，您需要编码的[样板](../items-blocks-machines/patterns.md)**可能与您在 JEI 中看到的不一致**，或者与您点击 JEI 中的 + 按钮时输出的样板不同。
在这种情况下，JEI 会输出 2 个独立的样板，一个用于打印组件，另一个用于最终组装，并且打印组件的样板会包含一个[压印模板](../items-blocks-machines/presses.md)。这不是我们想要的，因为这与我们的设置不符。我们需要的是 1 个输入原始资源并输出完整处理器的样板，并且由于压印模板已经存在于压印器中，我们不应将其包含在样板中。

---

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/processor_automation.snbt" />

  <BoxAnnotation color="#dddddd" min="5 1 0" max="6 2 1" thickness=".05">
        (1) 样板供应器：默认配置，包含相关的处理样板。

        <Row>
            ![逻辑处理器样板](../assets/diagrams/logic_pattern_small.png)
            ![运算处理器样板](../assets/diagrams/calculation_pattern_small.png)
            ![工程处理器样板](../assets/diagrams/engineering_pattern_small.png)
        </Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4.7 2 0" max="5 3 1" thickness=".05">
        (2) 存储总线 #1：默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 1 0" max="4.3 2 1" thickness=".05">
        (3) 输出总线 #1：过滤设置为硅，配备 2 张加速卡
        <Row><ItemImage id="silicon" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 4 0" max="4.3 3 1" thickness=".05">
        (4) 输出总线 #2：过滤设置为金锭，配备 2 张加速卡
        <Row><ItemImage id="minecraft:gold_ingot" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 5 0" max="4.3 4 1" thickness=".05">
        (5) 输出总线 #3：过滤设置为赛特斯石英水晶，配备 2 张加速卡
        <Row><ItemImage id="certus_quartz_crystal" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 6 0" max="4.3 5 1" thickness=".05">
        (6) 输出总线 #4：过滤设置为钻石，配备 2 张加速卡
        <Row><ItemImage id="minecraft:diamond" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 3 0" max="2 2 1" thickness=".05">
        (7) 输出总线 #5：过滤设置为红石粉，配备 2 张加速卡
        <Row><ItemImage id="minecraft:redstone" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 1 0" max="3 2 1" thickness=".05">
        (8) 压印器 #1：默认配置。装有硅压印模板和 4 张加速卡
        <Row><ItemImage id="silicon_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 3 0" max="3 4 1" thickness=".05">
        (9) 压印器 #2：默认配置。装有逻辑压印模板和 4 张加速卡
        <Row><ItemImage id="logic_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 4 0" max="3 5 1" thickness=".05">
        (10) 压印器 #3：默认配置。装有运算压印模板和 4 张加速卡
        <Row><ItemImage id="calculation_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 5 0" max="3 6 1" thickness=".05">
        (11) 压印器 #4：默认配置。装有工程压印模板和 4 张加速卡
        <Row><ItemImage id="engineering_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 2 0" max="1 3 1" thickness=".05">
        (12) 压印器 #5：默认配置。装有 4 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 2 0" max="3 1 1" thickness=".05">
        (13) 输入总线 #1：默认配置，配备 2 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 4 0" max="3 3 1" thickness=".05">
        (14) 输入总线 #2：默认配置，配备 2 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 5 0" max="3 4 1" thickness=".05">
        (15) 输入总线 #3：默认配置，配备 2 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 6 0" max="3 5 1" thickness=".05">
        (16) 输入总线 #4：默认配置，配备 2 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 3 0" max="1 3.3 1" thickness=".05">
        (17) 存储总线 #2：默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 1.7 0" max="1 2 1" thickness=".05">
        (18) 存储总线 #3：默认配置。
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 2 0" max="0.7 3 1" thickness=".05">
        (19) 输入总线 #5：默认配置，配备 2 张加速卡
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="5 0.7 0" max="6 1 1" thickness=".05">
        (20) 存储总线 #4：默认配置。
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.3 2.7 0.3" max="3.7 3 0.7" thickness=".05">
        石英纤维为所有 3 个压印器供能，因为压印器的作用类似于线缆，因此可以传输能量。
  </BoxAnnotation>

<DiamondAnnotation pos="7 1.5 0.5" color="#00ff00">
        连接至主网络
    </DiamondAnnotation>

  <IsometricCamera yaw="185" pitch="5" />
</GameScene>

## 配置说明

* <ItemLink id="pattern_provider" /> (1) 为默认配置，包含相关的<ItemLink id="processing_pattern" />。
  请注意，样板直接从原始资源指向完成的处理器，并且**不**包含[压印模板](../items-blocks-machines/presses.md)。

  ![逻辑处理器样板](../assets/diagrams/logic_pattern.png)
  ![运算处理器样板](../assets/diagrams/calculation_pattern.png)
  ![工程处理器样板](../assets/diagrams/engineering_pattern.png)

* 所有的<ItemLink id="storage_bus" /> (2, 17, 18, 20) 均为默认配置。
* 所有的<ItemLink id="export_bus" /> (3-7) 均过滤为相应的原料。它们配备有 2 张<ItemLink id="speed_card" />。
    <Row>
      <ItemImage id="silicon" scale="2" />
      <ItemImage id="minecraft:gold_ingot" scale="2" />
      <ItemImage id="certus_quartz_crystal" scale="2" />
      <ItemImage id="minecraft:diamond" scale="2" />
      <ItemImage id="minecraft:redstone" scale="2" />
    </Row>
* 所有的<ItemLink id="import_bus" /> (13-16, 19) 均为默认配置。它们配备有 2 张<ItemLink id="speed_card" />。
* 所有的<ItemLink id="inscriber" />均为默认配置。它们装有相应的[压印模板](../items-blocks-machines/presses.md)和 4 张<ItemLink id="speed_card" />。
   <Row>
     <ItemImage id="silicon_press" scale="2" />
     <ItemImage id="logic_processor_press" scale="2" />
     <ItemImage id="calculation_processor_press" scale="2" />
     <ItemImage id="engineering_processor_press" scale="2" />
   </Row>

## 工作原理

1. <ItemLink id="pattern_provider" /> 将原料推入桶中。
2. 第一个[管道子网络](pipe-subnet.md)（橙色）从桶中取出硅、红石粉以及相应处理器所需的原料（金锭、赛特斯石英水晶或钻石），并将其放入相应的<ItemLink id="inscriber" />中。
3. 前四个<ItemLink id="inscriber" />分别制造<ItemLink id="printed_silicon" />、<ItemLink id="printed_logic_processor" />、<ItemLink id="printed_calculation_processor" />或<ItemLink id="printed_engineering_processor" />。
4. 第二个和第三个[管道子网络](pipe-subnet.md)（绿色）从前四个<ItemLink id="inscriber" />中取出打印好的电路板，并将其放入第五个用于最终组装的<ItemLink id="inscriber" />中。
5. 第五个<ItemLink id="inscriber" />组装[处理器](../items-blocks-machines/processors.md)。
6. 第四个[管道子网络](pipe-subnet.md)（紫色）将处理器放入样板供应器，使其返回到主网络。