---
navigation:
  parent: example-setups/example-setups-index.md
  title: 一个“主网络”示例
  icon: controller
---

# 一个“主网络”示例

许多其他配置方案都提到了“主网络”。你可能也会好奇所有这些[设备](../ae2-mechanics/devices.md)是如何组合成一个功能系统的。这里有一个示例：

<GameScene zoom="2.5" interactive={true}>
  <ImportStructure src="../assets/assemblies/small_base_network.snbt" />

    <BoxAnnotation color="#33dd33" min="5 1 10" max="9 7 14" thickness="0.05">
        一大簇样板供应器和装配器为合成、切石和锻造样板提供了大量空间。
        棋盘格布局使得供应器能够在保持紧凑的同时并行利用多个装配器。
        8个一组的配置可以防止频道路由出错。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="13 10 12" max="14 11 14" thickness="0.05">
        你实际上并不需要那么大的控制器，你在别人基地里看到的那些巨大的环状和立方体设计主要是为了看起来酷炫。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="13 12 13" max="14 13 14" thickness="0.05">
        每个好的网络都有一个能量电池，以便每个游戏刻能输入更多能量并平滑功率波动。
    </BoxAnnotation>
    
    <BoxAnnotation color="#33dd33" min="2 1 10" max="4 4 13" thickness="0.05">
        你可能会想使用其他模组的能源，比如反应堆、太阳能板或发电机等等。
        谐振仓也还行，但AE2的设计初衷是在整合包中使用，并利用你基地的主发电机。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="15 1 9" max="16 3 14" thickness="0.05">
        伪装块可用于将东西隐藏在墙后。
    </BoxAnnotation>
    <BoxAnnotation color="#33dd33" min="15 3 12" max="16 10 14" thickness="0.05">
        伪装块可用于将东西隐藏在墙后。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="13 9 7" max="14 10 9" thickness="0.05">
        对于常规存储，你并不需要那么多驱动器阵列和存储元件，2-4个驱动器（装有4k或16k存储元件）几乎总是足够的。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="13 9 10" max="14 11 11" thickness="0.05">
        对于大宗存储，你需要使用大容量存储元件，并设置为特定物品，放入单独的驱动器中并设置更高的优先级。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="10 9 13" max="11.7 13 14" thickness="0.05">
        基于接口的自动补货。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="6 10 12" max="9 12 15" thickness="0.05">
        充能自动化配置的逻辑扩展，扩展到多个充能器。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="2 10 12" max="5 11 15" thickness="0.05">
        另一种自动化处理器的办法，因为压印器在1.20版本可以自动弹出产物了。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="3 10 10" max="4 12 11" thickness="0.05">
        另一种自动化处理器的办法，因为压印器在1.20版本可以自动弹出产物了。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="7.2 9.2 8.2" max="7.8 10 8.8" thickness="0.05">
        无线访问点位于中央，因为其作用范围是球形的。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="14 1 2" max="16 5 7" thickness="0.05">
        通常你会准备1-2个大型合成CPU来处理大任务，以及几个小型的来处理大型CPU繁忙时的次要任务。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="5 3 6" max="6 4 7" thickness="0.05">
        有时子网络如果设备超过8个（例如需要分发到超过8个地方），可能需要自己的控制器。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="7.3 1 3.3" max="9.7 4 6" thickness="0.05">
        赛特斯石英农场。
    </BoxAnnotation>

    <BoxAnnotation color="#33dd33" min="10.3 1 2.3" max="12.7 3.7 5" thickness="0.05">
        水中投掷自动化。
    </BoxAnnotation>

  <IsometricCamera yaw="135" pitch="15" />
</GameScene>