<h5 id="start"></h5>

### Advanced Functionality

<aside>
💡 Advanced functions allow you to handle text, styles, and table elements more flexibly, meeting various complex printing needs.
</aside>
<br>

### **1. Text/Long Text: Format Function {formatter}**

<mark>**Note**</mark>: It can only access templateData and cannot calculate dynamic elements via script.

#### 1.1 Why Use It?
The formatter function allows you to easily transform data into a specified format, such as formatting dates or adding thousand separators.<br/> 
It is also very useful when you need to calculate or process data, such as calculating the sum of a particular column in a table.<br/>

#### 1.2 Parameter Description
`title`: The title data of the element.<br/>
`value`: The specific value of the element.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`templateData`: All print data.<br/>
`target`: An object that contains the outer div element DOM information. It is used to directly locate the target element when setting styles later.<br/>

#### 1.3 Example Logic
> Calculate the total value of the [Amount] column in the table detaillist in templateData.<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month)
```
function formatter(title,value,options,templateData,target){
  let amount = 0;
  for (let index = 0; index < templateData?.detaillist?.length; index++) {
      amount += 1 * templateData.detaillist[index].amount;
  }
  return amount;
}
```

#### 1.4 Example Effect Display
![highlevel2](../_images/zh-cn/highlevel/highlevel2.png)
<br>
<br>
<br>

### **2. Text/Long Text: Style Function {styler}**

#### 2.1 Why Use It?
When you want to apply specific styles to text or long text elements, you can use the style function. For example, you might want to set a particular font, color, or alignment for a text element.

#### 2.2 Parameter Description
`value`: The specific value of the element.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`target`: An object that contains the outer div element DOM information. It is used to directly locate the target element when setting styles later.<br/>
`templateData`: All print data.<br/>

#### 2.3 Example Logic
> Vertical writing mode, from left to right.
```
function styler(value, options, target, templateData) {
    return {
        writingMode: 'vertical-lr', 
    };
}
```

#### 2.4 Example Effect Display
![highlevel2](../_images/zh-cn/highlevel/highlevel1.png)
<br>
<br>
<br>

### **3. Table Column: Footer Aggregate Format Function {tableSummaryFormatter}**

#### 3.1 Why Use It?
When you want to display the sum, average, or other statistical information of a column at the bottom of a table, you can use the footer aggregate formatter function. This is very useful for providing an overview and statistics of the data.

#### 3.2 Parameter Description
`column`: An object representing the properties of the current column. Through this, you can access the column’s name, value, etc.<br/>
`fieldPageData`: An array containing all row data for the current column.<br/>
`tableData`: An array representing all row data in the current table, used to access a broader data context.<br/>
`options`: An object that contains all properties of the current table, used for logical judgments and retrieving specific information.<br/>

#### 3.3 Example Logic
> Display "Total Quantity: " + {total value}. Total value: Accumulate the numerical values in the column, adding comma separators for thousands, and do not display decimals. 【HTML style: Center aligned, light blue background, red font.】<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month)

```
function tableSummaryFormatter(column, fieldPageData, tableData, options) {
    let sum = fieldPageData.reduce((acc, cur) => acc + parseInt(cur), 0); 
    let formattedSum = sum.toLocaleString(); 
    return `<td style="text-align:center;background-color:lightblue;color:red;">数量合計：${formattedSum}</td>`; 
}
```

#### 3.4 Example Effect Display
![highlevel3](../_images/zh-cn/highlevel/highlevel3.png)
<br>
<br>
<br>

### **4. Table Column: Cell Render Function {renderFormatter}**

#### 4.1 Why Use It?
The renderFormatter function allows you to customize the rendering of cells based on the characteristics of the data, such as color marking, date formatting, currency values, or percentages. For example, when inventory managers need to quickly identify products with low stock, the renderFormatter function can highlight these products' stock levels, making them immediately visible.

#### 4.2 Parameter Description
`value`: The print data value of the cell.<br/>
`row`: An object representing the data of the current row. You can query the value of a specific column in the current row through `row.columnName`.<br/>
`colIndex`: The index position of the current column in the table, starting from 0.<br/>
`options`: An object that contains all properties of the current table, used for logical judgments and retrieving specific information.<br/>
`rowIndex`: The index position of the current row in the table, starting from 0.<br/>

