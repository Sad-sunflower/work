<h5 id="start"></h5>

*Prerequisites (the following configurations are completed):*<br/>
*1. Cloud/Local Print Service Configuration*<br/>
*2. Template Datasource Setup*<br/>

### Interface Layout
① [Basic Information](#basic-information)  
② [Template Settings](#template-setting)  
③ [Functional Settings](#functional-setting)  
④ [Print Settings](#print-setting)  
⑤ [Callback](#callback)  
⑥ [VF Code Generation](#vf-generate)  
⑦ [Button Generation](#button-generate)  
⑧ [Apex Class Generation](#apex-generate)  

![Action Config_Property Description](../_images/zh-cn/Action配置_属性说明.png)
<br/>
<br/>
<br/>

<h5 id="basic-information">
① Basic Information
</h5>

`Action Name`: Enter the name of the current action for saving and identification.

![Action Config_Basic Information](../_images/zh-cn/Action配置_基本信息.png)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="template-setting">
② Template Settings
</h5>

`Template Selection`: Choose and configure multiple templates according to your needs. Templates will be displayed sequentially during printing in the order you set (Template 1→Template 2→Template 3→Template 4→Template 5). For example, select the [Cover] template for Template 1, the [Order] template for Template 2, and the [Shipping Information] template for Template 3. <br/>
`Summary of Template`: Displays the datasource, paper orientation, and paper type information for each template, helping you quickly understand the template settings. <br/>
`Data Source Main Object`: Specify the main object for Templates 1~5 to read data from, such as "Order". This ensures that the templates can correctly display data related to the main object.

![Action Config_Template Settings](../_images/zh-cn/Action配置_模板设置.png)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="functional-setting">
③ Functional Settings
</h5>

`Button Type`: Choose where the button will be displayed. It can be shown on the list or detail page. <br/>
`For List View Print`: If `Button Type` is set to list button, this property will be displayed. Enabling this feature allows you to print the selected record fields and their corresponding values in a table format. When checked, the print preview effect is shown as below. <br/>
![Action Config_Functional Settings_For List View Print](../_images/zh-cn/Action配置_功能设置_列表打印视图.gif)

`Dynamic Setting of PDF Name`: When checked, you can dynamically set the PDF file name based on the field name of the datasource main object. If not checked, the default name will be used. <br/>
`PDF Name`: Enter the field name of the datasource main object, only single fields are supported. For example, "Name" will set the PDF name to be the same as the value of this field. The effect is shown as below. <br/>
![Action Config_Functional Settings_Dynamic Setting of PDF Name](../_images/zh-cn/Action配置_功能设置_PDF名动态设置.gif)

`Save PDF when Download or Print`: When checked, the generated PDF file will be automatically saved to Salesforce's ContentFile for easy subsequent management and retrieval. <br/>
`Show Preview Screen`: When checked, a preview screen will be displayed before downloading/printing, allowing users to review the layout and content of the PDF file first. <br/>
`Required Functions`: When `Show Preview Screen` is checked, multiple features can be selected to meet different preview needs. When not previewing, only one feature can be selected. <br/>

`Checked Show Preview Screen`:  
![Action Config_Functional Settings_Show Preview Screen_Checked](../_images/zh-cn/Action配置_功能设置_显示预览画面_勾选.gif)

`Unchecked Show Preview Screen`:  
![Action Config_Functional Settings_Show Preview Screen_Unchecked](../_images/zh-cn/Action配置_功能设置_显示预览画面_不勾选.gif)

`ZIP File Name`: Customize the name of the compressed package when downloading in bulk; leave blank for default. <br/>
`Apex Class Name`: Enter the class name, and the system will generate Apex code, providing advanced users with [Advanced Development Applications](sc-customDevelop.md). <br/>

![Action Config_Functional Settings](../_images/zh-cn/Action配置_功能设置.png)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="print-setting">
④ Print Settings
</h5>

`Print Service Setting`: Enter the name of the [Cloud Print Service](sc-cloudPrint.md#start) or [Local Print Service](sc-localPrint.md#start) you want to connect to. This allows you to specify the specific print service integrated with your system. <br/>
`Client Id`: Enter the corresponding Client Id according to the print service you selected in "Print Service Setting". The Client Id is usually used to uniquely identify a specific printer or print queue in the print service. <br/>

<mark>**Note**</mark> : Ensure that you have correctly configured the print service and Client Id to ensure the print function works properly. 
![Action Config_Print Settings](../_images/zh-cn/Action配置_打印设置.png)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="callback">
⑤ Callback
</h5>
Enter a boolean field of the datasource main object. Once the print operation is successfully completed, the system will automatically set the value of this field to True to mark or record the print status.

![Action Config_Callback](../_images/zh-cn/Action配置_回调操作.png)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="vf-generate">
⑥ VF Code Generation
</h5>
After completing the Action Config settings from ① to ⑤, click the save button. The system will automatically generate a new Visualforce Page (VF) file in area ⑥. This file will contain the VF code required based on your configured features, allowing you to easily integrate it into your Salesforce application.

![Action Config_VF Page Code Generation](../_images/zh-cn/Action配置_VFPage代码生成.gif)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="button-generate">
⑦ Button Generation
</h5>

This area provides a detailed guide for adding a button. Follow the provided steps to add a custom button to the Salesforce object and associate it with the Visualforce Page file generated in ⑥. This way, when users click the button, it will trigger and execute the functions you set in the Action Config.

![Action Config_Button Generation](../_images/zh-cn/Action配置_按钮生成.gif)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>

<h5 id="apex-generate">
⑧ Apex Class Generation
</h5>

The Apex class generation function aims to support advanced customization development needs, allowing developers to generate [custom Apex classes](sc-customDevelop.md) to define template datasources. This feature provides developers with the flexibility to customize and enhance the functionality of Action Config by setting specific datasource properties (such as dataSource, dataSourcePlus, zipDataSource).

> dataSource: When this property is set, the template will directly read data from the specified datasource. <br/>
> dataSourcePlus: When this property is enabled and set, the template will add the field values in dataSourcePlus to the datasource, thus expanding the content of the datasource. <br/>
> zipDataSource: When a compressed package needs to be downloaded, setting this property will allow the template to read data from the specified zipDataSource, so that related datasource information is included in the compressed package. <br/>

![Action Config_Apex Class Generation](../_images/zh-cn/Action配置_ApexClass生成.gif)

[↑ Back to Top](#start)
<br/>
<br/>
<br/>