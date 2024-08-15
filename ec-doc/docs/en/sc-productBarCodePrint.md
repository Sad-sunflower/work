<h5 id="start"></h5>

### Product BARCODE Printing

<aside>
💡 The product barcode (BARCODE) printing function allows users to select multiple records from the list view for batch preview, printing, and PDF export. This function significantly enhances efficiency and convenience when handling a large number of product barcodes.
</aside>
<br>

#### **1. Open the Designer**

Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

![Create185](../_images/zh-cn/Create185.gif)

#### **2. Create a Product Barcode Template**

2.1 In the designer, add a barcode element and a text element. Set the basic properties, font, size, and position of the barcode element and text element.

![Create198](../_images/zh-cn/Create198.gif)

2.2 Add field name information to the barcode element and text element. You can input sample data in the test data to ensure that the data is correctly displayed during preview.

<p style="background:grey">TODO->gif<br/></p>

2.3 Name the template and click the "Save" icon.

<p style="background:grey">TODO->gif<br/></p>

#### **3. Extract Data Model**

3.1 Click the "View Apex Class Data Model" button to display the Apex class code of the fields in the template.

![Create199](../_images/zh-cn/Create199.gif)

3.2 Create a new Apex Class file in Salesforce and paste the code copied from step 3.1 into the file to store data models related to the template.

<p style="background:grey">TODO->gif<br/></p>

#### **4. Data Source Config**

4.1 Open the application, select "Data Source Settings", and click the "New" button.

<p style="background:grey">TODO->gif<br/></p>

4.2 First, set the main object, which is usually the main or core data. Then, set the sub-objects as needed, which are secondary data associated with the main object.

<p style="background:grey">TODO->gif<br/></p>

4.3 Select the previously saved product barcode template in the designer.

<p style="background:grey">TODO->gif<br/></p>

4.4 Map the fields from the data source to the fields in the template.

<p style="background:grey">TODO->gif<br/></p>

4.5 Click "Save and Jump to Design Page" and click "Preview" on the designer page to view the effect of the successfully bound data source.

<p style="background:grey">TODO->gif<br/></p>

#### **5. Configure Action**

5.1 Open the application, select the "Action Config" option, and click the "New" button.

<p style="background:grey">TODO->image<br/></p>

5.2 Set the information:
- Template Name: Choose the template from Step 2.3．
- Button Type: Select list view button.
- Check "Show Preview Content" in the "Function to Use" section.
- Select "Printer Print" and "PDF Download" in the function to use.
- Enter the Apex class name information.

<p style="background:grey">TODO->image<br/></p>

5.3 Click "Save", and the system will generate sample codes for Apex Class and Visualforce Page.

<p style="background:grey">TODO->image<br/></p>

#### **6. Create Visualforce Page**

6.1 Create a new Visualforce Page file in Salesforce.

![Create68](../_images/zh-cn/Create68.gif)

6.2 Paste the sample code generated in step 2.3 into the file.

![Create69](../_images/zh-cn/Create69.gif)

6.3 Visualforce Page: Set the standardcontroller in the code to the API name of the object extracting data and set extensions to the name of the Apex Class from step 6.1.

![Create157](../_images/zh-cn/Create157.gif)

#### **7. Configure Preview Button**

7.1 Add a button in the Salesforce object that needs to be printed.

![Create71](../_images/zh-cn/Create71.gif)

7.2 Ensure the button is visible on the object page.

![Create72](../_images/zh-cn/Create72.gif)

#### **8. Preview and Operate**

8.1 On the detailed data page of the business object, click the preview button.

![Create158](../_images/zh-cn/Create158.gif)

8.2 View the template preview with data to ensure the data is displayed correctly.

![Create159](../_images/zh-cn/Create159.gif)

8.3 Click the "print" button to print the template along with the data (make sure the print client is connected).
- <mark>**Note**</mark>: Printing requires the print client to be connected. If not connected, refer to [Print Terminal](download.md).

8.4 Click the "PDF" button to export the template and data as a PDF file.

<p style="background:grey">TODO->gif<br/></p>