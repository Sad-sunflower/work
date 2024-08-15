<h5 id="start"></h5>

### 高级函数功能

<aside>
💡 高级函数功能可助您更灵活地处理文本、样式和表格元素，以满足各种复杂的打印需求。
</aside>
<br>

### **1. 文本/长文本：格式化函数{formatter}**

<mark>**注意**</mark>：只能访问templateDate的数据，没法统计通过script动态计算的项目。

#### 1.1 为什么使用它？
通过formatter函数，能够便捷地将数据转换为指定的格式，例如，格式化日期、添加千分位分隔符。<br/>
同时，当您需要计算或处理数据时，formatter函数会非常有用。例如，计算表格中某一列的总和。<br/>

#### 1.2 参数介绍
`title`：元素的标题数据。<br/>
`value`：具体元素值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`templateData`：所有打印数据。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>

#### 1.3 示例逻辑
> 计算templateData中表格detaillist的[金 額]列总值。<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)
```
function formatter(title,value,options,templateData,target){
  let amount = 0;
  for (let index = 0; index < templateData?.detaillist?.length; index++) {
      amount += 1*templateData.detaillist[index].amount;
  }
  return amount;
}
```

#### 1.4 示例效果展示
![高级函数功能_格式化函数](../_images/zh-cn/高级函数功能_格式化函数.gif)
<br>
<br>
<br>

### **2. 文本/长文本：样式函数{styler}**

#### 2.1 为什么使用它？
当您想对文本或长文本元素应用特定的样式时，可以使用样式函数。例如，您可能想将某个文本元素设置特定的字体、颜色或对齐方式。

#### 2.2 参数介绍
`value`：具体元素值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>
`templateData`：所有打印数据。<br/>

#### 2.3 示例逻辑
> 纵向书写模式，从左到右。
```
function styler(value, options, target, templateData) {
    return {
        writingMode: 'vertical-lr', 
    };
}
```

#### 2.4 示例效果展示
![高级函数功能_样式函数](../_images/zh-cn/高级函数功能_样式函数.gif)
<br>
<br>
<br>

### **3. 表格 列：底部聚合格式化函数{tableSummaryFormatter}**

#### 3.1 为什么使用它？
当您想在表格的底部显示某列的总和、平均值或其他统计信息时，可以使用底部聚合格式化函数。这对于提供数据的概览和统计非常有用。

