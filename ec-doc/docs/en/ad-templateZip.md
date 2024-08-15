<h5 id="start"></h5>

### Bulk Download

<aside>
💡 This guide will detail how to achieve the bulk download functionality for Salesforce object lists on our platform.
</aside>
<br>

#### 1. Action Config

> 1.1 Open the application, select "Action Config", and either edit or create new data.

![Bulk Download_Action Config_1.1](../_images/en/bulk_download_action_configuration_1.1.png)

> 1.2 Select a template, check `Show Preview Screen`, and choose "PDF Download" and "ZIP Download" for `Required Functions`.

![Bulk Download_Action Config_1.2](../_images/en/bulk_download_action_configuration_1.2.gif)

#### **2. Create Visualforce Page and Apex Class**

> 2.1 Refer to steps 6 and 8 in [Action Config](c-actionOverview#vf-generate).

#### **3. Configure List View Button**

> 3.1 Add a list button to the Salesforce object list where you want to enable bulk download and ensure that the button is visible on the object list page.

![Bulk Download_Configure List View Button](../_images/en/bulk_download_configure_list_view_button.gif)

#### 4. Bulk Download Operation

> 4.1 In the object list, select the multiple records you want to download and click the button set in the "Action Config".

![Bulk Download_Bulk Download Operation_4.1](../_images/en/bulk_download_bulk_download_operation_4.1.png)

> 4.2 The system will then navigate to the preview page, displaying the content you are about to download.

![Bulk Download_Bulk Download Operation_4.2](../_images/en/bulk_download_bulk_download_operation_4.2.png)

> 4.3 On the preview page, you will see two icons: one for generating a single PDF file (containing template prints for all selected records) and another for generating a ZIP file (containing separate PDF files for each selected record).

- Click the "PDF" icon to print multiple templates into one PDF file and download it.

![Bulk Download_Bulk Download Operation_4.3_pdf](../_images/en/bulk_download_bulk_download_operation_4.3_pdf.gif)

- Click the "PDF ZIP" icon to generate a ZIP file containing individual PDF files for each selected record and download it.

![Bulk Download_Bulk Download Operation_4.3_pdfZip](../_images/en/bulk_download_bulk_download_operation_4.3_pdfZip.gif)

*Choose the appropriate download option based on your needs and save the downloaded file.*
<br/>
<br/>
<br/>