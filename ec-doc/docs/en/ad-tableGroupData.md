<h5 id="start"></h5>

### Table Grouping and Data Statistics

<aside>
💡 This guide will show you how to easily add group headers, group footers, and perform table classification statistics based on specific fields in our designer, making your table data presentation clearer and more professional.
</aside>
<br>

#### 1. Open the Designer

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### 2. Set Grouping Fields

> Select the table element you need to group, open its properties panel, and switch to the "Advanced" tab. <br/>

> In the "Group Field Function" input box, click to open the function window. You can use [AI to generate the group field function](#ai-group1) or write it yourself (refer to the <a href="/#/zh-cn/ad-highlevel.md#self-group1" target="_blank">group field function</a> description in advanced function applications).

![Table Grouping and Data Statistics_Set Grouping Fields](../_images/zh-cn/表格分组以及数据统计_设定分组字段.gif)

<div id="ai-group1"></div>

#### 3. Use AI to Generate Group Field Function
> 3.1 In the AI assistant window on the left, enter your grouping requirements, such as: "Group the table by month field".

> 3.2 AI will generate the corresponding code block based on your requirements.

> 3.3 Copy the AI-generated code block to the function code area on the right side of the "Group Field Function" and click "OK" to save the settings.

![Table Grouping and Data Statistics_Use AI to Generate Group Code](../_images/zh-cn/表格分组以及数据统计_利用AI生成分组代码.gif)

<div id="self-group1"></div>

#### 4. Customize Group Header
*To make the grouping information clearer, you can add a group header for each group. <br/>
The group header is usually used to display the title of the current group.* <br/>
> In the "Group Header Format Function" input box, click to open the function window. You can use [AI to generate the group header function](#ai-group2) or write it yourself (refer to the <a href="/#/zh-cn/ad-highlevel.md#self-group2" target="_blank">group header function</a> description in advanced function applications).

![Table Grouping and Data Statistics_Customize Group Header](../_images/zh-cn/表格分组以及数据统计_自定义分组头.gif)

<div id="ai-group2"></div>

#### 5. Use AI to Generate Group Header Function
> 5.1 In the AI chat window on the left, clearly describe your group header requirements, such as: <br/>

```
The table is now grouped by [Month], generate the group header.
Group header content: {group field value}+" month data is as follows:".
HTML style: No line break, one line occupies all columns, center aligned, blue font.
```

> 5.2 AI will generate the corresponding code block based on your requirements. <br/>

> 5.3 Copy the AI-generated code block to the function code area on the right side of the "Group Header Format Function" and click "OK" to save the settings. <br/>

![Table Grouping and Data Statistics_Use AI to Generate Group Header Code](../_images/zh-cn/表格分组以及数据统计_利用AI生成分组头代码.gif)

#### 6. Customize Group Footer
*To display statistics for the group information, you need to add a group footer for each group. <br/>
The group footer is usually used to display the statistical information of the group data, such as totals, averages, etc.* <br/>

> In the "Group Footer Format Function" input box, click to open the function window. You can use [AI to generate the group footer function](#ai-group3) or write it yourself (refer to the <a href="/#/zh-cn/ad-highlevel.md#self-group3" target="_blank">group footer function</a> description in advanced function applications).

![Table Grouping and Data Statistics_Customize Group Footer](../_images/zh-cn/表格分组以及数据统计_自定义分组脚.gif)

<div id="ai-group3"></div>

#### 7. Use AI to Generate Group Footer Function
> 7.1 In the AI chat window on the left, clearly describe your group footer requirements, such as: <br/>

```
The table is now grouped by [Month], generate the group footer.
Group footer content, return 4 td tags:
1. "Total:"; [HTML style: red font, center aligned, occupies 2 columns]
2. Quantity count: {count value of records in the group}, numerical type quantity value accumulation; [HTML style: left aligned, occupies 1 column]
3. Unit price total: {accumulated value of unit price in the group records}, numerical type unit price value accumulation; [HTML style: left aligned, occupies 1 column]
4. Amount total: {accumulated value of amount in the group records}, numerical type amount value accumulation; [HTML style: left aligned, occupies 1 column]
```

> 7.2 AI will generate the corresponding code block based on your requirements. <br/>

> 7.3 Copy the AI-generated code block to the function code area on the right side of the "Group Footer Format Function" and click "OK" to save the settings. <br/>

![Table Grouping and Data Statistics_Use AI to Generate Group Footer Code](../_images/zh-cn/表格分组以及数据统计_利用AI生成分组脚代码.gif)

#### 8. Preview Print Effect
> Click the preview icon to view the grouping and statistics effects of the added table. Make necessary adjustments and optimizations based on the preview effect.

![Table Grouping and Data Statistics_Preview Print Effect](../_images/zh-cn/表格分组以及数据统计_预览打印效果.gif)

#### 9. Save Template
> When you are satisfied with the grouping and statistical effects of the table, name the template and click the save icon.

![Table Grouping and Data Statistics_Save Template](../_images/zh-cn/表格分组以及数据统计_保存模板.gif)