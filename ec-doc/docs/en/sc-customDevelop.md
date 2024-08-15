<h5 id="start"></h5>

### Advanced Development Applications

<aside>
💡 Developers can extract business object data through custom development, and can choose the fields to be extracted according to actual needs. This flexibility allows developers to customize the data extraction process based on specific business requirements, ensuring that only the necessary data is extracted, avoiding unnecessary data redundancy, and improving the efficiency and accuracy of data processing.
</aside>
<br>

#### **1. Open the Designer**

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### **2. Select or Create a New Template**

> In the template sample, select a template or create a new blank template. Here, we'll use a request form as an example.

<p style="background:grey">TODO->image<br/></p>

#### **3. Save the Template**

> After designing, enter the template name in the upper left corner and click the save button or use the shortcut key (Ctrl / Command + S) to save your template.

![Create99](../_images/zh-cn/Create99.gif)

#### **4. Extract and Create Apex Class Data Model**

> 4.1 Click the "ApexClass Data Model" icon and copy the generated Apex class definition content.

![Create195](../_images/zh-cn/Create195.gif)

> 4.2 In the Salesforce development environment, create a new Apex class and paste the previously copied code into it.

<p style="background:grey">TODO->gif (demonstrating copying, creating class process)<br/></p>

Example code:
```
TODO complete the code
```

#### **5. Generate Apex Class in Action Config**

> In the Action Config Tab, copy the Apex Class code and create a new Apex class for custom development.

![Create196](../_images/zh-cn/Create196.gif)

Example code:

```
TODO complete the code, simplify the code, add comments to help developers understand quickly
```

#### **6. Create Visualforce Page**

> 6.1 Create a new Visualforce Page file in Salesforce.

![Create68](../_images/zh-cn/Create68.gif)

> 6.2 Paste the example code generated in the Action Config into the file and set the extensions attribute to the name of the Apex class you created earlier.

![Create69](../_images/zh-cn/Create69.gif)

Example code:

```
TODO complete the code, simplify the code
```

#### **7. Configure Button**

> 7.1 Add a button in the Salesforce object that needs to be printed.

![Create71](../_images/zh-cn/Create71.gif)

> 7.2 Ensure the button is visible on the object page.

![Create72](../_images/zh-cn/Create72.gif)

#### **8. Preview**

> Click the button to display the selected template in a new window.<br/>

![Create73](../_images/zh-cn/Create73.png)

#### **9. Print**

> Click "print" button to print the template.<br/>

<mark>**Note**</mark>: Before printing, please make sure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

![Create73](../_images/zh-cn/Create73.png)