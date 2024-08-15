<h5 id="start"></h5>

*Prerequisite: The template is complete, and the field properties in the template are set.*<br/>
*Data Source Config allows users to associate Salesforce objects with templates, ensuring that the data in the templates can be dynamically updated. Below is a detailed introduction to the main functional areas and operations of Data Source Config.*

> #### Selecting the main object
##### Function Description<br/>
Selecting the main object is the first step in Data Source Config, helping users define the primary data source for the template. You can choose the object in Salesforce that is most relevant to the template, such as "Order". <br/>

##### User Guide<br/>
![Data Source Config_Main Object Selection](../_images/zh-cn/数据源设定_主对象选择.png)

<h5>① Comment</h5>
Enter a description to distinguish different Data Source Config objects.

<h5>② Search Box</h5>
Used to quickly search for the required object name.

<h5>③ Select Main Object</h5>
Select the Salesforce object most relevant to the template from the list.

<h5>④ Sort Order</h5>
If the Salesforce object is bound to a table, multiple data entries will be displayed. You can specify the display order of the data here to ensure logical and readable data presentation.
<br/>
<br/>
<br/>

> #### Selecting child (related) objects
##### Function Description<br/>
The child object selection feature allows you to further extend the data source of the template. In some cases, the template may need to retrieve data from child objects related to the main object. For example, if the main object is "Order", you might also want to include "Order Details" associated with the order in the template. In this area, you can select these child objects to incorporate the relevant data into the template.

##### User Guide<br/>
![Data Source Config_Child Object Selection](../_images/zh-cn/数据源设定_子对象选择.png)

<h5>① Search Box</h5>
Used to quickly search for the required object name.

<h5>② Select Child Object</h5>
Select the child object related to the main object from the list.

<h5>③ Condition Requirements</h5>
Set data filtering criteria to further screen and limit the data displayed in the template. This helps ensure that only the data you care about is displayed in the template, enhancing the specificity and accuracy of data presentation.

<h5>④ Sort Order</h5>
If the Salesforce object is bound to a table, multiple data entries will be displayed. You can specify the display order of the data here to ensure logical and readable data presentation.

<h5>⑤ List of Conditions</h5>
Displays data filtering criteria and data sorting rules.
<br/>
<br/>
<br/>

> #### Selecting template
##### Function Description<br/>
In the template selection area, you can choose a template from the list of saved templates to associate it with the selected main object and child objects. This ensures that when you retrieve data from Salesforce, it will be displayed in the format specified by the template. After selecting a template, you can further edit and customize it to meet your specific needs.

##### User Guide<br/>
![Data Source Config_Template Selection](../_images/zh-cn/数据源设定_模板选择.png)

<h5>① Search Box</h5>
Used to quickly search for the required template name.

<h5>② Select Template List</h5>
Select the template from the list.

<h5>③ Create New Template</h5>
Create a new template without using an existing one.
<br/>
<br/>
<br/>

> #### Setting up the mapping
##### Function Description<br/>
Field mapping is a key step in Data Source Config. In this area, you need to match the fields in the object with the fields in the template. This allows data from Salesforce to dynamically populate the corresponding positions in the template. By dragging and dropping, you can map Salesforce fields to text boxes, tables, or other elements in the template. Once field mapping is complete, when you retrieve data from Salesforce, it will automatically populate the corresponding positions in the template, generating a complete and dynamic document.

##### User Guide<br/>
![Data Source Config_Setting up the mapping](../_images/zh-cn/数据源设定_设定映射.png)

<h5>① Search Box</h5>
Used to quickly search for the required object name. 

<h5>② Object Field List</h5>
Select the fields of the object from the list and drag them to the right template field name to map. Click [Label] to display the label name of the object field, and click [API] to display the API name of the object field.

<h5>③ Template Field List</h5>
Displays the fields in the selected template, and maps the fields of the object to the [Template field name] column by dragging and dropping.

<h5>④ System Information</h5>
Displays the fields of the user and organization system objects, and maps them to the right template field name by dragging and dropping.

<h5>⑤ Preview Data</h5>
Displays which data to use as the test data source when previewing in the designer, allowing users to see the actual effect during preview.

<h5>⑥ Save and transfer to the design screen</h5>
After setting the mapping, click this button to jump to the designer to preview the actual mapping effect, showing the data read in ⑤.

<h5>⑦ Save and Back to List</h5>
After setting the mapping, click this button to jump to the Data Source Config list without viewing the mapping preview effect.
<br/>
<br/>
<br/>