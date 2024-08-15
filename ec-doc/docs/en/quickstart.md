#### 1. App Download
*Download the application from the Appexchange market [here](appDownload.md).*

#### 2. User Permission Settings
- Go to Salesforce "Users" -> "Permission Sets" and select "eDocument DX管理者".

![Permission Settings_Permission Sets](../_images/en/Permission-Settings_Permission-Sets.png)

- Select "Manage Assignments".
![Permission Settings_Manage Assignments](../_images/en/Permission-Settings_Manage-Assignments.png)

- Click "Add Assignment".
![Permission Settings_Add Assignments](../_images/en/Permission-Settings_Add-Assignments.png)

- Check the users who need the permissions (users who will use the app), then click "Next".
![Permission Settings_Check Users](../_images/en/Permission-Settings_Check-Users.png)

- Click "Assign", and the setup is complete.
![Permission Settings_Assign](../_images/en/Permission-Settings_Assign.png)

#### 3. Enter the Designer
*Click "Quick Start" or "New" from the homepage to enter the template designer.*
![Quick Start_Enter Designer](../_images/en/Quick-Start_Enter-Designer.png)

#### 4. Switch Language
*Switch your language in the top right corner of the designer.*
![Quick Start_Switch Language](../_images/en/Quick-Start_Switch-Language.png)

#### 5. Select Request Form Template
*5.1 Click the "Template Sample" icon to browse pre-set templates.*
![Quick Start_Select Request Template](../_images/en/Quick-Start_Select-Request-Template.png)

*5.2 Select "サンプル請求書01" form template and click confirm.*
![Quick Start_Select Request Template Confirm](../_images/en/Quick-Start_Select-Request-Template-Confirm.png)

#### 6. Customize and Modify Template
*Edit and customize the selected template, such as adding an aggregation function to the table's amount column to calculate the average value.*
![Quick Start_Customize Template](../_images/en/Quick-Start_Customize-Template.png)

#### 7. Preview Print Effect
*7.1 Click "Preview" icon to see the print effect of the template.*
![Quick Start_Preview Print Effect 7.1](../_images/en/Quick-Start_Preview-Print-Effect-7.1.png)

*7.2 In preview mode, you can directly export as a PDF file or print directly in the browser. The templates provided in the template sample contain test data for convenient previewing.*
![Quick Start_Preview Print Effect 7.2](../_images/en/Quick-Start_Preview-Print-Effect-7.2.png)

#### 8. Save Template
*Name the template and click "Save" icon.*
![Quick Start_Save Template](../_images/en/Quick-Start_Save-Template.png)

#### 9. Set Template Data
*9.1 Click the "Data Source Config" tab and click the "New" button.*
![Quick Start_Set Template Data 9.1](../_images/en/Quick-Start_Set-Template-Data-9.1.png)

*9.2 Select the main object you want the template to bind to, such as order information for a request form.*
![Quick Start_Set Template Data 9.2](../_images/en/Quick-Start_Set-Template-Data-9.2.png)

*9.3 Select the child (related) objects the template will bind to, such as product information under the order for a request form.*
![Quick Start_Set Template Data 9.3](../_images/en/Quick-Start_Set-Template-Data-9.3.png)

*9.4 Choose the template created in step 6.*
![Quick Start_Set Template Data 9.4](../_images/en/Quick-Start_Set-Template-Data-9.4.png)

*9.5 Drag the object fields to the corresponding template fields to map them, then click save. The template is now bound to the data.*
![Quick Start_Set Template Data 9.5](../_images/en/Quick-Start_Set-Template-Data-9.5.png)

#### 10. Create Print Service Setting
Refer to [Cloud Print Service](sc-cloudPrint.md#start) for cloud printing configuration.
Refer to [Local Print Service](sc-localPrint.md#start) for local printing configuration.

#### 11. Create Action Config
*11.1 Click the "Action Config" tab and click the "New" button.*
![Quick Start_Create Action Config 11.1](../_images/en/Quick-Start_Create-Action-Config-11.1.png)

*11.2 Add configuration information and click the "Save" button. [For configuration details, see Action Config](c-actionOverview.md#start)*

![Quick Start_Create Action Config 11.2](../_images/en/Quick-Start_Create-Action-Config-11.2.png)

*11.3 After completing the settings, the system will generate sample code for you.*
![Quick Start_Create Action Config 11.3](../_images/en/Quick-Start_Create-Action-Config-11.3.gif)

#### 12. Create Visualforce Page

*12.1 Create a new Visualforce Page file in Salesforce.*
![Quick Start_Create VF Page 12.1](../_images/en/Quick-Start_Create-VF-Page-12.1.gif)

*12.2 Create a new preview button in the object.*
![Quick Start_Create Preview Button 12.2](../_images/en/Quick-Start_Create-Preview-Button-12.2.gif)

*12.3 Create a new Apex Class file in Salesforce.*
![Quick Start_Create Apex Class 12.3](../_images/en/Quick-Start_Create-Apex-Class-12.3.gif)

#### 13. Preview Print Settings

*Ensure the button is visible on the object page.*

![Quick Start_Preview Print Settings](../_images/en/Quick-Start_Preview-Print-Settings.gif)

#### 14. Preview

*Click the "Order Print" button to display the selected template in a new window.*

![Quick Start_Preview](../_images/en/Quick-Start_Preview.gif)

#### 15. Print

*Click "print" button to print the template.*

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

![Quick Start_Print](../_images/en/Quick-Start_Print.png)