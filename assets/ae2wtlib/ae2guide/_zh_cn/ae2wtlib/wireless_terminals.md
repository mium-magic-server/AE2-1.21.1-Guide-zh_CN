---
navigation:
  parent: ae2wtlib/ae2wtlib-index.md
  title: AE2WTLib 无线终端
  icon: ae2wtlib:wireless_universal_terminal
  position: 10
categories:
- ae2wtlib
item_ids:
  - ae2wtlib:wireless_pattern_encoding_terminal
  - ae2wtlib:wireless_pattern_access_terminal
---

# 无线终端

<ItemGrid>
  <ItemIcon id="ae2wtlib:wireless_universal_terminal" />
  <ItemIcon id="ae2:wireless_crafting_terminal" />
  <ItemIcon id="ae2wtlib:wireless_pattern_encoding_terminal" />
  <ItemIcon id="ae2wtlib:wireless_pattern_access_terminal" />
</ItemGrid>

除了 <ItemLink id="ae2:energy_card" />（能量卡），所有 AE2WTLib 无线终端都可以用 <ItemLink id="ae2wtlib:quantum_bridge_card" />（量子桥卡）升级，
并组合成一个 <ItemLink id="ae2wtlib:wireless_universal_terminal" />（无线通用终端）。

与 AE2 的 <ItemLink id="ae2:wireless_terminal" />（无线终端）类似，它可以通过按键绑定访问，并可以放入饰品槽
（如果安装了任何实现了 Curio API 的模组）。

无线终端也可以像普通的 <ItemLink id="ae2:wireless_terminal" />（无线终端）一样，使用 <ItemLink id="ae2:wireless_access_point" />（无线访问点）进行链接。

## 无线通用终端

<ItemImage id="ae2wtlib:wireless_universal_terminal" scale="3" />

<ItemLink id="ae2wtlib:wireless_universal_terminal" />（无线通用终端）是将多个无线终端组合成一个物品。

## 无线合成终端

<ItemImage id="ae2:wireless_crafting_terminal" scale="3" />

<ItemLink id="ae2:wireless_crafting_terminal" />（无线合成终端）是合成终端的无线版本。
与原版 AE2 相比，它拥有[一些额外的功能](wireless_crafting_terminal.md)。

## 无线样板终端

<ItemImage id="ae2wtlib:wireless_pattern_encoding_terminal" scale="3" />

这是 <ItemLink id="ae2:pattern_encoding_terminal" />（样板编码终端）的无线版本。

<RecipeFor id="ae2wtlib:wireless_pattern_encoding_terminal" />

## 无线样板管理终端

<ItemImage id="ae2wtlib:wireless_pattern_access_terminal" scale="3" />

这是 <ItemLink id="ae2:pattern_access_terminal" />（样板管理终端）的无线版本。

<RecipeFor id="ae2wtlib:wireless_pattern_access_terminal" />

## 附加终端

来自其他附加模组的大多数无线终端也可以与 <ItemLink id="ae2wtlib:wireless_universal_terminal" />（无线通用终端）一起使用。

## 无法在通用终端中使用的终端

<ItemLink id="ae2:wireless_terminal" />（无线终端）不能在 <ItemLink id="ae2wtlib:wireless_universal_terminal" />（无线通用终端）中使用，
因为它不会提供比 <ItemLink id="ae2:wireless_crafting_terminal" />（无线合成终端）更多的优势。
它也不能使用 <ItemLink id="ae2wtlib:quantum_bridge_card" />（量子桥卡）。