#### 3.2 参数介绍
`column`：表示当前列的相关属性对象。通过它可以访问该列的名称、值等信息。<br/>
`fieldPageData`：包含当前列所有行数据的数组。<br/>
`tableData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`options`：包含当前表格的所有属性的对象，用于逻辑判断和获取特定信息。<br/>

#### 3.3 示例逻辑
> 显示"数量合計："+{集记值}。集记值：累加列中的数值，实现千分位添加逗号分隔，不显示小数。【html样式：居中，浅蓝色背景，红色字体。】<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)

```
function tableSummaryFormatter(column, fieldPageData, tableData, options) {
    let sum = fieldPageData.reduce((acc, cur) => acc + parseInt(cur), 0); 
    let formattedSum = sum.toLocaleString(); 
    return `<td style="text-align:center;background-color:lightblue;color:red;">数量合計：${formattedSum}</td>`; 
}
```

#### 3.4 示例效果展示
![高级函数功能_底部聚合格式化函数](../_images/zh-cn/高级函数功能_底部聚合格式化函数.gif)
<br>
<br>
<br>

### **4. 表格 列：单元格渲染函数{renderFormatter}**

#### 4.1 为什么使用它？
renderFormatter函数允许您根据数据的特性进行定制化渲染，比如颜色标记、格式化日期、货币值或百分比。例如，当库存管理员需要快速识别库存不足的商品时，通过renderFormatter函数，可以高亮显示这些商品的库存量，使其一目了然。

#### 4.2 参数介绍
`value`：单元格的打印数据值。<br/>
`row`：表示当前行数据的对象。通过row.列名来查询当前行某列的值。<br/>
`colIndex`：表示当前列在表格中的索引位置，从0开始计数。<br/>
`options`：包含当前表格的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`rowIndex`：表示当前行在表格中的索引位置，从0开始计数。<br/>

#### 4.3 示例逻辑
> [商品名 ／ 品名]列，列文字后添加：行号。【html样式：红色字体】<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)。
```
function renderFormatter(value, row, colIndex, options, rowIndex) {
    return `<td style="color:red;">${value} 行号：${rowIndex + 1}</td>`;
}
```

#### 4.4 示例效果展示
![高级函数功能_单元格渲染函数](../_images/zh-cn/高级函数功能_单元格渲染函数.gif)
<br>
<br>
<br>

### **5. 表格 列：单元格格式化函数{formatter2}**

#### 5.1 为什么使用它？
当您需要在表格某列中显示某些经过计算或处理的数据时，formatter2函数会非常有用。例如，您有一个员工绩效信息，表格中包含了员工的姓名、销售额、销售目标以及达成率（销售额与销售目标的比例）。您可以使用formatter2函数来计算达成率，省去了用户手动计算的步骤。

#### 5.2 参数介绍
`value`：单元格的打印数据值。<br/>
`row`：表示当前行数据的对象。通过row.列名来查询当前行某列的值。<br/>
`colIndex`：表示当前列在表格中的索引位置，从0开始计数。<br/>
`options`：包含当前表格的所有属性的对象，用于逻辑判断和获取特定信息。<br/>

#### 5.3 示例逻辑
> [金 額]大于60000的数据，[数 量]列中的值加上6。<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)

```
function formatter2(value, row, colIndex, options) {
    if(row.amount > 60000) {
        return Number(row.quantity) + 6;
    }
    return value;
}
```

#### 5.4 示例效果展示
![高级函数功能_单元格格式化函数](../_images/zh-cn/高级函数功能_单元格格式化函数.gif)
<br>
<br>
<br>

### **6. 表格 列：单元格样式函数{styler2}**

#### 6.1 为什么使用它？
通过styler2函数，您可以动态地为单元格应用不同的样式（如颜色、字体、边框等）。

#### 6.2 参数介绍
`value`：单元格的打印数据值。<br/>
`row`：表示当前行数据的对象。通过row.列名来查询当前行某列的值。<br/>
`colIndex`：表示当前列在表格中的索引位置，从0开始计数。<br/>
`options`：包含当前表格的所有属性的对象，用于逻辑判断和获取特定信息。<br/>

#### 6.3 示例逻辑
> [数 量]文本类型数据，等于"200"的数据，字体颜色设为红色，左右对齐方式为居中。<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)

```
function styler2(value, row, colIndex, options) {
  if (row.quantity === '200') {
    return {color: 'red', textAlign: 'center'};
  }
}
```

#### 6.4 示例效果展示
![高级函数功能_单元格样式函数](../_images/zh-cn/高级函数功能_单元格样式函数.gif)
<br>
<br>
<br>

### **7. 表格 列：表格头样式函数{stylerHeader}**

#### 7.1 为什么使用它？
通过stylerHeader函数，您可以动态地为表头应用不同的样式（如颜色、字体、边框等）。

#### 7.2 参数介绍
`options`：包含当前表格的所有属性的对象，用于逻辑判断和获取特定信息。<br/>

#### 7.3 示例逻辑
> 当前列(商品名 ／ 品名)的表头字体颜色设为红色，左右对齐方式为居右，字体斜体。</br>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)

```
function stylerHeader(options) {
    return {color: 'red', textAlign: 'right', fontStyle: 'italic'};
}
```

#### 7.4 示例效果展示
![高级函数功能_表格头样式函数](../_images/zh-cn/高级函数功能_表格头样式函数.gif)
<br>
<br>
<br>

### **8. 表格：样式函数{styler}**

#### 8.1 为什么使用它？
通过styler函数，您可以动态地为表格整体应用不同的样式（如颜色、字体、边框等）。

#### 8.2 参数介绍
`value`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`target`：一个包含表格元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>
`templateData`：所有打印数据。<br/>

#### 8.3 示例逻辑
> 设置当前表格的边框 2px solid yellow。

```
function styler(value, options, target, templateData){
  return {"border":"2px solid yellow"};
}
```

#### 8.4 示例效果展示
![高级函数功能_表格_样式函数](../_images/zh-cn/高级函数功能_表格_样式函数.gif)
<br>
<br>
<br>

### **9. 表格：行样式函数{rowStyler}**

#### 9.1 为什么使用它？
通过rowStyler函数，您可以动态地为表格行应用不同的样式（如颜色、字体、边框等）。

#### 9.2 参数介绍
`value`：表示当前行数据的对象。通过value.列名来查询当前行某列的值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`rowIndex`：表示当前行在表格中的索引位置，从0开始计数。<br/>

#### 9.3 示例逻辑
> 设置奇数行背景浅蓝色，字体深蓝色。

```
function rowStyler(value, options, rowIndex) {
    return rowIndex % 2 === 0 ? { 'background-color': '#add8e6', 'color': '#00008b' } : {};
}
```

#### 9.4 示例效果展示
![高级函数功能_行样式函数](../_images/zh-cn/高级函数功能_行样式函数.gif)
<br>
<br>
<br>

### **10. 表格：表格脚函数{footerFormatter}**

#### 10.1 为什么使用它？
通过footerFormatter函数，可以自定义表格脚的内容，使其能够在表格的底部动态地反映数据的汇总信息或统计数据。

#### 10.2 参数介绍
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`rowsData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`data`：表格每页的数据。<br/>
`templateData`：所有打印数据。<br/>

#### 10.3 示例逻辑
> 生成表格脚<br/>
> 表格脚内容，返回2个td标签：<br/>
  > 1. "数量集记："；【html样式：左右对齐方式为居中，占2列】<br/>
  > 2. {数量集记值}，数值类型数量值累加，不统计不是数字的值和空行。【html样式：左右对齐方式为居左，占3列】<br/>

> 表格字段信息：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)<br/>

```
function footerFormatter(options, rowsData, data, templateData) {
  let totalQuantity = 0;
  rowsData.forEach(row => {
    const quantity = Number(row.quantity);
    if (!isNaN(quantity)) {
      totalQuantity += quantity;
    }
  });
  return `<tr><td colspan="2" style="text-align:center;border:1px solid black;">数量集记：</td><td colspan="3" style="text-align:left;border:1px solid black;">${totalQuantity}</td></tr>`;
}
```

#### 10.4 示例效果展示
![高级函数功能_表格脚函数](../_images/zh-cn/高级函数功能_表格脚函数.gif)
<br>
<br>
<br>

### **11. 表格：行/列合并函数{rowsColumnsMerge}**

#### 11.1 为什么使用它？
当表格中存在大量具有相同值（如商品名）的行时，通过rowsColumnsMerge函数，您可以合并这些行或列，优化表格的展示效果。

