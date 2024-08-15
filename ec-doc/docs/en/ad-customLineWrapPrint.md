<h5 id="start"></h5>

### Custom Line Break Printing

<aside>
💡 The custom line break printing feature allows you to flexibly adjust the display of data in a table based on actual content. When the data is too long, this feature can automatically wrap the text to ensure complete display, avoiding data truncation. Additionally, you can customize the settings to hide or omit content in specific columns to better fit the cell size and overall layout.
</aside>
<br>

#### **Example Explanation:**
Suppose you are designing a sales report table that includes customer names, order numbers, product descriptions, and quantities. Since product descriptions can be lengthy, directly printing them might result in truncated content. Using the custom line break printing feature, you can easily set product descriptions to automatically wrap, ensuring complete display while maintaining the table's neatness and readability.

#### **1. Open the Designer**

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### **2. Select or Create a Template**

> In the template sample, choose a template that already includes a table or create a new blank template.

![Custom Line Break Printing_Select or Create Template](../_images/en/custom_line_break_printing_select_or_create_template.gif)

#### **3. Modify Table Properties to Hide Non-Wrapped Content**

> By default, content in table rows is automatically wrapped. If you want to display content without wrapping, you need to modify the table style property to a fixed row height (Note: If you choose fixed, the title row height will be displayed according to the "Body Row Height" setting. Values exceeding this height will be hidden).

![Custom Line Break Printing_Modify Table Properties to Hide Non-Wrapped Content](../_images/en/custom_line_break_printing_modify_table_properties_to_hide_non_wrapped_content.gif)

#### **4. Save the Template**

> After completing the design, enter the template name in the top left corner and click the save button or use the shortcut (Ctrl / Command + S) to save your template.

![Custom Line Break Printing_Save the Template](../_images/en/custom_line_break_printing_save_template.gif)

#### **5. View and Manage Templates**

> In the Template Tab, change the "Recently Viewed (Pinned List)" to "All" to view all saved templates. You can then edit or delete them as needed.

![Custom Line Break Printing_View and Manage Templates](../_images/en/custom_line_break_printing_view_and_manage_templates.gif)

#### **6. Preview and Print Settings**

> Refer to [Document Preview and Printing](ad-print.md#adprint-step1) to configure the preview and print functionality.

#### **7. Select Data**

> After configuring the preview and print settings, select the Salesforce Object from which you want to print data (this must match the main Object in the Data Source Config). Choose a record to see how it appears in the template.

![Custom Line Break Printing_Select Data](../_images/en/custom_line_break_printing_select_data.gif)

#### **8. Preview and Print**

> Click the preview print button to display the selected template and data in a new window.<br/>

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

> Without Line Break:

![Custom Line Break Printing_Preview Print_No Line Break](../_images/en/custom_line_break_printing_preview_print_no_line_break.gif)

> With Line Break:

![Custom Line Break Printing_Preview Print_With Line Break](../_images/en/custom_line_break_printing_preview_print_with_line_break.gif)