---

navigation:

  parent: aae_intro/aae_intro-index.md

  title: 量子计算机

  icon: advanced_ae:quantum_core

categories:

  - 高级设备

item_ids:

  - advanced_ae:quantum_unit

  - advanced_ae:quantum_core

  - advanced_ae:quantum_structure

  - advanced_ae:quantum_accelerator

  - advanced_ae:quantum_multi_threader

  - advanced_ae:quantum_storage_128

  - advanced_ae:quantum_storage_256

  - advanced_ae:data_entangler

---



# 量子计算机



量子计算机是一种特殊的合成计算机。只要拥有足够的合成存储空间，它就能够运行无限数量的合成请求。



<GameScene zoom="2" background="transparent">

  <ImportStructure src="../structure/quantum_computer_multiblock.snbt"></ImportStructure>

</GameScene>



## 量子核心



<BlockImage id="advanced_ae:quantum_core" p:powered="true" p:formed="true" scale="4"></BlockImage>



量子核心是量子计算机的核心。它自身拥有 256M 的合成存储空间和 8 个并行处理线程。它是唯一能够单独构成一个完整量子计算机并提供其所有益处的方块。然而，如果用于构建多方块结构，则可以创建出更强大的计算机。当作为独立计算机使用时，必须通过其上方或下方（连接器所在面）提供能量。



## 量子存储



<Row gap="20">

<BlockImage id="advanced_ae:quantum_storage_128" scale="4"></BlockImage>

<BlockImage id="advanced_ae:quantum_storage_256" scale="4"></BlockImage>

</Row>



这些方块用于扩展量子核心的合成存储空间。它们能有效增加量子计算机能够同时运行的任务数量。共有两种变体，容量分别为 128M 和 256M。



## 量子数据纠缠器



<BlockImage id="advanced_ae:data_entangler" scale="4"></BlockImage>



数据纠缠器是一种特殊的方块，它会影响多方块结构中所有的存储方块。它能使存储方块将数据存储在多个维度中，从而将其存储容量乘以 4。每个量子计算机多方块结构中只能放置一个此类方块。



## 量子加速器



<BlockImage id="advanced_ae:quantum_accelerator" scale="4"></BlockImage>



量子加速器为量子计算机多方块结构增加 8 个并行处理单元。需要注意的是，量子计算机运行的所有合成样板都能够共享所有的并行处理单元，因此大量投资于这些方块可能是个好主意。



## 量子多线程处理器



<BlockImage id="advanced_ae:quantum_multi_threader" scale="4"></BlockImage>



与数据纠缠器类似，多线程处理器能使加速器在独立的维度中运行额外的线程，将其并行处理能力乘以 4。每个量子计算机多方块结构中只能放置一个此类方块。



## 量子结构



<Row gap="20">

<BlockImage id="advanced_ae:quantum_structure" scale="4"></BlockImage>

<BlockImage id="advanced_ae:quantum_structure" p:formed="true" scale="4"></BlockImage>

<BlockImage id="advanced_ae:quantum_structure" p:formed="true" p:powered="true" scale="4"></BlockImage>

</Row>



这些方块构成了量子计算机的框架。它们用作量子计算机的结构方块，并将所有部件连接在一起。



## 多方块结构



要创建一个多方块量子计算机，必须遵循以下规则：

- 最大尺寸为 7x7x7（外部尺寸）；

- 多方块结构内部不能存在空位。可以使用 <ItemLink id="advanced_ae:quantum_unit" /> 填充，但不会带来额外增益；

- 必须有且仅有一个 <ItemLink id="advanced_ae:quantum_core" />；

- 最多一个 <ItemLink id="advanced_ae:data_entangler" />；

- 最多一个 <ItemLink id="advanced_ae:quantum_multi_threader" />；

- 最外层的所有方块必须是 <ItemLink id="advanced_ae:quantum_structure" />；

- 内部不能有任何 <ItemLink id="advanced_ae:quantum_structure" /> 方块。



## 服务端配置



可以通过服务端配置调整多个数值，例如：

- 多方块结构最大尺寸；

- 每个量子加速器提供的并行处理单元数量；

- 量子多线程处理器的最大数量；

- 多线程处理器的线程倍增系数；

- 数据纠缠器的最大数量；

- 数据纠缠器的存储倍增系数；



您可以通过物品的工具提示来查看当前实例的限制。