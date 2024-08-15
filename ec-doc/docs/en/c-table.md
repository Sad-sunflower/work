<h5 id="start"></h5>

### Table

<aside>
💡 Tables are powerful tools for organizing and presenting data. They consist of rows and columns and can contain various types of data such as text, numbers, images, QR codes, barcodes, etc. Each cell can contain text, numbers, QR codes, barcodes, images, and more. With the table element, you can easily create, edit, and adjust tables to present the required information.
</aside>

#### **Drag and Edit**

- Drag Table Element: Select the [Table] element from the element library and drag it to the desired position in the template.
- Edit Header: Double-click the table's header section to enter or modify the title.

![Table_Drag and Edit](../_images/zh-cn/表格_拖拽与编辑.gif)

#### Property Settings

#### 1. Basic Properties

`Field Name`: Define the field name of the element to associate it with the datasource (see text section for demonstration).<br/>
`Test Data`: Enter test data to preview the actual effect (the field name must be set first, see text section for demonstration).<br/>
`Position Coordinate, Width & Height`: Adjust the position, width, and height of the table on the interface (see text section for demonstration).<br/>
[`Table Header/Footer Display`](#table-header-footer-display): Control whether to display the table header and footer.<br/>
[`Auto Complete`](#table-auto-complete): When enabled, it automatically fills in the content according to the data rules.<br/>
[`Max Rows Per Page`](#table-maximum-number-per-page): Set the maximum number of rows displayed per page.<br/>

<div id="table-header-footer-display">
<div style="display: flex;justify-content: left;"><span>1-1 Basic - Table Header/Footer Display</span></div>

![Table_Basic Properties_Table Header/Footer Display](../_images/zh-cn/表格_基础属性_表格头、表格脚显示.gif)
</div>
<br/><br/>

<div id="table-auto-complete">
<div style="display: flex;justify-content: left;"><span>1-2 Basic - Auto Complete</span></div>

![Table_Basic Properties_Auto Complete](../_images/zh-cn/表格_基础属性_自动补全.gif)
</div>
<br/><br/>

<div id="table-maximum-number-per-page">
<div style="display: flex;justify-content: left;"><span>1-3 Basic - Max Rows Per Page</span></div>

![Table_Basic Properties_Max Rows Per Page](../_images/zh-cn/表格_基础属性_每页最大行数.gif)
</div>
<br/><br/>

#### 2. Style Properties

<div id="full-table-font-size">

- [Property Panel](c-overview.md#property-panel)
  - Style
    - `Font`: The font of the table's header and body sections.
    - `Font Size`: The font size of the table's header and body sections.
    - `Font Height`: The font line height of the table's header and body sections.

</div>

![Table_Style Properties_Font](../_images/zh-cn/表格_样式属性_字体.gif)

<div id="full-table-align">

- Property Panel
  - Style
    - `Horizontal Align`: The horizontal alignment of the table's header and body sections.

</div>

![Table_Style Properties_Horizontal Align](../_images/zh-cn/表格_样式属性_左右对齐.gif)

- Property Panel
  - Style
    - `Multi Groups`: Support displaying multiple groups of data in one row.
    - `Multi Groups Spacing`: Set the interval size between multiple groups of data.

![Table_Style Properties_Multiple Groups in One Row](../_images/zh-cn/表格_样式属性_一行多组.gif)

- Property Panel
  - Style
    - `Table Border`: Display/hide the table's outer border.
    - `Header Border`: Display/hide the outer border of the table's header section.
    - `Header Cell Border`: Display/hide the inner border between cells in the table's header section.
    - `Table Border Color`: The color of the table's outer border.
    - `Body Row Border`: Display/hide the outer border of each row in the table's body section.
    - `Body Cell Border`: Display/hide the border of each cell in the table's body section.
    - `Footer Border`: Display/hide the border of the table's footer.
    - `Footer Cell Border`: Display/hide the border of each cell in the table's footer.

![Table_Style Properties_Border](../_images/zh-cn/表格_样式属性_边框.gif)

<span id="header-font-size"></span>

- Property Panel
  - Style
    - `Header Font Color`
    - `Header Font Weight`
    - `Header Font Size`
    - <mark>*Note*</mark>: The header font size setting will override the [`Font Size`](#full-table-font-size) setting.

#### 3. Column Properties

- Property Panel
  - Column
    - `Title`: The title name of the specified column in the table, such as Product Name.
    - `Column Field Name`: The field name of the specified column in the table, such as productName.
    - `Cell Horizontal Align`: The horizontal alignment of the body section of the specified column in the table.
    - `Header Cell Horizontal Align`: The horizontal alignment of the header section of the specified column in the table.
    - `Cell Vertical Align`: The vertical alignment of the header and body sections of the specified column in the table.
    - <mark>*Note*</mark>: The cell horizontal alignment and header cell horizontal alignment settings will override the [`Horizontal Align`](#full-table-align) settings.

- Property Panel
  - Column
    - `Field Type`: The field type of the body section of the specified column in the table, such as text, number, date, etc.
    - `Format`: The field format of the body section of the specified column in the table, such as ￥#,##0.

![Table_Column Properties_Field, Format](../_images/zh-cn/表格_列属性_字段名、格式.gif)

- Property Panel
  - Column
    - `Cell Height`: The cell height of the specified column in the table, applicable to barcodes, QR codes, and images.
    - `Left Padding`: The left padding of the body content of the specified column in the table, minimum value 0.75pt.
    - `Right Padding`: The right padding of the body content of the specified column in the table, minimum value 0.75pt.

![Table_Column Properties_Cell Height, Padding](../_images/zh-cn/表格_列属性_单元格高度、内边距.gif)

- Property Panel
  - Column
    - `Barcode Format`: The barcode format of the specified column in the table, ensuring that each column of data can generate the correct barcode for scanning.
    - `QR ECLevel`: The QR code error correction level of the specified column in the table, used to improve the readability of the QR code when damaged or contaminated, ensuring data reliability.

- Property Panel
  - Column
    - `Footer Aggregate Title`: When set to "Show", the content of the footer aggregate will be displayed in the specified format at the bottom of the table; if set to "Hide", the footer aggregate content will not be displayed.
    - `Footer Aggregate Text`: Define the text description of the aggregate result for the specified column in the table, such as "Total Amount:".
    - `Footer Aggregate Colspan`: Set the number of columns to merge for cross-column aggregate calculations.
    - `Footer Aggregate Type`: Select the aggregate calculation type for the specified column in the table, such as sum, average, etc.
    - `Footer Aggregate Horizontal Align`: Set the alignment of the aggregate result text, such as left, right, etc.
    - `Footer Aggregate Decimal`: Define the number of decimal places to retain in the aggregate result, ensuring data accuracy.

![Table_Column Properties_Footer Aggregate](../_images/zh-cn/表格_列属性_底部聚合.gif)

#### 4. Advanced Properties

`Drag Direction`: Set the dragging direction of the table to meet specific layout needs.<br/>