#### 11.2 参数介绍
`data`：表示当前行数据的对象。通过data.列名来查询当前行某列的值。<br/>
`column`：表示当前列的相关属性对象。通过它可以访问该列的名称、值等信息。<br/>
`colIndex`：表示当前列在表格中的索引位置，从0开始计数。<br/>
`rowIndex`：表示当前行在表格中的索引位置，从0开始计数。<br/>
`tableData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`templateData`：所有打印数据。<br/>

#### 11.3 示例逻辑
> [商品名 ／ 品名]列中内容一致的数据，合并行。<br/>

> 表格字段：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)

```
function rowsColumnsMerge(data, column, colIndex, rowIndex, tableData, templateData) {
    if (column.field === 'productName') { 
        if (rowIndex === 0 || data.productName !== tableData[rowIndex - 1].productName) {
            let mergeCount = 1;
            for (let i = rowIndex + 1; i < tableData.length && tableData[i].productName === data.productName; i++) {
                mergeCount++;
            }
            return [mergeCount, 1]; 
        } else {
            return [0, 1]; 
        }
    }
    return [1, 1]; 
}
```

#### 11.4 示例效果展示
![高级函数功能_行/列合并函数](../_images/zh-cn/高级函数功能_行、列合并函数.gif)
<br>
<br>
<br>

<h4 id="self-group1"></h4>

### **12. 表格：分组字段函数{groupFieldsFormatter}**

<mark>**注意**</mark>：需要配合`分组头格式化函数`和`分组脚格式化函数`使用。

#### 12.1 为什么使用它？
通过groupFieldsFormatter函数，您可以对表格中的数据按照指定的字段进行分组。更清晰地看到不同组之间的数据差异和趋势，从而更好地理解数据背后的含义。

#### 12.2 参数介绍
`type`：当前表格元素的基本属性。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`data`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>

#### 12.3 示例逻辑
> 按照[月]分组<br/>

> 表格字段：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)<br/>

```
function groupFieldsFormatter(type, options, data) {
    return ['month'];
}
```

#### 12.4 示例效果展示
![高级函数功能_分组字段函数](../_images/zh-cn/高级函数功能_分组字段函数.gif)
<br>
<br>
<br>

<h4 id="self-group2"></h4>

### **13. 表格：分组头格式化函数{groupFormatter}**

<mark>**注意**</mark>：需要配合`分组字段函数`使用。

#### 13.1 为什么使用它？
通过groupFormatter函数，您可以自定义表格中分组头的显示内容和样式，以满足特定的业务需求或视觉设计要求。

#### 13.2 参数介绍
`colTotal`：表格的总列数。<br/>
`tableData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`templateData`：所有打印数据。<br/>
`groupData`：当前分组的分组字段名和分组数据的对象。groupData.rows来查询分组数据。groupData.XXX可以获取当前分组字段信息。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`numberFormat`：用于自定义格式化数据的函数。<br/>
`columnsFormats`：数组类型，数组内对象保存三个属性如下：
- `columnsFormats[index].colnumIndex`: 表示当前列在表格中的索引位置，从0开始计数;<br/>
- `columnsFormats[index].format`: 列的数据格式，例如'#,##0';<br/>
- `columnsFormats[index].dataType`: 列的数据类型;<br/>

<div id="groupFormatter"></div>

#### 13.3 示例逻辑
> 表格现在按照[月]分组，生成分组头。<br/>
> 分组头内容：{分组字段值}+"月度数据如下："。【html样式：不换行，一行占所有列，居中对齐，蓝色字体。】<br/>

> 表格字段：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)<br/>

```
function groupFormatter(colTotal, tableData, templateData, groupData, options, numberFormat, columnsFormats) {
    return `<td class="hi-td-center" style="color: blue; text-align: center;" colspan="${colTotal}">${groupData.month}月度数据如下：</td>`;
}
```

#### 13.4 示例效果展示
![高级函数功能_分组头格式化函数](../_images/zh-cn/高级函数功能_分组头格式化函数.gif)
<br>
<br>
<br>

<h4 id="self-group3"></h4>

### **14. 表格：分组脚格式化函数{groupFooterFormatter}**

<mark>**注意**</mark>：需要配合`分组字段函数`使用。

#### 14.1 为什么使用它？
通过groupFooterFormatter函数，您可以自定义表格中分组脚的显示内容和样式，以满足特定的业务需求或视觉设计要求。

