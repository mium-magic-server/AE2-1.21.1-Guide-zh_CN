---
navigation:
  title: ME 请求器
  icon: requester
  position: 100
item_ids:
  - merequester:requester
  - merequester:requester_terminal
---

# ME 请求器

<Row>
  <ItemImage id="requester" scale="3"/>
  <ItemImage id="requester_terminal" scale="3"/>
</Row>

一个附加模组，允许你在 [ME 系统](ae2:getting-started.md#your-very-first-me-system)中保持物品和流体的库存。
<br/>

## 开始使用

首先放置一个 <ItemLink id="requester"/> 并将其连接到你的网络。确保将其连接到与你的[自动合成](ae2:ae2-mechanics/autocrafting.md)逻辑所在的同一网络中。它应托管你的[合成 CPU](ae2:ae2-mechanics/autocrafting.md#the-crafting-cpu) 和 <ItemLink id="ae2:pattern_provider"/>。

<RecipeFor id="requester"/>

为了使 <ItemLink id="requester"/> 正常工作，你需要确保想要保持库存的物品或流体有对应的样板，并且在你作为玩家请求时能够被合成。它只会自动化请求过程本身。合成由 [ME 系统](ae2:getting-started.md#your-very-first-me-system) 处理。
<br/>

<FloatingImage src="assets/gui.png" align="right"/>

## 配置

首次打开 <ItemLink id="requester"/> 时，你将看到请求设置的概览。单个方块可以承载的槽位数量可在配置中调整。GUI 的每一行代表一个独立的请求。
<br/>

### 切换开关

左侧的复选框用于切换该行配置的请求。当请求被禁用时，不会进行任何检查，也不会维持你请求的库存。<br/>
这可用于临时禁用特定请求，或在你仍在修改某行时防止 <ItemLink id="requester"/> 发出合成任务。
<br/>

### 库存内容

在第二列中，你可以指定想要保持库存的内容。这些槽位是虚影槽，不会持有实际物品。将物品拖到槽位时，你可以右键单击将数量设置为 1，或左键单击使用你拖动的堆叠数量。将装有流体的桶拖到槽位时，你可以右键单击设置包含的流体，或左键单击设置桶本身。你也可以按住 Shift 键单击物品来快速设置物品类型。如果你的物品栏中没有所需的物品，你也可以从 Applied Energistics 支持的配方查看器中拖放。
<br/>

### 库存容量

库存容量字段指示要保持多少库存。首先指定库存内容，然后输入所需的值。对于非物品请求，该字段将适应类型。例如，显示 `B` 表示流体的桶数。<br/>
当当前库存低于指定数量时，<ItemLink id="requester"/> 将请求更多。
<br/>

### 并行大小

下一个输入字段指定一旦当前库存低于库存容量字段中指定的阈值时将请求的批次大小。<br/>
这可用于减轻[合成 CPU](ae2:ae2-mechanics/autocrafting.md#the-crafting-cpu) 和合成所用机器的压力，因为会一次性请求全部数量，而不是多个独立任务。
<br/>

### 提交按钮

要将更改应用到请求，请在库存容量和并行大小字段中输入所需的值，然后按 Enter 键或单击当前行右侧的提交按钮。单击任何其他行将把值重置为先前的状态。
<br/>

### 状态栏

输入框和提交按钮下方的条形图反映了请求的当前状态。
<br clear="all" />
<br/>

## 状态

每个请求的状态栏中会显示以下状态。
<br/>

### 灰色 - 空

当前行被禁用或未指定库存内容。
<br/>

### 绿色 - 空闲

已达到目标库存量，或者配置的请求没有对应的样板。
<br/>

### 红色 - 缺少材料

系统缺少发出当前任务所需的材料。一旦在系统中找到足够的材料，它将继续。
<br/>

### 黄色 - 合成中

所需的请求当前正在合成中。请求器正在等待任务完成。<br/>
在此状态激活期间，<ItemLink id="requester"/> 内相应请求的设置被锁定，无法更改。
<br/>

### 紫色 - 输出中

<ItemLink id="requester"/> 已从当前任务接收到所有结果，并正尝试将其输出到存储系统中。<br/>
此状态通常不可见。如果它激活时间过长，意味着你的存储系统空间不足。
<br/>

### 方块外观

如果 <ItemLink id="requester"/> 中的任何请求具有除空闲或空以外的任何状态，它将改变其外观。

<Row>
  <Column>
    未激活
    <BlockImage id="requester" scale="3" p:active="false"/>
  </Column>
  <Column>
    已激活
    <BlockImage id="requester" scale="3" p:active="true"/>
  </Column>
</Row>
<br/>

## 终端

该模组还提供了一个名为 <ItemLink id="requester_terminal"/> 的新终端。它允许你从一个中心点访问同一网络中的所有 <ItemLink id="requester"/>。

该终端具有与 <ItemLink id="ae2:pattern_access_terminal"/> 相同的功能，并允许你搜索特定请求。由于所有 <ItemLink id="requester"/> 默认具有相同的名称，所有请求将被分组在同一标题下。如果你希望在 <ItemLink id="requester_terminal"/> 中有单独的 <ItemLink id="requester"/> 组，你可以在铁砧中或使用 <ItemLink id="ae2:name_press"/> 重命名它们。