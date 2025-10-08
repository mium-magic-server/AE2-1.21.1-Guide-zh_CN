---

navigation:

    parent: epp_intro/epp_intro-index.md

    title: 装配矩阵

    icon: extendedae:assembler_matrix_frame

categories:

- 扩展设备

item_ids:

- extendedae:assembler_matrix_frame

- extendedae:assembler_matrix_wall

- extendedae:assembler_matrix_glass

- extendedae:assembler_matrix_pattern

- extendedae:assembler_matrix_crafter

- extendedae:assembler_matrix_speed

---



# 装配矩阵



<Row>

<BlockImage id="extendedae:assembler_matrix_frame" p:formed="true" p:powered="true" scale="5"></BlockImage>

<BlockImage id="extendedae:assembler_matrix_wall" scale="5"></BlockImage>

<BlockImage id="extendedae:assembler_matrix_glass" scale="5"></BlockImage>

</Row>

<Row>

<BlockImage id="extendedae:assembler_matrix_pattern" scale="5"></BlockImage>

<BlockImage id="extendedae:assembler_matrix_crafter" scale="5"></BlockImage>

<BlockImage id="extendedae:assembler_matrix_speed" scale="5"></BlockImage>

</Row>



装配矩阵是一个多方块结构。它是 <ItemLink id="ae2:molecular_assembler" /> 和 <ItemLink id="ae2:pattern_provider" /> 的结合体。

它可以同时运行大量合成任务（只要你的ME网络中有足够的 <ItemLink id="ae2:crafting_accelerator" />），并为你节省频道。



## 结构



<GameScene zoom="3" background="transparent" interactive={true}>

  <ImportStructure src="../structure/assembler_matrix.snbt"></ImportStructure>

</GameScene>



它是一个长方体，边长在3到7格之间。

- 边缘由装配矩阵框架构成。
- 表面由装配矩阵墙壁/玻璃构成。
- 内部由装配矩阵样板/合成/速度核心构成。

一个有效的装配矩阵必须至少包含一个样板核心和一个合成核心。
它必须被完全填满，不能是空心的。
当装配矩阵正确成型并通电后，框架上的线条会变成蓝色。



## 装配矩阵核心



共有3种不同的装配矩阵核心。

- 装配矩阵样板核心

装配矩阵仅从其样板核心获取样板。每个样板核心为装配矩阵提供36个样板槽位。

- 装配矩阵合成核心

装配矩阵会将接收到的合成任务分配给其合成核心。每个合成核心可以同时运行8个合成任务。

- 装配矩阵速度核心

这是装配矩阵的 <ItemLink id="ae2:speed_card" />。5个速度核心可使装配矩阵全速运行。
安装超过5个速度核心不会提供额外的速度加成。



## 图形用户界面



右键点击一个已成型且在线（Online）的装配矩阵将打开其图形用户界面。



![GUI](../pic/assembler_matrix.png)



你可以在其中放入或搜索样板，并查看它正在运行多少个合成任务。