#### 14.2 参数介绍
`colTotal`：表格的总列数。<br/>
`tableData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`templateData`：所有打印数据。<br/>
`groupData`：当前分组的分组字段名和分组数据的对象。groupData.rows来查询分组数据。groupData.XXX可以获取当前分组字段信息。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`numberFormat`：用于自定义格式化数据的函数。<br/>
`columnsFormats`：数组类型，数组内对象保存三个属性如下：<br/>
- `columnsFormats[index].colnumIndex`: 表示当前列在表格中的索引位置，从0开始计数;<br/>
- `columnsFormats[index].format`: 列的数据格式，例如'#,##0';<br/>
- `columnsFormats[index].dataType`: 列的数据类型;<br/>

#### 14.3 示例逻辑
>  表格现在按照[月]分组，生成分组脚。<br/>
>  分组脚内容，返回4个td标签：<br/>
>  1. "合计："；【html样式：红色字体，左右对齐方式为居中，占2列】<br/>
>  2. 数量合计：{分组内的记录的数量集记值}，数值类型数量值累加；【html样式：左右对齐方式为居左，占1列】<br/>
>  3. 单价合计：{分组内的记录的单价集记值}，数值类型单价值累加；【html样式：左右对齐方式为居左，占1列】<br/>
>  4. 金额合计：{分组内的记录的金額集记值}，数值类型金额值累加；【html样式：左右对齐方式为居左，占1列】<br/>

> 表格字段：productName(商品名 ／ 品名),quantity(数 量),unitPrice(単 価),amount(金 額),month(月)<br/>

```
function groupFooterFormatter(colTotal, tableData, templateData, groupData, options, numberFormat, columnsFormats) {
    let quantitySum = 0;
    let unitPriceSum = 0;
    let amountSum = 0;
    groupData.rows.forEach(function(data) {
        quantitySum += parseInt(data.quantity, 10); 
        unitPriceSum += parseFloat(data.unitPrice); 
        amountSum += parseFloat(data.amount); 
    });
    return `
        <td class="hi-td-center" colspan="2" style="color: red; text-align: center;">合计：</td>
        <td class="hi-td-left" style="text-align: left;">数量合计：${numberFormat(quantitySum, columnsFormats[2].format)}</td>
        <td class="hi-td-left" style="text-align: left;">单价合计：${numberFormat(unitPriceSum, columnsFormats[3].format)}</td>
        <td class="hi-td-left" style="text-align: left;">金额合计：${numberFormat(amountSum, columnsFormats[4].format)}</td>`;
}
```

#### 14.4 示例效果展示
![高级函数功能_分组脚格式化函数](../_images/zh-cn/高级函数功能_分组脚格式化函数.gif)
<br>
<br>
<br>

### **15. 表格：多组表格脚函数{gridColumnsFooterFormatter}**

#### 15.1 为什么使用它？
在数据分析、报告生成等场景中，通过此函数，您可以在表格底部添加一个自定义的、包含统计信息的多组表格脚。这个功能在需要向用户展示表格数据的总体统计时非常有用。例如，当用户在查看大量数据时，一个明确的总和或其他统计信息可以帮助他们快速了解数据的规模或特征。

#### 15.2 参数介绍
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`rowsData`：表示当前表格的所有行数据的数组，用于访问更广泛的数据上下文。<br/>
`templateData`：所有打印数据。<br/>
`pageData`：表示当前表格的所有行数据的数组(包括空行数据)，用于访问更广泛的数据上下文。<br/>

#### 15.3 示例逻辑
>  统计表格有多少笔记录，生成多组表格脚【html样式：红色字体】。<br/>

```
function gridColumnsFooterFormatter(options, rowsData, templateData, pageData) {
    let rowCount = rowsData.length;
    return `<span style="color:red;">${rowCount} 行</span>`; 
}
```

#### 15.4 示例效果展示
![高级函数功能_多组表格脚函数](../_images/zh-cn/高级函数功能_多组表格脚函数.gif)
<br>
<br>
<br>

### **16. 图表：渲染函数{eChartsOption}**

#### 16.1 为什么使用它？
通过eChartsOption函数，您可以根据需求，定制图表的配置项，从而确保图表能够准确地展示数据。例如，您有一个销售数据的报告，需要展示不同产品在不同时间段的销售额。您可以使用柱状图来展示这些数据，并通过eChartsOption函数来定制图表的配置项。

#### 16.2 参数介绍
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`templateData`：所有打印数据。<br/>
`echarts`：echarts.js的组件。<br/>
`chart`：echarts.js初始化后，当前元素的echarts属性。<br/>
`columns`：数组类型，当前图表元素对应的表格元素的所有列的信息。<br/>

####  ① 柱状图
###### 示例逻辑
```
1.数据来源：将templateData中的表格histogramTable，生成柱状图，需要使用templateData?.的方式。
2.数据布局：不堆叠。
3.X轴配置：如果标题(options.customTitle)字段不为空使用","分割作为标题，如果标题(options.customTitle)字段为空使用表格的标题。
4.Y轴配置：字段值。
5.样式要求：
 - 颜色方案：柱子颜色按照表格的记录分类，从浅蓝到深蓝。
 - 字体：Arial字体，字号为12pt，颜色为深灰色(#444444)。
 - 背景与网格线：背景米白色(#F8F8F8)，Y轴和X轴的网格线设置为细虚线，颜色为浅灰色(#DDDDDD)。
```

###### 示例代码

```
function eChartsOption(options, templateData) {
    let histogramTable = templateData?.histogramTable || [];
    let categories = []; // X轴数据类别
    let seriesData = []; // 系列数据
    let colorPalette = ['#87CEFA', '#1E90FF']; // 浅蓝到深蓝颜色渐变

    histogramTable.forEach((item, index) => {
        for (let key in item) {
            if (categories.indexOf(key) === -1) {
                categories.push(key);
            }
            if (!seriesData[index]) {
                seriesData[index] = {
                    name: key,
                    type: 'bar',
                    stack: null, // 不堆叠
                    data: [],
                    itemStyle: {
                        color: colorPalette[index % colorPalette.length] // 循环使用颜色
                    }
                };
            }
            seriesData[index].data.push(item[key]);
        }
    });

    let xAxisData = options.customTitle ? options.customTitle.split(',') : categories;

    let option = {
        backgroundColor: '#F8F8F8', // 背景米白色
        textStyle: {
            fontFamily: 'Arial',
            fontSize: 12,
            color: '#444444' // 字体样式
        },
        xAxis: {
            type: 'category',
            data: xAxisData,
            axisLine: {lineStyle: {color: '#DDDDDD', type: 'dashed'}}, // X轴网格线
            axisTick: {show: false},
            axisLabel: {textStyle: {color: '#444444'}}
        },
        yAxis: {
            type: 'value',
            splitLine: {lineStyle: {color: '#DDDDDD', type: 'dashed'}} // Y轴网格线
        },
        series: seriesData
    };

    return option;
}
```

###### 示例效果展示
![高级函数功能_渲染函数_柱状图](../_images/zh-cn/高级函数功能_渲染函数_柱状图.gif)
<br>
<br>
<br>

#### ② 折线图
###### 示例逻辑
```
1. 数据来源：将templateData中的表格histogramTable，生成折线图，需要使用templateData?.的方式。
2. X轴配置：如果标题(options.customTitle)字段不为空使用","分割作为标题，如果标题(options.customTitle)字段为空使用表格的标题。
3. Y轴配置：字段值。
4. 样式要求：
 - 颜色方案：折线颜色按照表格的记录分类，显示不同颜色。
 - 折线上显示值。
```

###### 示例代码

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // 初始化x轴数据和系列数据
  let xAxisData = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
  let seriesData = [[150, 230, 224, 218, 135, 147, 260]];
  // 检查options和templateData是否存在
  if (options && options.field && templateData) {
    // 从templateData中获取字段数据字符串
    let fieldDataStr = templateData[options.field];
    // 如果fieldDataStr存在且长度大于0
    if (fieldDataStr && fieldDataStr.length > 0) {
      // 设置x轴数据为fieldDataStr的第一个对象的键值
      xAxisData = Object.keys(fieldDataStr[0]);
      // 如果有自定义标题
      if (options.customTitle) {
        // 使用逗号分隔的自定义标题数组替换x轴数据
        let customTitles = options.customTitle.split(',');
        xAxisData = customTitles.map(item => {
          return item;
        });
      } 
      // 否则如果有列定义
      else if (columns && columns.length > 0) {
        // 根据列定义中的标题替换x轴数据
        xAxisData = xAxisData.map(item => {
          const matchColumn = columns.find(column => column.field === item);
          return (matchColumn && matchColumn.title) ? matchColumn.title : item;
        });
      }
      // 清空seriesData
      seriesData = [];
      // 遍历fieldDataStr，将每个对象的值推入seriesData
      fieldDataStr.forEach(item => {
        seriesData.push(Object.values(item));
      });
    }
  }
  // 为每个系列数据创建一个对象，设置类型为"line"
  let series = seriesData.map(function(data) {
    return {
      data: data,
      type: "line",
    };
  });
  // 构建option对象
  let option = {
    xAxis: {
      type: "category",  // 设置x轴类型为类别型
      data: xAxisData,   // 设置x轴数据
    },
    yAxis: {
      type: "value",     // 设置y轴类型为数值型
    },
    series: series,      // 设置系列数据
    tooltip: {
      trigger: 'axis'    // 设置折线上显示值
    }
  };
  // 返回option对象
  return option;
}
```

###### 示例效果展示
![高级函数功能_渲染函数_折线图](../_images/zh-cn/高级函数功能_渲染函数_折线图.gif)
<br>
<br>
<br>

#### ③ 饼图
###### 示例逻辑
```
1. 数据来源：将templateData中的表格pieChartTable，生成饼图，需要使用templateData?.的方式。
2. 表格字段：如果标题(options.customTitle)字段不为空使用","分割作为表格字段，如果标题(options.customTitle)字段为空使用表格的标题。
3. 样式要求：边缘圆滑，高亮时放大。
```

###### 示例代码

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // 初始化系列数据为一个饼图的默认值
  let seriesData = [
    { value: 1048, name: "Search Engine" },
    { value: 735, name: "Direct" },
    { value: 580, name: "Email" },
    { value: 484, name: "Union Ads" },
    { value: 300, name: "Video Ads" },
  ];
  // 检查options和templateData是否存在并且field属性是否存在
  if (options && options.field && templateData) {
    // 从templateData中获取指定field的数据
    let fieldDataStr = templateData[options.field];
    // 如果fieldDataStr存在且长度大于0
    if (fieldDataStr && fieldDataStr.length > 0) {
      // 清空系列数据
      seriesData = [];
      // 如果有自定义标题
      if (options.customTitle) {
        // 使用逗号分隔的自定义标题数组生成seriesData
        let customTitles = options.customTitle.split(',');
        let values = Object.values(fieldDataStr[0]);
        seriesData = customTitles.map((item, index) => {
          return { value: values[index], name: item };
        });
      } 
      // 否则如果有列定义
      else if (columns && columns.length > 0) {
        // 根据列定义中的标题生成seriesData
        Object.keys(fieldDataStr[0]).forEach(key => {
          const matchColumn = columns.find(column => column.field === key);
          const name = matchColumn && matchColumn.title ? matchColumn.title : key;
          seriesData.push({ value: fieldDataStr[0][key], name });
        });
      } 
      // 如果没有自定义标题或列定义
      else {
        // 直接使用fieldDataStr中的键值生成seriesData
        Object.keys(fieldDataStr[0]).forEach(key => {
          seriesData.push({ value: fieldDataStr[0][key], name: key });
        });
      }
    }
  }
  // 构建option对象
  let option = {
    series: [
      {
        type: 'pie',                // 设置图表类型为饼图
        radius: ['40%', '70%'],     // 设置饼图的内外半径
        avoidLabelOverlap: false,   // 避免标签重叠
        itemStyle: {
          borderRadius: 10,         // 设置边框圆角
          borderColor: '#fff',      // 设置边框颜色
          borderWidth: 2            // 设置边框宽度
        },
        label: {
          show: true,               // 显示标签
          position: 'outside',      // 标签位置在外部
          formatter: '{b}: {d}%',   // 标签格式：显示名称和百分比
          textStyle: { fontSize: 12 } // 设置标签文字大小
        },
        emphasis: { scale: 1.1 },    // 设置强调样式，放大1.1倍
        data: seriesData            // 设置饼图数据
      }
    ]
  };
  // 返回option对象
  return option;
}
```

###### 示例效果展示
![高级函数功能_渲染函数_饼图](../_images/zh-cn/高级函数功能_渲染函数_饼图.gif)
<br>
<br>
<br>

#### ④ 雷达图
###### 示例逻辑
```
1. 数据来源：将templateData中的表格radarChartTable，生成雷达图，需要使用templateData?.的方式。
2. 标题来源：如果标题(options.customTitle)字段不为空使用","分割作为indicator的数据，如果标题(options.customTitle)字段为空使用表格的标题作为indicator的数据。
3. 样式要求：Arial字体，字号为12pt，字体颜色为黑色。
```

###### 示例代码

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // 初始化雷达图的指标数据和系列数据
  let indicatorData = [
    { name: "Sales" },
    { name: "Administration" },
    { name: "Information Technology" },
    { name: "Customer Support" },
    { name: "Development" },
    { name: "Marketing" },
  ];
  let seriesData = [
    { value: [4200, 3000, 20000, 35000, 50000, 18000] },
    { value: [5000, 14000, 28000, 26000, 42000, 21000] },
  ];
  // 检查options和templateData是否存在并且field属性是否存在
  if (options && options.field && templateData) {
    // 从templateData中获取指定field的数据
    let fieldDataStr = templateData[options.field];
    // 如果fieldDataStr存在且长度大于0
    if (fieldDataStr && fieldDataStr.length > 0) {
      // 清空指标数据
      indicatorData = [];
      // 根据fieldDataStr的键生成指标数据
      indicatorData = Object.keys(fieldDataStr[0]).map(key => ({ name: key }));
      // 如果有自定义标题
      if (options.customTitle) {
        // 使用逗号分隔的自定义标题数组生成indicatorData
        let customTitles = options.customTitle.split(',');
        indicatorData = customTitles.map(item => {
          return { name: item };
        });
      } 
      // 否则如果有列定义
      else if (columns && columns.length > 0) {
        // 根据列定义中的标题生成indicatorData
        indicatorData = indicatorData.map(item => {
          const matchColumn = columns.find(column => column.field === item.name);
          return { name: (matchColumn && matchColumn.title) ? matchColumn.title : item.name };
        });
      }
      // 清空系列数据
      seriesData = [];
      // 根据fieldDataStr生成系列数据
      seriesData = fieldDataStr.map(item => {
        return { value: Object.values(item) };
      });
    }
  }
  // 构建option对象
  let option = {
    radar: {
      indicator: indicatorData,  // 设置雷达图的指标数据
      axisName: {
        fontSize: 12,            // 设置指标名称字体大小
        fontFamily: 'Arial',     // 设置指标名称字体
        color: 'black'           // 设置指标名称颜色
      }
    },
    series: [
      {
        name: "Budget vs spending", // 设置系列名称
        type: "radar",              // 设置图表类型为雷达图
        data: seriesData,           // 设置系列数据
      },
    ],
    textStyle: {
      fontFamily: 'Arial',          // 设置全局字体
      fontSize: 12,                 // 设置全局字体大小
      color: 'black'                // 设置全局字体颜色
    },
    legend: {
      textStyle: {
        fontFamily: 'Arial',        // 设置图例字体
        fontSize: 12,               // 设置图例字体大小
        color: 'black'              // 设置图例字体颜色
      }
    }
  };
  // 返回option对象
  return option;
}
```

###### 示例效果展示
![高级函数功能_渲染函数_雷达图](../_images/zh-cn/高级函数功能_渲染函数_雷达图.gif)
<br>
<br>
<br>

#### ⑤ 散点图
###### 示例逻辑
```
1. 数据来源：将templateData中的表格scatterPlotTable，生成散点图，需要使用templateData?.的方式。
2. 数据列：如果数据列(options.dataColumns)字段不为空使用","分割作为表格字段，如果数据列(options.dataColumns)字段为空使用步骤一的数据来源。
3. 样式要求：显示散点上的值。
```

###### 示例代码

```
function eChartsOption(options, templateData, echarts, chart, columns) {
    // 初始化系列数据为空数组
    let seriesData = [];
    // 根据 options 中的 dataColumns 属性获取数据列
    let dataColumns = options.dataColumns ? options.dataColumns.split(',') : null;
    // 确定使用的列，如果 dataColumns 存在则使用它，否则使用 templateData 中的列
    const useColumns = dataColumns || Object.keys(templateData?.scatterPlotTable[0]);
    // 如果使用的列数不是偶数，发出警告并移除最后一个元素
    if (useColumns.length % 2 !== 0) {
        console.warn('数据列数量应为偶数，以确保每一对数据都能映射到x和y轴。');
        useColumns.pop(); // 移除最后一个元素以保持偶数个数
    }
    // 遍历模板数据的 scatterPlotTable
    templateData?.scatterPlotTable.forEach(item => {
        // 每次处理两列数据，分别映射到 x 和 y 轴
        for (let i = 0; i < useColumns.length; i += 2) {
            const xKey = useColumns[i];
            const yKey = useColumns[i + 1];
            seriesData.push({
                value: [item[xKey], item[yKey]], // 设置散点的 x 和 y 值
                symbolSize: function(val) {
                    return val[1] ? 10 : 5; // 根据 y 值调整散点大小
                },
                label: {
                    show: true, // 显示标签
                    formatter: '{c}', // 标签内容为散点的值
                    position: 'top', // 标签位置在顶部
                },
            });
        }
    });
    // 返回 eCharts 图表配置对象
    return {
        xAxis: {
            type: 'value', // x 轴类型为数值型
        },
        yAxis: {
            type: 'value', // y 轴类型为数值型
        },
        series: [{
            data: seriesData, // 设置系列数据
            type: 'scatter', // 设置图表类型为散点图
            symbolSize: function(val) {
                return val[1] ? 10 : 5; // 根据 y 值调整散点大小
            },
            label: {
                show: true, // 显示标签
                formatter: '{c}', // 标签内容为散点的值
                position: 'top', // 标签位置在顶部
            },
        }],
        textStyle: {
            fontFamily: 'Arial', // 设置全局字体为 Arial
            fontSize: 12, // 设置全局字体大小为 12
            color: 'black', // 设置全局字体颜色为黑色
        },
    };
}
```

###### 示例效果展示
![高级函数功能_渲染函数_散点图](../_images/zh-cn/高级函数功能_渲染函数_散点图.gif)
<br>
<br>
<br>

#### ⑥ 漏斗图
###### 示例逻辑
```
1.  数据来源：将templateData中的表格funnelChartTable，生成漏斗图，需要使用templateData?.的方式。
2.  表格字段：如果标题(options.customTitle)字段不为空使用","分割作为标题，如果标题(options.customTitle)字段为空使用表格的标题。
3.  样式要求：
 - 颜色方案：漏斗图颜色按照表格的记录分类，显示不同颜色。
```

###### 示例代码

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // 初始化图例数据和系列数据
  let legendData = ["Show", "Click", "Visit", "Inquiry"];
  let seriesData = [
    { value: 60, name: "Visit" },
    { value: 40, name: "Inquiry" },
    { value: 20, name: "Order" },
    { value: 80, name: "Click" },
    { value: 100, name: "Show" },
  ];
  // 检查options和templateData是否存在并且field属性是否存在
  if (options && options.field && templateData) {
    // 从templateData中获取指定field的数据
    let fieldDataStr = templateData[options.field];
    // 如果fieldDataStr存在且长度大于0
    if (fieldDataStr && fieldDataStr.length > 0) {
      // 获取fieldDataStr的键名作为初始的图例数据
      var names = Object.keys(fieldDataStr[0]);
      legendData = Object.keys(fieldDataStr[0]);
      // 如果有自定义标题
      if (options.customTitle) {
        // 使用逗号分隔的自定义标题数组替换legendData
        let customTitles = options.customTitle.split(',');
        legendData = customTitles.map(item => {
          return item;
        });
      } 
      // 否则如果有列定义
      else if (columns && columns.length > 0) {
        // 根据列定义中的标题替换legendData
        legendData = legendData.map(item => {
          const matchColumn = columns.find(column => column.field === item);
          return (matchColumn && matchColumn.title) ? matchColumn.title : item;
        });
      }
      // 清空系列数据
      seriesData = [];
      // 遍历fieldDataStr，生成seriesData
      fieldDataStr.forEach(item => {
        legendData.forEach((data, index) => {
          var dataObject = {};
          dataObject['value'] = item[names[index]];
          dataObject['name'] = data;
          seriesData.push(dataObject);
        });
      });
    }
  }
  // 构建option对象
  let option = {
    legend: {
      data: legendData, // 设置图例数据
    },
    series: [
      {
        name: "Funnel",          // 系列名称
        type: "funnel",          // 设置图表类型为漏斗图
        left: "10%",             // 设置图表左边距
        top: 60,                 // 设置图表上边距
        bottom: 60,              // 设置图表下边距
        width: "80%",            // 设置图表宽度
        min: 0,                  // 设置最小值
        max: 100,                // 设置最大值
        minSize: "0%",           // 设置最小尺寸
        maxSize: "100%",         // 设置最大尺寸
        sort: "descending",      // 设置排序方式为降序
        gap: 2,                  // 设置漏斗图元素之间的间隙
        label: {
          show: true,            // 显示标签
          position: "inside"     // 标签位置在内部
        },
        labelLine: {
          length: 10,            // 标签线长度
          lineStyle: {
            width: 1,            // 标签线宽度
            type: "solid"        // 标签线类型
          },
        },
        itemStyle: {
          borderColor: "#fff",   // 设置边框颜色
          borderWidth: 1,        // 设置边框宽度
        },
        emphasis: {
          label: {
            fontSize: 20,        // 设置强调状态下标签的字体大小
          },
        },
        data: seriesData,        // 设置系列数据
      },
    ],
  };
  // 返回option对象
  return option;
}
```

###### 示例效果展示
![高级函数功能_渲染函数_漏斗图](../_images/zh-cn/高级函数功能_渲染函数_漏斗图.gif)
<br>
<br>
<br>

<h4 id="self-format1"></h4>

### **17. HTML：格式化函数{formatter}**

#### 17.1 为什么使用它？
通过formatter函数允许您根据特定需求和数据内容来定制数据的展示方式。比如，您有一个销售报告，其中包含了不同格式的金额数据，有的是美元，有的是欧元。通过formatter函数，您可以轻松地将这些金额数据转换为统一的货币格式，并添加上正确的货币符号和千位分隔符。<br/>
再比如，您可能有一个超链接字段，formatter函数能够实现点击这个字段跳转到您需要的地址。

#### 17.2 参数介绍
`value`：具体元素值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`templateData`：所有打印数据。<br/>

#### 17.3 示例逻辑
> 1. 数据来源：将templateData中的richText和richImage显示在html组件中。<br/>
> 2. 数据格式：<br/>
> - richText数据格式：文本<br/>
> - richImage数据格式：图片地址<br/>
> 需求：<br/>
> - richText中`隐私政策`文本设为link，点击可以跳转到`https://www.opentext.com/ja-jp/about/privacy`<br/>

