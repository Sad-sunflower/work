<h5 id="start"></h5>

### HTML

<aside>
💡 By customizing HTML code, you can easily embed tables, text, images, hyperlinks, and other elements in your template to achieve personalized design effects.
</aside>

#### **Drag and Rotate**

- Drag HTML Element: Select the [HTML] element from the element library and drag it to the desired position in the middle template.
- Rotate and Resize: Click the rotation control to rotate, or drag the edges of the element to resize it to fit the template layout.

#### Property Settings

#### 1. Basic Properties

`Field Name`: Define the field name of the element to associate it with the datasource.<br/>
`Position Coordinate, Width & Height`: Adjust the position, width, and height of the HTML element on the interface.<br/>
`Show Rule`: Set the display conditions of the element, such as hiding the element on specific pages or conditions (see text section for demonstration).<br/>
`Fixed Position`: Once fixed, the element will stay in its position and will not move when other elements are adjusted.<br/>

#### 2. Style Properties

[`Fixed Height`](#html-fixed-height): When fixed, the height remains unchanged.<br/>
`Rotate Angle`: Rotate the element by a specified angle.<br/>
`Z-index`: Control the display order of elements within layers.<br/>

<div id="html-fixed-height">
<div style="display: flex;justify-content: left;"><span>2-1 Style - Fixed Height</span></div>

![HTML_Style Properties_Fixed Height](../_images/zh-cn/HTML_样式属性_固定高度.gif)
</div>

#### 3. Advanced Properties

`Force Page Break`: Control whether the element is forced to display alone on the page.<br/>
`Drag Direction`: Set the direction in which the element can be dragged.<br/>

#### 4. Notes

4.1 HTML elements currently do not support pagination and can only be displayed on a single page. When the content of an HTML element is too long and overlaps other elements, you can set the fixed height in the style properties. This way, the overflow content will be hidden and will not overlap other elements.

4.2 If the HTML element is set with a field name and no data is retrieved, the preview will be empty.