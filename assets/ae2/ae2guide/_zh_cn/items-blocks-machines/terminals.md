---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 终端
  icon: crafting_terminal
  position: 210
categories:
- 设备
item_ids:
- ae2:terminal
- ae2:crafting_terminal
- ae2:pattern_encoding_terminal
- ae2:pattern_access_terminal
---

# 终端

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/terminals.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

虽然<ItemLink id="pattern_provider" />（样板供应器）、<ItemLink id="import_bus" />（输入总线）、<ItemLink id="storage_bus" />（存储总线）等是AE2网络与世界交互的主要方式，但终端是AE2网络与你交互的主要方式。有几种功能不同的变体。

终端会继承其所连接的[线缆](cables.md)的颜色。

它们是[线缆子部件](../ae2-mechanics/cable-subparts.md)。

## 终端放置

由于终端通常是人们放置的第一个[子部件](../ae2-mechanics/cable-subparts.md)，很容易出错并将其放反。以下是一个正确和错误操作的示例：

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/terminal_placement.snbt" />
  <IsometricCamera yaw="195" pitch="30" />

  <LineAnnotation color="#ff3333" from="2.5 .5 .5" to="4.5 2.5 .5" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#ff3333" from="2.5 2.5 .5" to="4.5 .5 .5" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#33ff33" from="-.5 2.5 .5" to="1 .5 .5" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1 .5 .5" to="1.5 1 .5" alwaysOnTop={true} thickness="0.05"/>
</GameScene>

你仍然拥有一个终端和一个能源接收器，只不过现在终端朝向正确并且实际连接到了网络，而且所有东西都占用了更小的空间。

<a name="terminal-ui"></a>

# 终端搜索

搜索框接受正则表达式（Regex）术语，例如，你可以输入“gtceu:.*ore”来获取来自Gregtech的所有矿石。学习正则表达式留给读者作为练习。

# 终端

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/blocks/terminal.snbt" />
  <IsometricCamera yaw="180" />
</GameScene>

基础终端，允许你查看和访问[网络存储](../ae2-mechanics/import-export-storage.md)的内容，并向你的[自动合成](../ae2-mechanics/autocrafting.md)设置请求物品。

## 用户界面

基础终端的用户界面有几个部分：

中心部分提供对网络存储的访问。你可以放入和取出物品。有几种鼠标/键盘快捷键：

*   左键点击抓取一组物品，右键点击抓取半组物品。
*   如果某个物品、流体等能够被[自动合成](../ae2-mechanics/autocrafting.md)，你绑定给“选取方块”（通常是中键点击）的按键会弹出一个界面来指定要合成的数量。你也可以输入公式如`3*64/2`，或输入`=32`来仅合成达到存储中32个所需数量的物品。
*   按住Shift键会将显示的物品冻结在原位，防止它们在数量变化或新物品进入系统时重新组织。
*   使用桶或其他流体容器右键点击会存入流体，在终端中用空的流体容器左键点击流体会取出流体。

左侧部分有设置按钮，用于：

*   按不同属性排序，如名称、模组和数量
*   查看存储的、可合成的或两者都看
*   查看物品、流体或两者都看
*   更改排序顺序
*   打开详细的终端设置窗口
*   更改终端用户界面的高度

右侧有用于放置<ItemLink id="view_cell" />（显示元件）的槽位。

中心部分的右上角（锤子按钮）会打开[自动合成](../ae2-mechanics/autocrafting.md)状态界面，允许你查看自动合成的进度以及每个[合成CPU](crafting_cpu_multiblock.md)正在做什么。

## 配方

<RecipeFor id="terminal" />

<a name="crafting-terminal-ui"></a>

# 合成终端

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/blocks/crafting_terminal.snbt" />
  <IsometricCamera yaw="180" />
</GameScene>

合成终端类似于普通终端，具有所有相同的设置和部分，但增加了一个合成网格，该网格会自动从[网络存储](../ae2-mechanics/import-export-storage.md)补充物品。Shift点击输出时要小心！

你应该尽快将你的终端升级为合成终端。

## 用户界面

合成终端具有与普通终端相同的用户界面，但在中间增加了一个合成网格。

还有2个额外的按钮，用于将合成网格中的物品清空到网络存储或你的物品栏中。

## 配方

<RecipeFor id="crafting_terminal" />

<a name="pattern-encoding-terminal-ui"></a>

# 样板编码终端

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/blocks/pattern_encoding_terminal.snbt" />
  <IsometricCamera yaw="180" />
</GameScene>

样板编码终端类似于普通终端，具有所有相同的设置和部分，但增加了一个[样板](patterns.md)编码界面。它看起来类似于合成终端的用户界面，但这个合成网格实际上并不执行合成。

除了合成终端之外，你还应该拥有一个这样的终端。

## 用户界面

样板编码终端具有与普通终端相同的用户界面，并增加了[样板](patterns.md)编码界面。

样板编码界面有几个部分：

一个用于插入<ItemLink id="blank_pattern" />（空白样板）的槽位。

一个用于编码样板的大箭头。

一个用于已编码样板的槽位。将一个已编码的样板放入此槽位以进行编辑，然后单击“编码”箭头。

右侧有4个标签页，用于在以下样板类型之间切换：

*   合成
*   处理
*   锻造
*   切石

中央用户界面根据要编码的样板类型而变化：

*   在合成模式下：
    *   左键点击或从JEI/REI拖拽材料以形成配方。右键点击移除材料。
    *   启用替换允许使用任何类型的木板来合成木棍等。这应仅在绝对必要时使用。
    *   流体替换允许使用存储的流体来代替桶装流体。
    *   你也可以直接从JEI/REI配方界面编码样板。

*   在处理模式下：
    *   左键点击、右键点击或从JEI/REI拖拽材料以指定配方的输入和输出。
    *   使用流体容器（如桶或流体储罐）右键点击以将该流体设置为材料，而不是桶或储罐物品。
    *   手持一组物品时，左键点击放置整组，右键点击放置一个物品。左键点击现有的材料堆叠以移除整组，右键点击将堆叠减少1。你绑定给“选取方块”（通常是中键点击）的按键允许你指定物品或流体的精确数量。
    *   输出槽有一个主要输出和用于你可能希望自动合成算法知道的任何次要输出的空间。
    *   输入和输出槽都可以滚动，因此你可以有81种不同的材料和26种次要输出。
    *   你也可以直接从JEI/REI配方界面编码样板。

*   锻造和切石模式的用户界面分别类似于锻造台和切石机。

## 配方

<RecipeFor id="pattern_encoding_terminal" />

<a name="pattern-access-terminal-ui"></a>

# 样板管理终端

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/blocks/pattern_access_terminal.snbt" />
  <IsometricCamera yaw="180" />
</GameScene>

样板管理终端用于解决一个特定问题：在密集的<ItemLink id="pattern_provider" />（样板供应器）和<ItemLink id="molecular_assembler" />（分子装配室）塔中，你无法物理访问供应器以插入新样板。此外，也许你很懒，不想穿过你的基地去插入一个[样板](patterns.md)。样板管理终端允许访问网络上的所有样板供应器。

## 用户界面

此终端具有与其他所有终端不同的用户界面。

它有终端高度和显示哪些样板供应器的设置。

终端中的每一行对应一个特定的样板供应器。

终端中的样板供应器按它们连接的方块或你给它们的名称（在铁砧中或使用<ItemLink id="name_press" />（名称压印模板））排序。

## 配方

<RecipeFor id="pattern_access_terminal" />