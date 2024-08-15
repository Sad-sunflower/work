<h5 id="start"></h5>

### Multi-Template Printing

<aside>
💡 The multiple template printing feature helps you manage various templates and use a unified data source for preview and printing. You can select multiple designed templates that share the same data source. During the preview, the system automatically extracts data source information and populates it into each template, ensuring the printing results meet expectations.
</aside>
<br>

#### **Example Explanation:**
Suppose you are a customer service representative at an e-commerce company. When a customer places an order, you need to print both a detailed order receipt and a brief shipping notice. Using the multiple template printing feature, you can select the two pre-designed templates (one for the order receipt and one for the shipping notice) and use the order data as the data source. The system will automatically fill in the data into these templates, allowing you to print both reports at once.

#### **1. Print Operation Settings**

> 1.1 After opening the application, view the list of created templates. If you already have multiple templates, proceed to the next step; otherwise, create multiple templates first.

![Multi-template Printing_Print Operation Settings_1.1](../_images/en/multi-template_printing_1.1.png)

> 1.2 After selecting or creating templates, go to the "Action Config" interface, and select or create a new data record.

![Multi-template Printing_Print Operation Settings_1.2](../_images/en/multi-template_printing_1.2.png)

> 1.3 After opening a data record for editing, you can modify the print operation settings, select two different templates, and save the changes (the data source for multiple templates needs to be consistent).

![Multi-template Printing_Print Operation Settings_1.3](../_images/en/multi-template_printing_1.3.gif)

#### **2. Preview Print Settings**

> Refer to [Document Preview and Printing](ad-print.md#adprint-step1) to configure the preview and print functionality.

#### **3. Select Data**

> After completing the preview print settings, select the Salesforce Object from which you want to print data (this should be consistent with the main object in the Data Source Config), and select a record to view its display effect in the templates.

![Multi-template Printing_Select Data](../_images/en/multi-template_printing_select_data.gif)

#### **4. Preview Print**

> Click the preview print button to display the selected templates and data in a new window.<br/>

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

![Multi-template Printing_Preview Print](../_images/en/multi-template_printing_preview_print.gif)