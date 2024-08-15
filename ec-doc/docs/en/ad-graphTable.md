<h5 id="start"></h5>

### Reading Table Data Sources for Charts

<aside>
💡 This guide will detail how to read data from table data sources and use that data to render charts, ensuring the accuracy and professionalism of the charts.
</aside>
<br>

#### 1. Open the Designer

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### 2. Open Chart Render Function

> Select the chart element you need to render (using a bar chart as an example), open its properties panel, and switch to the "Advanced" tab. <br/>

> In the "Render Function" input box, click to open the function window. You can use [AI to generate the chart render function](#ai-charts) or write it yourself (refer to the <a href="/#/zh-cn/ad-highlevel.md#self-charts" target="_blank">Chart Render Function</a> description in advanced function applications).

![Reading Table Data Sources for Charts_Open Chart Render Function](../_images/zh-cn/图表读取表格数据源_打开图表渲染函数.gif)
<br/>
<br/>
<br/>

<div id="ai-charts"></div>

#### 3. Use AI to Generate Chart Render Function
> 3.1 In the AI assistant window on the left, describe your chart rendering requirements in detail. For example: <br/>
```
1. Data source: Generate a bar chart from the histogramTable in templateData, using templateData. syntax.
2. Data layout: Non-stacked.
3. X-axis configuration: If the title field (options.customTitle) is not empty, use it as the title, separated by commas. If the title field is empty, use the table's title.
4. Y-axis configuration: Field values.
5. Style requirements:
- Color scheme: Bar colors follow the table's record classification, ranging from light blue to dark blue.
- Font: Arial font, 12pt size, color deep gray (#444444).
- Background and grid lines: Background is light beige (#F8F8F8), Y-axis and X-axis grid lines are fine dotted lines, color light gray (#DDDDDD).
```

> 3.2 AI will automatically generate the corresponding code block based on your description.

> 3.3 Copy the AI-generated code block to the function code area on the right side of the "Render Function" and click "OK" to save the settings.

![Reading Table Data Sources for Charts_Use AI to Generate Chart Rendering Code](../_images/zh-cn/图表读取表格数据源_利用AI生成图表渲染代码.gif)
<br/>
<br/>
<br/>

#### 4. Preview Print Effect
> Click the preview icon to view the chart's rendering effect. Make necessary adjustments and optimizations based on the preview effect.

![Reading Table Data Sources for Charts_Preview Print Effect](../_images/zh-cn/图表读取表格数据源_预览打印效果.gif)

#### 5. Save Template
> When you are satisfied with the chart's rendering effect, name the template and click the save icon.

![Reading Table Data Sources for Charts_Save Template](../_images/zh-cn/图表读取表格数据源_保存模板.gif)