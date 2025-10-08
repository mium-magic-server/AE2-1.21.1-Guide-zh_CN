---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: 谐振仓
  icon: vibration_chamber
  position: 110
categories:
- 网络基础设施
item_ids:
- ae2:vibration_chamber
---

# 谐振仓

<BlockImage id="vibration_chamber" p:active="true" scale="8" />

虽然为网络提供[能量](../ae2-mechanics/energy.md)的主要预期方法是使用<ItemLink id="energy_acceptor" />，但谐振仓可以直接产生少量到中等数量的AE能量。

默认情况下（无[升级卡](upgrade_cards.md)且使用默认配置）它产生40 AE/t。

当网络的[能量](../ae2-mechanics/energy.md)存储已满时，谐振仓会降低运行速度以节省燃料，但无法完全关闭。

## 设置

*   谐振仓提供访问全局设置的选项，以查看AE或E/FE单位的能量。

## 升级

谐振仓支持以下[升级卡](upgrade_cards.md)：

*   <ItemLink id="energy_card" /> 将谐振仓的效率提高+50%，最高可达+150%，即基础效率的250%。
*   <ItemLink id="speed_card" /> 将谐振仓的燃烧速率提高+50%，最高可达+150%，即基础功率输出的250%。

## 配置

谐振仓的属性可以在.minecraft目录下的config文件夹内的ae2文件夹中的common.json文件中进行编辑。

*   baseEnergyPerFuelTick 设置谐振仓基础的、未升级的效率。
*   minEnergyPerGameTick 设置最低可能的能量生成（即使网络不需要能量，谐振仓也会始终缓慢消耗一些燃料）。
*   maxEnergyPerGameTick 设置未升级的谐振仓的最大输出（和速度）。

## 配方

<RecipeFor id="vibration_chamber" />