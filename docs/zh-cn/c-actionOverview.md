<h5 id="start"></h5>

*前提条件(以下配置已完成)：*<br/>
*1. 云/本地打印服务配置*<br/>
*2. 模版的数据源设定*<br/>

### 界面布局
① [基本信息](#basic-information)
② [模板设置](#template-setting)
③ [功能设置](#functional-setting)
④ [打印设置](#print-setting)
⑤ [回调](#callback)
⑥ [vf代码生成](#vf-generate)
⑦ [按钮生成](#button-generate)
⑧ [apex class生成](#apex-generate)

![Action配置_属性说明](../_images/zh-cn/Action配置_属性说明.png)
<br/>
<br/>
<br/>

<h5 id="basic-information">
① 基本信息
</h5>

`Action名称`：输入当前action的名称，以便保存和识别。

![Action配置_基本信息](../_images/zh-cn/Action配置_基本信息.png)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="template-setting">
② 模板设置
</h5>

`模板选择`：根据您的需求，选择并配置多个模板。模板将按照您设定的顺序（模板1→模板2→模板3→模板4→模板5）在打印时依次显示。例如，模板1选择[封面]模板，模板2选择[订单]模板，模板3选择[发货信息]模板。<br/>
<mark>**注意：如果配置多个模板数据源需要保持一致并且多个模板纸张大小应一致。如果选择的模板没有配置数据源则无法进行下一步操作。**</mark><br/>
`模板概要`：显示每个模板的数据源、纸张方向、纸张类型信息，帮助您快速了解模板的设置情况。<br/>
`数据源主对象`：指定模板1~5读取数据的主对象，例如"订单"。这将确保模板能够正确展示与主对象相关的数据。<br/>
<mark>**注意：数据源的主对象是固定的，不能更改。只能从数据源中获取指定的主对象作为数据源主对象。**</mark>

![Action配置_模板设置](../_images/zh-cn/Action配置_模板设置.png)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="functional-setting">
③ 功能设置
</h5>

`按钮类型`：选择按钮的显示位置。显示在列表或详细页面上。<br/>
`列表视图打印`：如果`按钮类型`选择列表按钮时，将会显示此属性。启用此功能后，您可以方便地将选中的记录字段及其对应的值以表格形式打印出来。勾选时，预览打印效果如下图。<br/>
![Action配置_功能设置_列表打印视图](../_images/zh-cn/Action配置_功能设置_列表打印视图.gif)

`PDF名动态设置`：勾选后，可根据数据源主对象的字段名来动态设置PDF的文件名。不勾选则使用默认名。<br/>
`PDF名`：输入数据源主对象的字段名，仅支持单一字段。如"Name"，PDF名将与该字段值相同。效果如下图。<br/>
![Action配置_功能设置_PDF名动态设置](../_images/zh-cn/Action配置_功能设置_PDF名动态设置.gif)

`下载或打印时保存`：勾选后，生成的PDF文件将自动保存到Salesforce的ContentFile（内容文件）中，方便后续管理和检索。<br/>
`显示预览画面`：勾选后，在下载/打印前将显示预览画面，允许用户先查看PDF文件的布局和内容。<br/>
`要使用的功能`：`显示预览画面`勾选时，功能允许多选，以满足不同的预览需求。不预览时，只能选一个功能。<br/>

`勾选显示预览画面`：
![Action配置_功能设置_显示预览画面_勾选](../_images/zh-cn/Action配置_功能设置_显示预览画面_勾选.gif)

`未勾选显示预览画面`：
![Action配置_功能设置_显示预览画面_不勾选](../_images/zh-cn/Action配置_功能设置_显示预览画面_不勾选.gif)

`ZIP文件名`：批量下载时自定义压缩包名；不填则默认。<br/>
`Apex类名`：输入类名，系统生成Apex代码，为高级用户提供[高级开发应用](sc-customDevelop.md)。<br/>
<mark>**注意：Apex类名唯一不可以重复。**</mark>

![Action配置_功能设置](../_images/zh-cn/Action配置_功能设置.png)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="print-setting">
④ 打印设置
</h5>

`打印服务设置`：在此处输入您想要连接的[云打印服务](sc-cloudPrint.md#start)或[本地打印服务](sc-localPrint.md#start)的名称。这允许您指定与您的系统集成的特定打印服务。<br/>
`设备编号`：根据您在"打印服务设置"中选择的打印服务，输入对应的设备编号。设备编号通常用于唯一标识打印服务中的特定打印机或打印队列。<br/>

<mark>**注意**</mark>：请确保您已经正确配置了打印服务和设备编号，以确保打印功能能够正常工作。
![Action配置_打印设置](../_images/zh-cn/Action配置_打印设置.png)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="callback">
⑤ 回调操作
</h5>
输入模板的数据源主对象的一个布尔类型字段，一旦打印操作成功完成，系统将自动将该字段的值设置为True，以标记或记录打印状态。

![Action配置_回调操作](../_images/zh-cn/Action配置_回调操作.png)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="vf-generate">
⑥ vf代码生成
</h5>
完成①至⑤的Action配置设定后，点击保存按钮，系统将在⑥区域自动为您生成新的Visualforce Page（VF）文件。这个文件将包含基于您配置的功能所需的VF代码，使得您可以轻松地集成到您的Salesforce应用中。

![Action配置_VFPage代码生成](../_images/zh-cn/Action配置_VFPage代码生成.gif)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="button-generate">
⑦ 按钮生成
</h5>

此区域提供了添加按钮的详细指南。按照提供的步骤，您可以在Salesforce对象中添加一个自定义按钮，并将该按钮与⑥中生成的Visualforce Page文件相关联。这样，当用户点击该按钮时，将触发并执行您在Action配置中设定的功能。

![Action配置_按钮生成](../_images/zh-cn/Action配置_按钮生成.gif)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>

<h5 id="apex-generate">
⑧ apex class生成
</h5>

Apex类生成功能旨在支持高级定制开发需求，允许开发人员生成[自定义Apex类](sc-customDevelop.md)以定义模板数据源。这一功能为开发人员提供了灵活性，使他们能够根据自己的业务需求，通过设定特定的数据源属性（如dataSource、dataSourcePlus、zipDataSource）来定制和增强Action配置的功能。

> dataSource：当设置此属性时，模板将直接从指定的数据源中读取数据。<br/>
> dataSourcePlus：当启用此属性并设置值时，模板将把dataSourcePlus中的字段值追加到数据源中，从而扩展数据源的内容。<br/>
> zipDataSource：当需要下载压缩包时，设置此属性将使模板从指定的zipDataSource中读取数据，以便在压缩包中包含相关的数据源信息。<br/>

![Action配置_ApexClass生成](../_images/zh-cn/Action配置_ApexClass生成.gif)

[↑ 回到顶部](#start)
<br/>
<br/>
<br/>