#### 4.3 Example Logic
> In the [Product Name] column, add: row number after the text. 【HTML style: red font】<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).
```
function renderFormatter(value, row, colIndex, options, rowIndex) {
    return `<td style="color:red;">${value} 行号：${rowIndex + 1}</td>`;
}
```

#### 4.4 Example Effect Display
![highlevel4](../_images/zh-cn/highlevel/highlevel4.png)
<br>
<br>
<br>

### **5. Table Column: Cell Format Function {formatter2}**

#### 5.1 Why Use It?
When you need to display some calculated or processed data in a specific column of the table, the formatter2 function becomes very useful. For example, if you have employee performance information that includes the employee's name, sales amount, sales target, and achievement rate (the ratio of sales amount to sales target), you can use the formatter2 function to calculate the achievement rate, saving the user from manually performing the calculations.

#### 5.2 Parameter Description
`value`: The print data value of the cell.<br/>
`row`: An object representing the data of the current row. You can query the value of a specific column in the current row through `row.columnName`.<br/>
`colIndex`: The index position of the current column in the table, starting from 0.<br/>
`options`: An object that contains all properties of the current table, used for logical judgments and retrieving specific information.<br/>

#### 5.3 Example Logic
> For data where the [Amount] is greater than 60,000, add 6 to the value in the [Quantity] column. <br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).

```
function formatter2(value, row, colIndex, options) {
    if(row.amount > 60000) {
        return Number(row.quantity) + 6;
    }
    return value;
}
```

#### 5.4 Example Effect Display
![highlevel5](../_images/zh-cn/highlevel/highlevel5.png)
<br>
<br>
<br>

### **6. Table Column: Cell Style Function {styler2}**

#### 6.1 Why Use It?
The `styler2` function allows you to dynamically apply different styles to cells (such as color, font, border, etc.).

#### 6.2 Parameter Description
`value`: The print data value of the cell.<br/>
`row`: An object representing the data of the current row. You can query the value of a specific column in the current row through `row.columnName`.<br/>
`colIndex`: The index position of the current column in the table, starting from 0.<br/>
`options`: An object that contains all properties of the current table, used for logical judgments and retrieving specific information.<br/>

#### 6.3 Example Logic
> For [Quantity] text type data, if the value equals "200", set the font color to red and align the text to the center.

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).

```
function styler2(value, row, index, options) {
  if (row.quantity === '200') {
    return {color: 'red', textAlign: 'center'};
  }
}
```

#### 6.4 Example Effect Display
![highlevel6](../_images/zh-cn/highlevel/highlevel6.png)
<br>
<br>
<br>

### **7. Table Column: Header Style Function {stylerHeader}**

#### 7.1 Why Use It?
The `stylerHeader` function allows you to dynamically apply different styles to table headers (such as color, font, border, etc.).

#### 7.2 Parameter Description
`options`: An object that contains all properties of the current table, used for logical judgments and retrieving specific information.

#### 7.3 Example Logic
> For the current column (Product Name), set the header font color to red, align text to the right, and use italic font style.

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).

```
function stylerHeader(options) {
    return {color: 'red', textAlign: 'right', fontStyle: 'italic'};
}
```

#### 7.4 Example Effect Display
![highlevel7](../_images/zh-cn/highlevel/highlevel7.png)
<br>
<br>
<br>

### **8. Table: Style Function {styler}**

#### 8.1 Why Use It?
The `styler` function allows you to dynamically apply different styles to the entire table (such as color, font, border, etc.).

#### 8.2 Parameter Description
`value`: An array representing all row data of the current table, used to access a broader data context.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`target`: An object containing the DOM information of the table element. Used to directly locate the target element when setting styles later.<br/>
`templateData`: All print data.<br/>

#### 8.3 Example Logic
> Set the border of the current table to 2px solid yellow.

```
function styler(value, options, target, templateData){
  return {"border":"2px solid yellow"};
}
```

#### 8.4 Example Effect Display
![highlevel8](../_images/zh-cn/highlevel/highlevel8.png)
<br>
<br>
<br>

