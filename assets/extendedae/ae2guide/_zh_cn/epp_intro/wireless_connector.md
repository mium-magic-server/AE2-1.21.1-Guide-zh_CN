---

navigation:

    parent: epp_intro/epp_intro-index.md

    title: ME无线连接器

    icon: extendedae:wireless_connect

categories:

- 扩展设备

item_ids:

- extendedae:wireless_connect

- extendedae:wireless_tool

---



# ME无线连接器



<Row gap="20">

<BlockImage id="extendedae:wireless_connect" scale="6"></BlockImage>

<ItemImage id="extendedae:wireless_tool" scale="6"></BlockImage>

</Row>



ME无线连接器可以像<ItemLink id="ae2:quantum_link" />一样连接两个网络，但传输距离有限且无法跨维度传输。ME无线连接器仅支持一对一连接，如需建立多对多连接，请使用<ItemLink id="extendedae:wireless_hub" />。



## 连接无线连接器



使用ME无线连接工具分别点击两个需要连接的无线连接器，即可建立连接。



潜行+点击可清除ME无线连接工具的当前设置。



当连接成功建立时，ME无线连接器的纹理会发生变化。



未连接的ME无线连接器



<GameScene zoom="5" background="transparent">

  <ImportStructure src="../structure/wireless_connector_off.snbt"></ImportStructure>

</GameScene>



已连接的ME无线连接器



<GameScene zoom="5" background="transparent">

  <ImportStructure src="../structure/wireless_connector_on.snbt"></ImportStructure>

</GameScene>



## 颜色设置



无线连接器可像线缆一样染色，且仅会与相同颜色的线缆/连接器建立连接。



需要使用<ItemLink id="ae2:color_applicator" />为连接器染色。



您可以按照以下方式设置无线连接器：



<GameScene zoom="3" background="transparent" interactive={true}>

  <ImportStructure src="../structure/wireless_connector_setup.snbt"></ImportStructure>

</GameScene>



## 能量消耗



ME无线连接器的能量消耗随距离增加而提升。其能耗-距离曲线并非线性关系，当距离过远时能耗会急剧增加。



可使用<ItemLink id="ae2:energy_card" />节省能耗，每张能量卡可降低10%能量消耗。