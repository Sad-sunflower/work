<h5 id="start"></h5>

### Multi-Table Printing

<aside>
💡 The multi-table printing feature allows users to design and print reports with multiple tables, combining different data sources in a single report. Using the report designer, users can easily drag, copy, and adjust tables and assign different datasource fields to meet various printing needs.
</aside>
<br>

#### **Example Explanation:**
Suppose you work in the finance department of an e-commerce company and need to print order details and invoices for each customer. Traditionally, you might need to print orders and invoices separately, but with the multi-table printing feature, you can display both order and invoice information in a single report. This feature is designed for such needs.

#### **1. Open the Designer**

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### **2. Select or Create a Template**

> In the Template Sample, select a template that already contains tables or create a new blank template.

![MultiTable_Printing_Select_Create_Template](../_images/en/MultiTable_Printing_Select_Create_Template.gif)

#### **3. Clone and Adjust Tables**

> Select the table and use the toolbar buttons at the top to clone a new table.

![MultiTable_Printing_Clone_Adjust_Tables](../_images/en/MultiTable_Printing_Clone_Adjust_Tables.gif)

#### **4. Modify Table Column Properties**

> Modify the field properties of the two tables separately to ensure they correspond to different datasource fields, so that different data is displayed during printing.

![MultiTable_Printing_Modify_Table_Column_Properties](../_images/en/MultiTable_Printing_Modify_Table_Column_Properties.gif)

#### **5. Save the Template**

> After completing the design, enter the template name in the upper left corner and click the save button or use the shortcut (Ctrl / Command + S) to save your template.

![MultiTable_Printing_Save_Template](../_images/en/MultiTable_Printing_Save_Template.gif)

#### **6. View and Manage Templates**

> In the Template Tab, change "Recently Viewed (Pinned List)" to "All" to view all saved templates and perform operations such as editing or deleting.

![MultiTable_Printing_View_Manage_Templates](../_images/en/MultiTable_Printing_View_Manage_Templates.gif)

#### **7. Template Data Source Config**

> Refer to [Data Source Config](c-datasourceOverview#start) to configure the datasource for the current template.

#### **8. Preview Print Settings**

> Refer to steps 1-3 in [Document Preview and Printing](ad-print.md#adprint-step1) to configure preview and printing functions.

#### **9. Select Data**

> After completing the preview print settings, select the Salesforce Object you want to print data from (which should be consistent with the Object in the Data Source Config), and select a record to see how it is displayed in the template.

![MultiTable_Printing_Select_Data](../_images/en/MultiTable_Printing_Select_Data.gif)

#### **10. Preview and Print**

> Click the preview print button to display your selected template and data in a new window.<br/>

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not connected, refer to [Print Terminal](download.md).

![MultiTable_Printing_Preview_Print](../_images/en/MultiTable_Printing_Preview_Print.gif)