### **9. Table: Row Style Function {rowStyler}**

#### 9.1 Why Use It?
The `rowStyler` function allows you to dynamically apply different styles to table rows (such as color, font, border, etc.).

#### 9.2 Parameter Description
`value`: An object representing the current row data. You can query the value of a specific column in the current row using `value.columnName`.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`rowIndex`: Indicates the index position of the current row in the table, starting from 0.<br/>

#### 9.3 Example Logic
> Set the background color of odd rows to light blue and the font color to dark blue.

```
function rowStyler(value, options, rowIndex) {
    return rowIndex % 2 === 0 ? { 'background-color': '#add8e6', 'color': '#00008b' } : {};
}
```

#### 9.4 Example Effect Display
![highlevel9](../_images/zh-cn/highlevel/highlevel9.png)
<br>
<br>
<br>

### **10. Table: Table Footer Function {footerFormatter}**

#### 10.1 Why Use It?
The `footerFormatter` function allows you to customize the content of the table footer, making it possible to dynamically reflect summary or statistical data at the bottom of the table.

#### 10.2 Parameter Description
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`rowsData`: An array representing all row data of the current table, used to access a broader data context.<br/>
`data`: Data for each page of the table.<br/>
`templateData`: All print data.<br/>

#### 10.3 Example Logic
> Generate table footer<br/>
> Table footer content returns 2 `<td>` tags:<br/>
  > 1. "Quantity Total:"; [HTML style: centered alignment, spans 2 columns]<br/>
  > 2. `{Total Quantity}`, the sum of numeric quantity values, excluding non-numeric values and empty rows. [HTML style: left alignment, spans 3 columns]<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).

```
function footerFormatter(options, rowsData, data, templateData) {
  let totalQuantity = 0;
  rowsData.forEach(row => {
    const quantity = Number(row.quantity);
    if (!isNaN(quantity)) {
      totalQuantity += quantity;
    }
  });
  return `<tr><td colspan="2" style="text-align:center;">Quantity Total:</td><td colspan="2" style="text-align:left;">${totalQuantity}</td></tr>`;
}
```

#### 10.4 Example Effect Display
![highlevel10](../_images/zh-cn/highlevel/highlevel10.png)
<br>
<br>
<br>

### **11. Table: Row/Column Merge Function {rowsColumnsMerge}**

#### 11.1 Why Use It?
When there are many rows in a table with the same value (e.g., product name), you can use the `rowsColumnsMerge` function to merge these rows or columns, optimizing the table's display.

#### 11.2 Parameter Description
`data`: An object representing the current row data. You can query the value of a specific column in the current row using `data.columnName`.<br/>
`column`: An object representing the relevant attributes of the current column. You can access the name, value, and other information of the column.<br/>
`colIndex`: Indicates the index position of the current column in the table, starting from 0.<br/>
`rowIndex`: Indicates the index position of the current row in the table, starting from 0.<br/>
`tableData`: An array representing all row data of the current table, used to access a broader data context.<br/>
`templateData`: All print data.<br/>

#### 11.3 Example Logic
> Merge rows with the same value in the [Product Name] column.<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month).

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

#### 11.4 Example Effect Display
![highlevel11](../_images/zh-cn/highlevel/highlevel11.png)
<br>
<br>
<br>

<h4 id="self-group1"></h4>

### **12. Table: Group Field Function {groupFieldsFormatter}**

<mark>Note</mark>: This function should be used in conjunction with the Group Header Format Function and the Group Footer Format Function.

#### 12.1 Why Use It?
The `groupFieldsFormatter` function allows you to group the data in the table by specified fields. This helps in clearly seeing the differences and trends between different groups, thereby better understanding the meaning behind the data.

#### 12.2 Parameter Description
`type`: The basic properties of the current table element.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`data`: An array representing all row data of the current table, used to access a broader data context.<br/>

#### 12.3 Example Logic
> Group by [Month]<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month)<br/>

```
function groupFieldsFormatter(type, options, data) {
    return ['month'];
}
```

#### 12.4 Example Effect Display
![highlevel13](../_images/zh-cn/highlevel/highlevel13.png)
<br>
<br>
<br>

<h4 id="self-group2"></h4>

