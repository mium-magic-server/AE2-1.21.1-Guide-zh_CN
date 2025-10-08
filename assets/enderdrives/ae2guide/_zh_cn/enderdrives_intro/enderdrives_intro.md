---
navigation:
  parent: enderdrives_intro/enderdrives_intro-index.md
  title: 末影物品存储元件
  icon: enderdrives:ender_disk_1k
categories:
  - 末影驱动器
item_ids:
  - enderdrives:ender_disk_1k
  - enderdrives:ender_disk_4k
  - enderdrives:ender_disk_16k
  - enderdrives:ender_disk_64k
  - enderdrives:ender_disk_256k
  - enderdrives:ender_disk_creative
---

# 末影驱动器

末影驱动器是功能强大的驱动器，允许通过频率在ME系统、维度甚至不同玩家之间实现全局同步存储。

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:ender_disk_1k" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:ender_disk_1k" />
  </Column>
</Row>

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:ender_disk_4k" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:ender_disk_4k" />
  </Column>
</Row>

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:ender_disk_16k" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:ender_disk_16k" />
  </Column>
</Row>

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:ender_disk_64k" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:ender_disk_64k" />
  </Column>
</Row>

<Row gap="10">
  <Column>
    <ItemImage id="enderdrives:ender_disk_256k" />
  </Column>
  <Column>
    <ItemLink id="enderdrives:ender_disk_256k" />
  </Column>
</Row>

---

## 工作原理
每个末影驱动器都配置有频率、范围和作用域。
- **频率**：相同频率的驱动器共享同一物品栏。
- **作用域**：决定谁可以访问该驱动器（全局、私人或团队）。
- **模式**：控制物品的流动方式（双向、输入、输出）。

所有具有相同频率和作用域的驱动器都将访问**相同的虚拟物品栏**，无论它们位于何处。

---

## 类型限制
与传统的AE2驱动器不同，末影驱动器的限制仅基于类型。由于物品在后端的存储方式，唯一的硬性限制是类型的数量。你实际上可以为每种类型存储多达 2^63 - 1 或 9,223,372,036,854,775,807 个物品。但要小心，能量消耗会随着该频率下驱动器存储的物品数量而增加！

每个服务器开始出现性能压力的类型数量阈值都不同。你可以使用自动基准测试命令来测试你的服务器。为了获得准确的结果，你需要打开一个终端，并在私人模式下放置一个具有选定频率的驱动器。基准测试将持续进行，直到TPS低于18。这可能需要几分钟时间。

我个人的平均值大约是275,000种类型。275,000/255 ≈ 1078。这意味着我需要用256k末影驱动器和已分类的物品填满107.8个ME驱动器，才会开始看到性能问题。我见过更高和更低的建议最大类型数。此限制在同一世界中所有使用这些驱动器的各方之间共享。

---

## 驱动器模式
每个驱动器可以设置为以下三种**传输模式**之一：

- ![PEGui1](../pic/transport_bidirectional_alt.png) **双向** _(默认)_  
  标准的ME驱动器行为。可以自由放入和取出物品。


- ![PEGui1](../pic/transport_input_alt.png) **仅输入**  
  可以放入物品，但不能取出。适用于缓冲器或同步输入。


- ![PEGui1](../pic/transport_output_alt.png) **仅输出**  
  可以取出物品，但不能放入。非常适合输出缓冲区或只读访问。

---

## 作用域与隐私

每个驱动器还有一个**作用域**，用于控制谁可以访问该物品栏：
-  **全局** _(默认)_  
   公开！任何使用相同频率的玩家都可以访问此共享物品栏。


-  **私人**  
   与你的UUID绑定。只有你可以创建驱动器来访问此频率。你ME系统的任何其他用户仍然可以访问此存储。


-  **团队**  
   与你的FTB团队共享。所有成员都可以创建具有访问相同频率权限的驱动器。