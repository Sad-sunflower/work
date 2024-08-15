<h5 id="start"></h5>

### Rich Text Content Printing

<aside>
💡 The rich text content printing feature allows you to easily embed rich text content into your print data when designing reports, automatically displaying it in HTML format during print preview. By binding HTML code to the rich text box, the system can automatically parse and display the formats included in the code, such as hyperlinks, italics, colors, etc. When handling HTML data, be sure to replace all double quotes with single quotes or use the placeholder &amp;quot; to avoid parsing conflicts.
</aside>
<br>

#### **Example Explanation:**
Suppose you are designing a template for orders that needs to display order details, including order number, customer information, shipping address, and product list. The product description is crucial, involving bold, italics, colors, and embedded hyperlinks to product pages. Using the rich text content printing feature, you can directly embed HTML-formatted product descriptions into the template, ensuring the best display effect in the print preview. This way, customers can intuitively understand product details and click links to see more information when they receive the printed order.

#### **1. Open the Designer**

> Open the designer via the eDocument DX Tab's Quick Start, New Template Data, or by editing an existing template.

![Create76](../_images/zh-cn/Create76.gif)

#### **2. Create a Template**

> Drag the HTML element onto the panel.

![Create103](../_images/zh-cn/Create103.gif)

#### **3. Set HTML Field Properties**

> Set the HTML field name.

![Create104](../_images/zh-cn/Create104.gif)

#### **4. Enter Template Name and Save Template**

> After completing the design, enter the template name in the upper left corner and click the save button or use the shortcut (Ctrl / Command + S) to save your template.

![Create105](../_images/zh-cn/Create105.gif)

#### **5. View Saved Templates**

> In the Template Tab, change "Recently Viewed (Pinned List)" to "All" to view all saved templates and perform operations such as editing or deleting.

![Create106](../_images/zh-cn/Create106.gif)

#### **6. Preview Print Settings**

> Refer to [Document Preview and Printing](ad-print.md#adprint-step1).

#### **7. Select Data Source**

> After completing the preview print settings, click on the object you want to extract data to the template from (for this demo, Demo01 is used), and select a record to view detailed information. The product description contains the data extracted during the template preview.

![Create107](../_images/zh-cn/Create107.gif)

#### **8. Preview Print**

> Click the preview print button to display your selected template and data in a new window. <br/>

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

![Create108](../_images/zh-cn/Create108.gif)