### **13. Table: Group Header Format Function {groupFormatter}**

<mark>Note</mark>: This function should be used in conjunction with the Group Field Function.

#### 13.1 Why Use It?
The `groupFormatter` function allows you to customize the display content and style of the group header in the table, meeting specific business needs or visual design requirements.

#### 13.2 Parameter Description
`colTotal`: The total number of columns in the table.<br/>
`tableData`: An array representing all row data of the current table, used to access a broader data context.<br/>
`templateData`: All print data.<br/>
`groupData`: An object containing the group field name and group data of the current group. Use `groupData.rows` to query group data and `groupData.fieldName` to get the current group field information.
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`numberFormat`: A function for custom formatting data.<br/>
`columnsFormats`: An array where each object contains the following three properties:<br/>
- `columnsFormats[index].colnumIndex`: Indicates the index position of the current column in the table, starting from 0.
- `columnsFormats[index].format`: The data format of the column, e.g., '#,##0'.
- `columnsFormats[index].dataType`: The data type of the column.

<div id="groupFormatter"></div>

#### 13.3 Example Logic
> The table is now grouped by [Month], generating a group header.<br/>
> Group header content: `{groupFieldValue} + "月のデータは以下の通りです："` [HTML style: no line breaks, spans all columns, centered alignment, blue font].<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month)

```
function groupFormatter(colTotal, tableData, templateData, groupData, options, numberFormat, columnsFormats) {
    return `<td class="hi-td-center" style="color: blue; text-align: center;" colspan="${colTotal}">${groupData.month}月のデータは以下の通りです：</td>`;
}
```

#### 13.4 Example Effect Display
![highlevel14](../_images/zh-cn/highlevel/highlevel14.png)
<br>
<br>
<br>

<h4 id="self-group3"></h4>

### **14. Table: Group Footer Format Function {groupFooterFormatter}**

<mark>Note</mark>: This function should be used in conjunction with the Group Field Function.

#### 14.1 Why Use It?
The `groupFooterFormatter` function allows you to customize the display content and style of the group footer in the table, meeting specific business needs or visual design requirements.

#### 14.2 Parameter Description
`colTotal`: The total number of columns in the table.<br/>
`tableData`: An array representing all row data of the current table, used to access a broader data context.<br/>
`templateData`: All print data.<br/>
`groupData`: An object containing the group field name and group data of the current group. Use `groupData.rows` to query group data and `groupData.fieldName` to get the current group field information.<br/>
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.<br/>
`numberFormat`: A function for custom formatting data.<br/>
`columnsFormats`: An array where each object contains the following three properties:<br/>
- `columnsFormats[index].colnumIndex`: Indicates the index position of the current column in the table, starting from 0.
- `columnsFormats[index].format`: The data format of the column, e.g., '#,##0'.
- `columnsFormats[index].dataType`: The data type of the column.

#### 14.3 Example Logic
> The table is now grouped by [Month], generating a group footer.<br/>
> Group footer content returns 4 `<td>` tags:<br/>
  > 1. "Total:"; [HTML style: red font, centered alignment, spans 2 columns]<br/>
  > 2. Quantity count: `{sum of quantity in the group}`, sums numeric values only; [HTML style: left alignment, spans 1 column]<br/>
  > 3. Total unit price: `{sum of unit prices in the group}`, sums numeric values only; [HTML style: left alignment, spans 1 column]<br/>
  > 4. Total amount: `{sum of amounts in the group}`, sums numeric values only; [HTML style: left alignment, spans 1 column]<br/>

> Table field information: productName (Product Name), quantity (Quantity), unitPrice (Unit Price), amount (Amount), month (Month)

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
        <td class="hi-td-center" colspan="2" style="color: red; text-align: center;">Total:</td>
        <td class="hi-td-left" style="text-align: left;">Quantity Count: ${quantitySum}</td>
        <td class="hi-td-left" style="text-align: left;">Total Unit Price: ${unitPriceSum.toFixed(2)}</td>
        <td class="hi-td-left" style="text-align: left;">Total Amount: ${amountSum.toFixed(2)}</td>`;
}
```

#### 14.4 Example Effect Display
![highlevel15](../_images/zh-cn/highlevel/highlevel15.png)
<br>
<br>
<br>

