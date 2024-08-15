<h5 id="start"></h5>

*Prerequisites (the following configurations are completed):*<br/>
*1. Cloud/Local Print Service Configuration*<br/>
*2. Template Data Source Config*<br/>
*3. Template Action Config*<br/>

### Document Preview and Printing

<aside>
💡 After completing the Action Config, the system will generate the corresponding Visualforce Page code for you. You only need to create a file in Salesforce and paste the code. Then, add preview and print buttons to your object to view the template and data preview on the screen and perform printing operations.
</aside>
<br>

#### **Example Explanation:**
Assume you are responsible for managing a company's sales orders. You have designed a detailed template for orders, including order number, customer information, product details, and other key information. You want the sales team and customer service team to quickly preview the detailed information of the order when viewing sales order records and directly print it out for internal communication or customer delivery.

<div id="adprint-step1"></div>

#### **1. Configure Buttons**

Ensure the button is visible on the object page.

![Document Preview and Printing_Configure Buttons](../_images/zh-cn/文档预览与打印_配置按钮.gif)

#### **2. Preview**

Click the button, and the selected template will be displayed in a new window.<br/>

![Document Preview and Printing_Preview](../_images/zh-cn/文档预览与打印_预览.gif)

#### **3. Print**

Click "print" button to print the template.<br/>

<mark>**Note**</mark>: Before printing, ensure your device is connected to the print client. If not, refer to [Print Terminal](download.md).

![Document Preview and Printing_Print](../_images/zh-cn/文档预览与打印_打印.png)