<h5 id="start"></h5>

### Long Text

<aside>
💡 In template design, long text elements are commonly used components. By using the following functional settings, you can easily customize the display effects and functions of long text elements, adding richer and more professional design elements to your templates: automatic pagination and fixed height, etc.
</aside>

<h4 id="longtext-drag-rotate">
Drag and Rotate
</h4>

- Dragging Long Text Element: Select the [Long Text] element from the element library, then drag it to the desired position in the template.
- Rotate and Resize: Click the rotate control to rotate, or drag the edges of the element to resize it to fit the template layout.

![Long Text_Drag and Rotate](../_images/en/Long Text_Drag and Rotate.gif)

#### Attribute Settings

#### 1. Basic Attributes
[`Title`](#longtext-title): Set the content displayed by the element.<br/>
[`Field Name`](#longtext-field): Define the field name of the element to associate it with the data source.<br/>
[`Test Data`](#longtext-test-data): Enter test data to preview the actual effect (field name must be set first).<br/>
[`Position Coordinates, Width and Height`](#longtext-position-width-height): Adjust the position, width, and height of the text on the interface.<br/>
[`Title Visibility`](#longtext-show-title): Control the visibility of the long text title (field name must be set first).<br/>
[`Fixed Position`](#longtext-position-width-height-fixed): Once fixed, the element will stay in its current position and will not move with other elements.<br/>

<div id="longtext-title">
<div style="display: flex;justify-content: left;"><span>1-1 Basic - Title</span></div>

![Long Text_Basic Attributes_Title](../_images/en/Long Text_Basic Attributes_Title.gif)
</div>
<br/><br/>

<div id="longtext-field">
<div style="display: flex;justify-content: left;"><span>1-2 Basic - Field Name</span></div>

![Long Text_Basic Attributes_Field Name](../_images/en/Long Text_Basic Attributes_Field Name.gif)
</div>
<br/><br/>

<div id="longtext-test-data">
<div style="display: flex;justify-content: left;"><span>1-3 Basic - Test Data</span></div>

![Long Text_Basic Attributes_Test Data](../_images/en/Long Text_Basic Attributes_Test Data.gif)
</div>
<br/><br/>

<div id="longtext-position-width-height">
<div style="display: flex;justify-content: left;"><span>1-4 Basic - Position Coordinates, Width and Height</span></div>

![Long Text_Basic Attributes_Position Coordinates, Width and Height](../_images/en/Long Text_Basic Attributes_Position Coordinates, Width and Height.gif)
</div>
<br/><br/>

<div id="longtext-show-title">
<div style="display: flex;justify-content: left;"><span>1-5 Basic - Title Visibility</span></div>

![Long Text_Basic Attributes_Title Visibility](../_images/en/Long Text_Basic Attributes_Title Visibility.gif)
</div>
<br/><br/>

<div id="longtext-position-width-height-fixed">
<div style="display: flex;justify-content: left;"><span>1-6 Basic - Fixed Position</span></div>

![Long Text_Basic Attributes_Fixed Position](../_images/en/Long Text_Basic Attributes_Fixed Position.gif)
</div>
<br/><br/>

#### 2. Style Attributes

[`Font Style`](#longtext-fonttype): Customize the font, size, weight, letter spacing, and color of the text to meet design requirements.<br/>
[`Line Style and Alignment`](#longtext-backgroundalign): Set the line spacing, indentation per line, remove left paragraph whitespace, and text alignment within the element (left or right alignment).<br/>
[`Line Height and Font Display Size`](#longtext-lineheight): Set the minimum height value of the long text element or fix its height. If the value inside the element exceeds the fixed height, you can reduce the font size to fully display the content within the long text.<br/>
[`Rotation Angle`](#longtext-rotationangle): Rotate the angle of the element.<br/>
[`Element Level`](#longtext-elementlevel): Control the display order of the element in the layer.<br/>

<mark>**Note: If the data of the long text element exceeds the footer line, it will automatically paginate. When both minimum height and fixed height are set, fixed height takes higher priority.**</mark>

<div id="longtext-fonttype">
<div style="display: flex;justify-content: left;"><span>1-1 Style - Font Style</span></div>

![Long Text_Style Attributes_Font Style](../_images/en/Long Text_Style Attributes_Font Style.gif)
</div>
<br/><br/>

<div id="longtext-backgroundalign">
<div style="display: flex;justify-content: left;"><span>1-2 Style - Line Style and Alignment</span></div>

![Long Text_Style Attributes_Line Style and Alignment](../_images/en/Long Text_Style Attributes_Line Style and Alignment.gif)
</div>
<br/><br/>

<div id="longtext-lineheight">
<div style="display: flex;justify-content: left;"><span>1-3 Style - Line Height and Font Display Size</span></div>

![Long Text_Style Attributes_Line Height and Font Display Size](../_images/en/Long Text_Style Attributes_Line Height and Font Display Size.gif)
</div>
<br/><br/>

<div id="longtext-rotationangle">
<div style="display: flex;justify-content: left;"><span>1-4 Style - Rotation Angle</span></div>

![Long Text_Style Attributes_Rotation Angle](../_images/en/Long Text_Style Attributes_Rotation Angle.gif)
</div>
<br/><br/>

<div id="longtext-elementlevel">
<div style="display: flex;justify-content: left;"><span>1-5 Style - Element Level</span></div>

![Long Text_Style Attributes_Element Level](../_images/en/Long Text_Style Attributes_Element Level.gif)
</div>
<br/><br/>

#### 3. Border Attributes
[`Border Style`](#longtext-bordertype): Set the styles for the left, top, right, and bottom borders respectively.<br/>
[`Border Size and Color`](#longtext-bordercolor): Adjust the width and color of the borders to meet design needs.<br/>
[`Padding`](#longtext-insidemargin): Set the styles for the left, top, right, and bottom padding respectively.<br/>

<div id="longtext-bordertype">
<div style="display: flex;justify-content: left;"><span>1-1 Border - Border Style</span></div>

![Long Text_Border Attributes_Border Style](../_images/en/Long Text_Border Attributes_Border Style.gif)
</div>
<br/><br/>

<div id="longtext-bordercolor">
<div style="display: flex;justify-content: left;"><span>1-2 Border - Border Size and Color</span></div>

![Long Text_Border Attributes_Border Size and Color](../_images/en/Long Text_Border Attributes_Border Size and Color.gif)
</div>
<br/><br/>

<div id="longtext-insidemargin">
<div style="display: flex;justify-content: left;"><span>1-3 Border - Padding</span></div>

![Long Text_Border Attributes_Padding](../_images/en/Long Text_Border Attributes_Padding.gif)
</div>
<br/><br/>

#### 4. Advanced Attributes

`Force Pagination`: Control whether the element is forced to display separately on the page.<br/>
`Show and Hide Rules`: Set the display conditions of the element, such as hiding the element under specific pages or conditions.<br/>
`Drag Direction`: Set the direction in which the element can be dragged.<br/>