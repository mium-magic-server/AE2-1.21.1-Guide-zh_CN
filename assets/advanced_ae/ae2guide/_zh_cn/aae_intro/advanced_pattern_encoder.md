---

navigation:

  parent: aae_intro/aae_intro-index.md

  title: 高级样板编码器

  icon: advanced_ae:adv_pattern_encoder

categories:

  - 高级物品

item_ids:

  - advanced_ae:adv_pattern_encoder

  - advanced_ae:adv_processing_pattern

---



# 高级样板编码器



为了指导ME高级样板供应器将物品发送至何处，需要使用特殊设备来编码这些信息。手持时右键点击即可打开其图形用户界面。



<ItemImage id="advanced_ae:adv_pattern_encoder" scale="4"></ItemImage>



已编码的处理样板可插入左侧槽位，系统会将其解码并将所有原材料以列表形式显示。



![PEGui1](../pic/ape_pattern.png)



每行包含一组代表所有可能传送方向的按钮。若保持选择在"A"按钮，材料将发送至直接连接样板供应器的任意面；若选择特定面，则会强制从该面输入物品。需注意高级样板仅能被<ItemLink id="advanced_ae:adv_pattern_provider" />正确解码，在其他类型的样板供应器中使用时将表现为普通样板。

此外，若单个物品无法从指定面输入，则不会进行定向输入，此时将采用标准样板供应器行为。