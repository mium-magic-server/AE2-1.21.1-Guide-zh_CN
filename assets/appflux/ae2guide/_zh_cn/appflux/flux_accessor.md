---

navigation:

  parent: appflux/appflux-index.md

  title: 通量访问点

  icon: appflux:flux_accessor

categories:

- 通量访问点

item_ids:

- appflux:flux_accessor

- appflux:part_flux_accessor

---



# 通量访问点



<Row>

<BlockImage id="appflux:flux_accessor" scale="8"></BlockImage>

<GameScene zoom="8" background="transparent">

  <ImportStructure src="../structure/flux_accessor.snbt"></ImportStructure>

</GameScene>

</Row>



通量访问点可以输入/输出存储在您ME网络中的能量。默认情况下它们没有输入/输出限制，这可以在Appflux配置中更改。



它们有快速模式和普通模式。在快速模式下，它会在每个游戏刻输出能量，如果大量使用可能会导致游戏卡顿。

在普通模式下，它会根据目标的能量存储情况输出能量，这不会引起卡顿问题。



* 注意：这里提到的“能量”是指存储在您[FE存储元件](./flux_cells.md)中的FE能量，而非[能源元件](ae2:items-blocks-machines/energy_cells.md)中的能量。