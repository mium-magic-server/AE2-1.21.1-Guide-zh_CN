---
navigation:
  parent: enderdrives_intro/enderdrives_intro-index.md
  title: 磁带磁盘物品存储单元
  icon: enderdrives:tape_disk
categories:
  - 磁带驱动器
item_ids:
  - enderdrives:tape_disk
---

# 磁带磁盘驱动器

磁带驱动器是功能强大的 AE2 兼容存储单元，专为处理**NBT 密集型物品**而设计，例如工具、盔甲、附魔装备或任何带有独特标签、通常会在传统 ME 驱动器中占用类型空间的物品。

与典型的 AE2 驱动器不同，磁带磁盘的字节使用量会根据存储物品的实际 **NBT 大小**动态调整——让您对系统拥有精细的控制。磁带驱动器**不会**告知 AE2 它优先存储任何与其过滤器匹配的物品，请使用 ME 驱动器优先级。

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:tape_disk" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:tape_disk" />
  </Column>
</Row>

---

## 工作原理

每个磁带磁盘仅允许存储带有非标准 NBT 的、盔甲、工具或不可堆叠的物品。

---

## 字节与类型限制

磁带磁盘同时强制执行**类型限制**和**字节使用限制**：

- **类型限制** – 可存储的唯一物品类型的最大数量（例如，附魔书、自定义盔甲）。
- **字节限制** – 基于每个物品的 **NBT 数据大小**。具有大量标签的物品（如神化装备）由于 NBT 数量多，会占用更多空间。

磁带磁盘专为**NBT 密集型物品**设计，使其成为存储装备或一次性物品的理想选择，而不会污染传统驱动器的空间。

---

## 何时使用磁带磁盘

在以下情况下，请使用磁带磁盘代替传统驱动器：

- 您正在存储**不可堆叠的物品**，如盔甲、工具或装备。
- 您需要为**NBT 密集型的模组物品**提供空间。
- 您希望将特殊物品与普通 ME 驱动器隔离开。

磁带驱动器在普通驱动器表现不佳的领域表现出色——避免占用您大型驱动器上的类型限制空间。

---

## I/O 端口传输

磁带磁盘在使用 I/O 端口进行传入或传出传输时会自动限制自身速度。这是因为可能需要处理 NBT 密集型物品，因此它不会一次性全部传输而导致游戏卡顿。

---

## 可以存储什么？

磁带磁盘专用于**NBT 密集型**、**不可堆叠**或**自定义**物品——而非通用的大宗存储。

---

### 可接受的物品

| 物品                                | 示例                                  |
|-------------------------------------|------------------------------------------|
| <ItemImage id="minecraft:diamond_chestplate" /> | 带有附魔的**钻石胸甲** |
| <ItemImage id="minecraft:enchanted_book" />     | 带有附魔的**附魔书**   |
| <ItemImage id="minecraft:splash_potion" />      | 带有效果的**药水**                 |
| <ItemImage id="minecraft:netherite_pickaxe" />  | 带有耐久度的**工具**                |

---

### 不可接受的物品

| 物品                              | 原因                         |
|-----------------------------------|--------------------------------|
| <ItemImage id="minecraft:cobblestone" /> | 无 NBT，可堆叠              |
| <ItemImage id="minecraft:wheat" />       | 无 NBT，可堆叠  |
| <ItemImage id="minecraft:oak_log" />     | 无 NBT，可堆叠             |
| <ItemImage id="minecraft:apple" />       | 无 NBT，可堆叠    |
| <ItemImage id="minecraft:iron_ingot" />  | 无 NBT，可堆叠    |

---