### **15. Table: Multi Group Table Footer Function {gridColumnsFooterFormatter}**

#### 15.1 Why Use It?
In scenarios such as data analysis and report generation, you can add a custom multi-group table footer with statistical information at the bottom of the table. This feature is useful when you need to show overall statistics of the table data to users. For example, when viewing a large amount of data, a clear total or other statistical information can help users quickly understand the scale or characteristics of the data.

#### 15.2 Parameter Description
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.
`rowsData`: An array representing all row data of the current table, used to access a broader data context.
`templateData`: All print data.
`pageData`: An array representing all row data of the current table (including blank rows), used to access a broader data context.

#### 15.3 Example Logic
> Count the number of records in the table and generate a multi-group table footer [HTML style: red font].

```
function gridColumnsFooterFormatter(options, rowsData, templateData, pageData) {
    let rowCount = rowsData.length;
    return `<span style="color:red;">${rowCount} 行</span>`; 
}
```

#### 15.4 Example Effect Display
![highlevel16](../_images/zh-cn/highlevel/highlevel16.png)
<br>
<br>
<br>

### **16. Chart: Render Function {eChartsOption}**

#### 16.1 Why Use It?
With the `eChartsOption` function, you can customize the chart configuration items according to your needs, ensuring that the chart can accurately display the data. For example, you have a sales report that contains sales data for different products over different time periods. You can use a bar chart to display this data and customize the chart configuration items through the `eChartsOption` function.

#### 16.2 Parameter Description
`options`: An object that contains all properties of the current element, used for logical judgments and retrieving specific information.
`templateData`: All print data.
`echarts`: The echarts.js component.
`chart`: The echarts property of the current element after initialization.
`columns`: An array containing information of all columns corresponding to the current chart element.

