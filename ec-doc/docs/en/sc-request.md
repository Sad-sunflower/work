### Request Form

<aside>
💡 Designing a high-quality request form requires following a series of carefully planned steps. Below is a detailed guide to help you efficiently and professionally complete the design of your request form.
</aside>
<br>

#### **I. Open the Designer**

Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

![Create118](../_images/zh-cn/Create118.gif)

#### **II. Select a Template**

Select the request form template from the template sample and click OK to load it into the designer.

![Create119](../_images/zh-cn/Create119.gif)

<h4 id="step3"></h4>

#### **III. Edit and Optimize**
> (A) Adjust the Overall Layout

> **1. Font:**

Choose an appropriate global font based on your needs. You can also select [custom fonts](ad-customFont.md#start) to meet special requirements.

![Create122](../_images/zh-cn/Create122.gif)

> **2. Page Number Format:**
Customize the format for displaying page numbers as needed, such as `${paperNo}-${paperCount}页`.

![Create123](../_images/zh-cn/Create123.gif)

> (B) Adjust Text Elements

> **1. Data Type and Format:**

- Specify the data type for text elements and choose an appropriate format as needed.
- The designer provides a variety of data formats, and you can also input custom data formats to meet special requirements.

![Create128](../_images/zh-cn/Create128.gif)

> **2. Font:**

Adjust the font size, weight, color, and letter spacing to enhance the readability and aesthetics of the text.

![Create129](../_images/zh-cn/Create129.gif)

> (C) Adjust Table Elements

> **1. Field:**

- Field names are used to connect with fields in the data source.
- After setting the field names, you can input sample data in the test data to ensure that the table data is correctly displayed during preview.
- <mark>**Note**</mark>: The test data for the table should be in JSON format.

![Create135](../_images/zh-cn/Create135.gif)

> **2. Background and Border Colors:**

Set the colors for the table header, body odd and even rows, and table borders to enhance visual effects.

![Create137](../_images/zh-cn/Create137.gif)

> **3. Border Style:**

You can set the row borders and cell borders of the table body to be dashed. Setting the row borders will display the internal row borders of the table body as dashed lines, while setting the cell borders will display the internal column borders of the table body as dashed lines.

![Create139](../_images/zh-cn/Create139.gif)

> (D) Adjust Table Column Elements

> **1. Field Types:**

You can set the appropriate field types for the cells, including: text, number, date/time, serial number, barcode, QR code, and image. Additionally, for different types, you can set corresponding formatting methods. For example, for numbers and date/time, you can choose existing formats or input custom formats.

- Serial number, text:

![Create143](../_images/zh-cn/Create143.gif)

- Number, date/time:

![Create144](../_images/zh-cn/Create144.gif)

- Barcode, QR code:

![Create145](../_images/zh-cn/Create145.gif)

- Image:

![Create146](../_images/zh-cn/Create146.gif)

> **2. Cell Height:**

When the table contains special column types (such as QR code, barcode, image), you can separately set the cell height for these columns. Once set, the QR code, barcode, and image will be displayed according to the cell height you set.
- <mark>**Note**</mark>: To ensure QR codes and barcodes are centered, the cell height should be less than the table body row height.

![Create147](../_images/zh-cn/Create147.gif)

> **3. Bottom Aggregation Settings:**

- Bottom Aggregation Title: When "Show" is selected, the bottom aggregation content will be displayed below the table.
- Bottom Aggregation Text: Defines the text description of the aggregation result for a specified column in the table, such as "Average:", to help users quickly understand the meaning of the aggregation result.
- Bottom Aggregation Merge Columns: Determines how many columns to merge from the current column to display the aggregation result.
- Bottom Aggregation Type: Select the aggregation calculation type for a specified column in the table, such as sum, average, etc., to meet different statistical needs.
- Bottom Aggregation Alignment: Set the text alignment of the aggregation result, such as left, right, etc.
- Bottom Aggregation Decimal Places: Set the number of decimal places to retain in the aggregation result as needed, ensuring data accuracy and readability.

![Create149](../_images/zh-cn/Create149.gif)

![Create150](../_images/zh-cn/Create150.gif)

<h4 id="step4"></h4>

#### **IV. Designer Preview and Save**

> **1. View JSON Data Model:**

- Click the "View JSON Data Model" button to view the JSON mapping of field names in the template.
- Paste the data (in JSON format) into "Edit Print Data" and click "Preview" to see the actual effect.

<p style="background:grey">TODO->gif<br/></p>

> **2. Save the Template:**

Enter the template name in the upper left corner and click the "Save" button to save the current template.

![Create153](../_images/zh-cn/Create153.gif)

<h4 id="step5"></h4>

#### **V. Actual Preview, Print, and Export PDF**

> **1. Data Model Extraction**

1.1 Click the "View Apex Class Data Model" button to display the Apex class code of the fields in the template.

![Create199](../_images/zh-cn/Create199.gif)

1.2 Create a new Apex Class file in Salesforce and paste the code copied from step 1.1 into the file to store data models related to the template.

<p style="background:grey">TODO->gif<br/></p>

> **2. Data Source Config**

2.1 Open the application, select "Data Source Settings", and click the "New" button.

<p style="background:grey">TODO->gif<br/></p>

2.2 First, set the main object, which is usually the main or core data. Then, set the sub-objects as needed, which are secondary data associated with the main object.

<p style="background:grey">TODO->gif<br/></p>

2.3 Select the request form template saved previously in the designer.

<p style="background:grey">TODO->gif<br/></p>

2.4 Map the fields from the data source to the fields in the template.

<p style="background:grey">TODO->gif<br/></p>

2.5 Click "Save and Jump to Design Page" and click "Preview" on the designer page to view the effect of the successfully bound data source.

<p style="background:grey">TODO->gif<br/></p>

> **3. Action Config**

3.1 Open the application, select "Action Config", and click the "New" button.

![Create65](../_images/zh-cn/Create65.gif)

3.2 Set the information:
- Template Name: Choose the template from **IV. Designer Preview and Save** -> Step 2.
- Check "Show Preview Content" in the "Function to Use" section.
- Select "Printer Print" and "PDF Download" in the function to use.
- Enter the Apex class name information.

![Create155](../_images/zh-cn/Create155.gif)

3.3 Click "Save", and the system will generate sample codes for Apex Class and Visualforce Page.

![Create67](../_images/zh-cn/Create67.gif)

> **4. Create Visualforce Page**

4.1 Create a new Visualforce Page file in Salesforce.

![Create68](../_images/zh-cn/Create68.gif)

4.2 Paste the Visualforce Page code generated in step 2.3 into the file.

![Create69](../_images/zh-cn/Create69.gif)

4.3 Visualforce Page: Set the standardcontroller in the code to the API name of the object extracting data and set extensions to the name of the

 Apex Class from step 4.1.

![Create157](../_images/zh-cn/Create157.gif)

> **5. Configure Preview Button**

5.1 Add a button in the Salesforce object that needs to be printed.

![Create71](../_images/zh-cn/Create71.gif)

5.2 Ensure the button is visible on the object page.

![Create72](../_images/zh-cn/Create72.gif)

> **6. Preview and Operate**

6.1 On the detailed data page of the business object, click the preview button.

![Create158](../_images/zh-cn/Create158.gif)

6.2 View the template preview with data to ensure the data is displayed correctly.

![Create159](../_images/zh-cn/Create159.gif)

6.3 Click the "print" button to print the template along with the data (make sure the print client is connected).
- <mark>**Note**</mark>: Printing requires the print client to be connected. If not connected, refer to [Print Terminal](download.md).

6.4 Click the "PDF" button to export the template and data as a PDF file.

<p style="background:grey">TODO->gif<br/></p>