```
function formatter(value, options, templateData) {
    const richText = templateData.richText;
    const richImage = templateData.richImage;
    let htmlContent = `<div>${richText.replace('隐私政策', `<a href="https://www.opentext.com/ja-jp/about/privacy" target="_blank">隐私政策</a>`)}<br><img width="700px" src="${richImage}" alt="Rich Image"></div>`;
    return htmlContent;
}
```

#### 17.4 示例效果展示
![高级函数功能_HTML_格式化函数](../_images/zh-cn/高级函数功能_HTML_格式化函数.gif)
<br>
<br>
<br>

### **18. 图片：格式化函数{formatter}**

#### 18.1 为什么使用它？
如果您想对图片的大小、比例进行调整，formatter函数会非常有用。例如，在打印报表或生成PDF文档时，由于纸张大小或布局限制，图片可能需要缩小或放大以适应页面。

#### 18.2 参数介绍
`title`：元素的标题数据。<br/>
`value`：图片地址。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`templateData`：所有打印数据。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>

#### 18.3 示例逻辑
> 图片大小缩小50%。<br/>
```
function formatter(title, value, options, templateData, target) {
    if (!options.hasOwnProperty('isResized')) {
        options.isResized = true;
        options.width *= 0.5;
        options.height *= 0.5;
    }
    return value; 
}
```

