---

导航:

    上级目录: epp_intro/epp_intro-index.md

    标题: ME装罐机

    图标: extendedae:caner

分类:

- 扩展设备

物品ID:

- extendedae:caner

---

# ME装罐机

<BlockImage id="extendedae:caner" scale="8"></BlockImage>

ME装罐机是一台能够"装罐"各种物质的机器，包括流体、通用机械模组的气体、植物魔法的魔力，甚至能量！

第一个槽位用于放置填充物，第二个槽位用于放置待填充容器。

它需要能量才能运行，每次操作消耗80 AE。

![GUI](../pic/caner_gui.png)

默认情况下它只能填充流体，你需要安装相应的附加模组才能让它填充其他物质。

### 支持的附加模组：

- 应用通量
- 应用机械
- 应用植物学附加

## 使用ME装罐机进行自动合成

只有顶部和底部面可以接收能量并连接至网络。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../structure/caner_example.snbt"></ImportStructure>
</GameScene>

一个简单的ME装罐机设置。当从<ItemLink id="ae2:pattern_provider" />接收到材料时，ME装罐机会自动弹出已填充的物品。

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../structure/caner_auto.snbt"></ImportStructure>
</GameScene>

样板必须只包含要填充的物质和待填充的容器。以下是一些示例：

填充水桶：

![P1](../pic/fill_water.png)

赋能能量板（需要安装应用通量）：

![P1](../pic/fill_energy.png)

## 排空操作

ME装罐机也可以在排空模式下从容器中抽取物质。你需要在样板中交换输入和输出位置。