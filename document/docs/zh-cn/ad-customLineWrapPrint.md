<h5 id="start"></h5>

### 自定义换行打印

<aside>
💡 自定义换行打印功能允许您根据表格中数据的实际情况，灵活地调整数据的展示方式。当数据内容过长时，该功能可以自动将其换行，确保完整显示，避免数据截断。同时，您还可以自定义设置隐藏或省略特定列的内容，以更好地适应单元格的大小和整体布局。
</aside>
<br>

#### **实例说明：**
假设，您正在设计一个销售情况的表格，其中包含客户名称、订单号、产品描述和数量。由于产品描述包含大量文字，如果直接打印会导致内容被截断。使用自定义换行打印功能，您可以轻松地将产品描述设置为自动换行，确保完整显示，同时保持表格的整洁和易读性。

#### **1. 打开设计器**

> 通过eDocument DX Tab的快速开始或新建模板数据的方式打开设计器。

#### **2. 选择或新建模板**

> 在模板中心中，选择一个已包含表格的模板或新建一个空白模板。

![内容换行定制_选择或新建模板](../_images/zh-cn/内容换行定制_选择或新建模板.gif)

#### **3. 修改表格属性实现不换行隐藏**

> 表格行中的内容默认是自动换行，如果想要不换行显示需要将表格样式属性中的固定行高修改为固定（注：如果选择固定那么表格的标题行高会根据“表体行高”设定的高度显示，超出这个高度的值会隐藏）。

![内容换行定制_修改表格属性实现不换行隐藏](../_images/zh-cn/内容换行定制_修改表格属性实现不换行隐藏.gif)

#### **4. 保存模板**

> 完成设计后，在左上角输入模板名称，并点击保存按钮或使用快捷键(Ctrl / Command + S)保存您的模板。

![内容换行定制_保存模板](../_images/zh-cn/内容换行定制_保存模板.gif)

#### **5. 查看和管理模板**

> 在模板Tab中，您可以将"最近查看的数据（固定列表）"修改为"全选"后即可查看所有保存的模板，并进行编辑或删除等操作。

![内容换行定制_查看和管理模板](../_images/zh-cn/内容换行定制_查看和管理模板.gif)

#### **6. 预览打印设置**

> 请参照[文档预览与打印](ad-print.md#adprint-step1)配置预览和打印功能。

#### **7. 选择数据**

> 预览打印设置完成后，选择您想要打印数据的Salesforce Object（需要和数据源配置中的主Object一致），选择一条记录以查看其在模板中的展示效果。

![内容换行定制_选择数据](../_images/zh-cn/内容换行定制_选择数据.gif)

#### **8. 预览打印**

> 点击预览打印按钮，将在新窗口中展示您所选的模板和数据。<br/>

<mark>**注意**</mark>：进行打印前，请确保您的设备已连接打印客户端。如没有连接请参考[打印终端](download.md)。

> 不换行：
 
![内容换行定制_预览打印_不换行](../_images/zh-cn/内容换行定制_预览打印_不换行.gif)

> 换行：

![内容换行定制_预览打印_换行](../_images/zh-cn/内容换行定制_预览打印_换行.gif)