#### 18.4 示例效果展示
![高级函数功能_图片_格式化函数](../_images/zh-cn/高级函数功能_图片_格式化函数.gif)
<br>
<br>
<br>

### **19. 图片：样式函数{styler}**

#### 19.1 为什么使用它？
当您需要美化图片时，styler函数会非常有用。例如，您有一个产品图，通过styler函数为图片添加上下左右边框线，边框颜色为蓝色。这样，产品图片就会以更加突出和美观的方式展示给用户。

#### 19.2 参数介绍
`value`：图片地址。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>
`templateData`：所有打印数据。<br/>

#### 19.3 示例逻辑
> 图片添加上下左右边框线，蓝色。<br/>
```
function styler(value, options, target, templateData) {
    return {
        'borderWidth': '1pt', 
        'borderColor': 'blue', 
        'borderStyle': 'solid', 
        'borderTop': '1pt solid blue',
        'borderBottom': '1pt solid blue',
        'borderLeft': '1pt solid blue',
        'borderRight': '1pt solid blue'
    };
}
```

#### 19.4 示例效果展示
![高级函数功能_图片_样式函数](../_images/zh-cn/高级函数功能_图片_样式函数.gif)
<br>
<br>
<br>

### **20. 二维码/条形码：格式化函数{formatter}**

