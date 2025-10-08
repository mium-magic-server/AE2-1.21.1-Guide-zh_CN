---
navigation:
  parent: 物品-方块-机器/物品-方块-机器索引.md
  title: 能源元件
  icon: energy_cell
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:energy_cell
- ae2:dense_energy_cell
- ae2:creative_energy_cell
---

# 能源元件

<Row gap="20">
  <BlockImage id="energy_cell" scale="8" p:fullness="4" />

  <BlockImage id="dense_energy_cell" scale="8" p:fullness="4" />

  <BlockImage id="creative_energy_cell" scale="8" />
</Row>

能源元件为网络提供额外的[能量](../ae2-mechanics/energy.md)存储。一定容量的能量缓冲有助于平滑处理大量物品插入或提取时产生的能量需求尖峰，而更大的能量存储容量则能让网络在能量停止生成时（例如使用太阳能板的夜晚）继续运行，或应对[空间存储](../ae2-mechanics/spatial-io.md)带来的巨大瞬时能量消耗。

## 填充条

<Row>
<BlockImage id="energy_cell" scale="4" p:fullness="0" />
<BlockImage id="energy_cell" scale="4" p:fullness="1" />
<BlockImage id="energy_cell" scale="4" p:fullness="2" />
<BlockImage id="energy_cell" scale="4" p:fullness="3" />
<BlockImage id="energy_cell" scale="4" p:fullness="4" />
</Row>

元件侧面的条纹数量对应其当前的能量水平。

*   0 条：电量低于 25%
*   1 条：电量在 25% 至 50% 之间
*   2 条：电量在 50% 至 75% 之间
*   3 条：电量在 75% 至 99% 之间
*   4 条：电量高于 99%

## 元件类型

*   <ItemLink id="energy_cell" /> 可存储 200k AE，单个即可满足大多数使用场景，轻松应对常规网络使用中的能量波动。
*   <ItemLink id="dense_energy_cell" /> 可存储 1.6M AE，适用于希望依靠存储能量运行网络，或处理大型[空间存储](../ae2-mechanics/spatial-io.md)装置带来的巨大瞬时能量消耗的情况。
*   <ItemLink id="creative_energy_cell" /> 是一个用于测试的创造模式物品，提供**无限的能量！！！** 之类的功能。

## 配方

<Row>
  <RecipeFor id="energy_cell" />

  <RecipeFor id="dense_energy_cell" />
</Row>