##### ① Bar Chart
###### Example Logic
> 1. Data source: Generate a bar chart from the `histogramTable` in `templateData`.Use templateData?.<br/>
> 2. Data layout: Not stacked.<br/>
> 3. X-axis configuration: Use the title (options.customTitle) field if it is not empty, split by "," as the title. If the title (options.customTitle) field is empty, use the title of the table.<br/>
> 4. Y-axis configuration: Field value.<br/>
> 5. Style requirements:<br/>
> - Color scheme: Bar color varies by record, from light blue to dark blue.<br/>
> - Font: Arial, 12pt, dark gray (#444444).<br/>
> - Background and grid lines: Beige background (#F8F8F8), dashed grid lines for Y-axis and X-axis, light gray (#DDDDDD).<br/>

> Table fields: mon (Mon), tue (Tue), wed (Wed), thu (Thu), fri (Fri), sat (Sat), sun (Sun)
```
function eChartsOption(options, templateData) {
    let histogramTable = templateData?.histogramTable || [];
    let categories = []; // X-axis data categories
    let seriesData = []; // Series data
    let colorPalette = ['#87CEFA', '#1E90FF']; // Light blue to dark blue color gradient

    histogramTable.forEach((item, index) => {
        for (let key in item) {
            if (categories.indexOf(key) === -1) {
                categories.push(key);
            }
            if (!seriesData[index]) {
                seriesData[index] = {
                    name: key,
                    type: 'bar',
                    stack: null, // Not stacked
                    data: [],
                    itemStyle: {
                        color: colorPalette[index % colorPalette.length] // Loop through colors
                    }
                };
            }
            seriesData[index].data.push(item[key]);
        }
    });

    let xAxisData = options.customTitle ? options.customTitle.split(',') : categories;

    let option = {
        backgroundColor: '#F8F8F8', // Light beige background
        textStyle: {
            fontFamily: 'Arial',
            fontSize: 12,
            color: '#444444' // Font style
        },
        xAxis: {
            type: 'category',
            data: xAxisData,
            axisLine: { lineStyle: { color: '#DDDDDD', type: 'dashed' } }, // X-axis grid line
            axisTick: { show: false },
            axisLabel: { textStyle: { color: '#444444' } }
        },
        yAxis: {
            type: 'value',
            splitLine: { lineStyle: { color: '#DDDDDD', type: 'dashed' } } // Y-axis grid line
        },
        series: seriesData
    };

    return option;
}
```

#### Example Effect Display
![highlevel17](../_images/zh-cn/highlevel/highlevel17.png)
<br>
<br>
<br>

##### ② Line Chart
###### Example Logic
> 1. Data source: Generate a line chart from the `histogramTable` in `templateData`.<br/>
> 2. X-axis configuration: Use the title (options.customTitle) field if it is not empty, split by "," as the title. If the title (options.customTitle) field is empty, use the title of the table.<br/>
> 3. Y-axis configuration: Field value.<br/>
> 4. Style requirements:<br/>
> - Color scheme: Line colors vary by record, showing different colors.<br/>
> - Display values on the lines.<br/>

> Table fields: mon (Mon), tue (Tue), wed (Wed), thu (Thu), fri (Fri), sat (Sat), sun (Sun)<br/>
```
function eChartsOption(options, templateData) {
  if (!templateData || !templateData.histogramTable || !Array.isArray(templateData.histogramTable)) return;
  let categories = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
  let seriesData = templateData.histogramTable.map((item, index) => ({
    name: `Data Series ${index + 1}`,
    type: 'line',
    data: categories.map(day => item[day.toLowerCase()]),
    label: {
      show: true,
      position: 'top',
      formatter: '{c}'
    }
  }));
  return {
    xAxis: {
      type: 'category',
      data: categories,
      name: 'Table Title'
    },
    yAxis: {
      type: 'value',
      name: 'Field Value'
    },
    series: seriesData,
    tooltip: { trigger: 'axis' }
  };
}
```

###### Example Effect Display
![highlevel18](../_images/zh-cn/highlevel/highlevel18.png)
<br>
<br>
<br>

#### ③ Pie Chart
###### Example Logic
> 1. Data source: Generate a pie chart from the `pieChartTable` in `templateData`.<br/>
> 2. X-axis configuration: Use the title (options.customTitle) field if it is not empty, split by "," as the title. If the title (options.customTitle) field is empty, use the title of the table.<br/>
> 3. Y-axis configuration: Field value.<br/>
> 4. Style requirements: Smooth edges, enlarge on highlight.<br/>

> Table fields: mon (Mon), tue (Tue), wed (Wed)

```
function eChartsOption(options, templateData) {
  if (!templateData || !templateData.pieChartTable || !templateData.pieChartTable.length) return;
  let singleRow = templateData.pieChartTable[0];
  let seriesData = [
    { value: singleRow.mon, name: 'Mon' },
    { value: singleRow.tue, name: 'Tue' },
    { value: singleRow.wed, name: 'Wed' }
  ];
  return {
    series: [
      {
        type: 'pie',
        radius: ['40%', '70%'], 
        avoidLabelOverlap: false,
        itemStyle: {
          borderRadius: 10, 
          borderColor: '#fff', 
          borderWidth: 2 
        },
        label: {
          show: true,
          position: 'outside',
          formatter: '{b}: {d}%',
          textStyle: { fontSize: 12 } 
        },
        emphasis: { scale: 1.1 }, 
        data: seriesData
      }
    ]
  };
}
```

###### Example Effect Display
![highlevel19](../_images/zh-cn/highlevel/highlevel19.png)
<br>
<br>
<br>

##### ④ Radar Chart
###### Example Logic
> 1. Data source: Generate a radar chart from the `radarChartTable` in `templateData`.<br/>
> 2. Style requirements: Arial font, 12pt, black font color.<br/>

> Table fields: mon (Mon), tue (Tue), wed (Wed)

```
function eChartsOption(options, templateData) {
    const radarChartTable = templateData.radarChartTable;
    let indicatorData = [{ name: 'Mon' }, { name: 'Tue' }, { name: 'Wed' }];
    let seriesData = templateData.radarChartTable.map((item, index) => ({
            name: `Series ${index + 1}`,
            type: 'radar',
            data: [{ value: [item.mon, item.tue, item.wed] }]
        }));
    let option = {
        radar: {
            indicator: indicatorData,
            axisName: {
                fontSize: 12,
                fontFamily: 'Arial',
                color: 'black'
            }
        },
        series: seriesData,
        textStyle: {
            fontFamily: 'Arial',
            fontSize: 12,
            color: 'black'
        },
        legend: {
            textStyle: {
                fontFamily: 'Arial',
                fontSize: 12,
                color: 'black'
            }
        }
    };
    return option;
}
```

###### Example Effect Display
![highlevel20](../_images/zh-cn/highlevel/highlevel20.png)
<br>
<br>
<br>

##### ⑤ Scatter Plot
###### Example Logic
> 1. Data source: Generate a scatter plot from the `scatterPlotTable` in `templateData`.<br/>
> 2. Style requirements: Display values on the scatter points.<br/>

```
function eChartsOption(options, templateData, echarts, chart, columns) {
    let seriesData = [];
    if (options.field && templateData.scatterPlotTable) {
        templateData.scatterPlotTable.forEach(item => {
            seriesData.push([item.xValue, item.yValue, item.displayValue]);
        });
    }
    let option = {
        xAxis: {
            type: 'value',
        },
        yAxis: {
            type: 'value',
        },
        series: [{
            data: seriesData,
            type: 'scatter',
            symbolSize: function (val) {
                return val[2] ? 10 : 5; 
            },
            label: {
                show: true,
                formatter: '{c}', 
                position: 'top',
            },
        }],
    };
    return option;
}
```

###### Example Effect Display
![highlevel21](../_images/zh-cn/highlevel/highlevel21.png)
<br>
<br>
<br>

##### ⑥ Funnel Chart
###### Example Logic
> 1. Data source: Generate a funnel chart from the `funnelChartTable` in `templateData`.<br/>
> 2. Table fields: mon (Mon), tue (Tue), wed (Wed), thu (Thu), fri (Fri), sat (Sat), sun (Sun)<br/>
> 3. Style requirements: Funnel chart colors vary by record, showing different colors.<br/>

```
function eChartsOption(options, templateData) {
    if (!templateData || !templateData.funnelChartTable) return;
    let singleRow = templateData.funnelChartTable[0];
    let seriesData = [
        { value: singleRow.mon, name: 'Mon' },
        { value: singleRow.tue, name: 'Tue' },
        { value: singleRow.wed, name: 'Wed' },
        { value: singleRow.thu, name: 'Thu' },
        { value: singleRow.fri, name: 'Fri' },
        { value: singleRow.sat, name: 'Sat' },
        { value: singleRow.sun, name: 'Sun' }
    ];
    let option = {
        series: [{
            type: 'funnel',
            width: '80%',
            height: '80%',
            left: '10%',
            top: '10%',
            sort: 'descending',
            gap: 2,
            label: {
                show: true,
                position: 'inside'
            },
            itemStyle: {
                borderColor: '#fff',
                borderWidth: 1
            },
            data: seriesData
        }]
    };
    return option;
}
```

###### Example Effect Display
![highlevel22](../_images/zh-cn/highlevel/highlevel22.png)
<br>
<br>
<br>

### **17. HTML: Format Function {formatter}**

#### 17.1 Why Use It?
The `formatter` function allows you to customize the display of data based on specific needs and content. For example, you might have a sales report containing amounts in different currencies, such as dollars and euros. Using the `formatter` function, you can easily convert these amounts to a uniform currency format, adding the correct currency symbols and thousand separators. <br/>
Additionally, you might have a hyperlink field, and the `formatter` function can enable clicking on this field to navigate to a desired URL.

#### 17.2 Parameter Introduction
`value`: The specific element value.<br/>
`options`: An object containing all the properties of the current element, used for logical judgment and obtaining specific information.<br/>
`templateData`: All print data.<br/>

#### 17.3 Example Logic
> 1. Data Source: Display `richText` and `richImage` from `templateData` in the HTML component.<br/>
> 2. Data Format:<br/>
> - `richText` data format: Text<br/>
> - `richImage` data format: Image URL<br/>
> 3. Requirements:<br/>
> - Set the text `プライバシーポリシー` in `richText` as a link, which redirects to `https://www.opentext.com/ja-jp/about/privacy` when clicked.<br/>

```
function formatter(value, options, templateData) {
    const richText = templateData.richText;
    const richImage = templateData.richImage;
    let htmlContent = `<div>${richText.replace('プライバシーポリシー', `<a href="https://www.opentext.com/ja-jp/about/privacy" target="_blank">プライバシーポリシー</a>`)}<br><img src="${richImage}" alt="Rich Image"></div>`;
    return htmlContent;
}
```

#### 17.4 Example Effect Display
![highlevel23](../_images/zh-cn/highlevel/highlevel23.png)
<br>
<br>
<br>

### **18. Image: Format Function {formatter}**

#### 18.1 Why Use It?
If you want to adjust the size or aspect ratio of an image, the `formatter` function is very useful. For example, when printing reports or generating PDF documents, the image might need to be resized to fit the page due to paper size or layout constraints.

#### 18.2 Parameter Introduction
`title`: The title data of the element.<br/>
`value`: The image URL.<br/>
`options`: An object containing all the properties of the current element, used for logical judgment and obtaining specific information.<br/>
`templateData`: All print data.<br/>
`target`: An object containing the DOM information of the outer div element, used for directly locating the target element during subsequent style settings.<br/>

#### 18.3 Example Logic
> Resize the image to 50% of its original size.<br/>
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

#### 18.4 Example Effect Display
![highlevel24](../_images/zh-cn/highlevel/highlevel24.png)
<br>
<br>
<br>

### **19. Image: Styling Function {styler}**

#### 19.1 Why Use It?
When you need to beautify an image, the `styler` function is very useful. For example, you have a product image, and by using the `styler` function, you can add borders to the image and set the border color to blue. This way, the product image will be displayed in a more prominent and aesthetically pleasing manner to the user.

#### 19.2 Parameter Introduction
`value`: The image URL.<br/>
`options`: An object containing all the properties of the current element, used for logical judgment and obtaining specific information.<br/>
`target`: An object containing the DOM information of the outer div element, used for directly locating the target element during subsequent style settings.<br/>
`templateData`: All print data.<br/>

#### 19.3 Example Logic
> Add borders to the image (top, bottom, left, right) in blue color.<br/>
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

#### 19.4 Example Effect Display
![highlevel25](../_images/zh-cn/highlevel/highlevel25.png)
<br>
<br>
<br>

### **20. QR Code/Barcode: Format Function {formatter}**

#### 20.1 Why Use It?
When you want to customize the processing of a QR code or barcode, the `formatter` function can be very useful. For example, in a logistics system, you might want the barcode values to be associated with other identifiers, such as prefixing each barcode with "ORD-".

#### 20.2 Parameter Introduction
`title`: The title data of the element.<br/>
`value`: The specific element value.<br/>
`options`: An object containing all the properties of the current element, used for logical judgment and obtaining specific information.<br/>
`templateData`: All print data.<br/>
`target`: An object containing the DOM information of the outer div element, used for directly locating the target element during subsequent style settings.<br/>

#### 20.3 Example Logic
> Add "ORD-" prefix to the barcode value.

```
function formatter(title, value, options, templateData, target) { 
    var barcodeValue = 'ORD-' + value;
    return barcodeValue;
}
```

#### 20.4 Example Effect Display
![highlevel26](../_images/zh-cn/highlevel/highlevel26.png)
<br>
<br>
<br>

### **21. QR Code/Barcode: Styling Function {styler}**

#### 21.1 Why Use It?
Using the `styler` function, you can control the style properties of a barcode or QR code, such as color, border, and size. For example, in a logistics tracking system, barcodes for shipped items can be displayed in green, while those for returns or exceptions can be displayed in red.

#### 21.2 Parameter Introduction
`value`: The specific element value.<br/>
`options`: An object containing all the properties of the current element, used for logical judgment and obtaining specific information.<br/>
`target`: An object containing the DOM information of the outer div element, used for directly locating the target element during subsequent style settings.<br/>
`templateData`: All print data.<br/>

#### 21.3 Example Logic
> Set the barcode color to green and add borders (top, bottom, left, right) in blue.<br/>
```
function styler(value, options, target, templateData) {
    return {
        color: 'green', 
        border: '1px solid blue' 
    };
}
```

#### 21.4 Example Effect Display
![highlevel27](../_images/zh-cn/highlevel/highlevel27.png)
<br>
<br>
<br>