#### 20.1 为什么使用它？
当您想对二维码/条形码进行定制化的处理，可以使用formatter函数。例如，在物流系统中，希望条形码的值与其他标识符有所关联，比如条形码前都有"ORD-"。

#### 20.2 参数介绍
`title`：元素的标题数据。<br/>
`value`：具体元素值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`templateData`：所有打印数据。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>

#### 20.3 示例逻辑
> 在条形码值前添加"ORD-"前缀。

```
function formatter(title, value, options, templateData, target) { 
    var barcodeValue = 'ORD-' + value;
    return barcodeValue;
}
```

#### 20.4 示例效果展示
![高级函数功能_二维码、条形码_格式化函数](../_images/zh-cn/高级函数功能_二维码、条形码_格式化函数.gif)
<br>
<br>
<br>

### **21. 二维码/条形码：样式函数{styler}**

#### 21.1 为什么使用它？
通过styler函数，您可以控制条形码或二维码的颜色、边框、大小等样式属性。例如，在物流跟踪系统中，已发货的条形码可以使用绿色表示，而退货或异常的条形码则可以使用红色表示。

#### 21.2 参数介绍
`value`：具体元素值。<br/>
`options`：包含当前元素的所有属性的对象，用于逻辑判断和获取特定信息。<br/>
`target`：一个包含外层div元素DOM信息的对象。用于后续样式设置时直接定位到目标元素。<br/>
`templateData`：所有打印数据。<br/>

#### 21.3 示例逻辑
> 条形码值设置颜色为绿色。添加上下左右边框线，蓝色。<br/>
```
function styler(value, options, target, templateData) {
    return {
        color: 'green', 
        border: '1px solid blue' 
    };
}
```

#### 21.4  示例效果展示
![高级函数功能_二维码、条形码_样式函数](../_images/zh-cn/高级函数功能_二维码、条形码_样式函数.gif)
<br>
<br>
<br>