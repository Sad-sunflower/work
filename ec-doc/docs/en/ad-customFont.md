<h5 id="start"></h5>

### Custom Font Upload

<aside>
💡 The font in the template's style tab can be modified to change the font in the template. This guide will provide detailed instructions on how to upload custom fonts to the font property in the style settings of the designer.
</aside>
<br>

#### **1. Check Current Font Options**
Before uploading a custom font, first check the current font options in the designer's style settings to understand the available fonts.

<p style="background:grey">TODO->image<br/></p>

#### **2. Upload Custom Font to Salesforce**

> 2.1 In the Salesforce setup menu, find and click on "Custom Code" and select "Custom Metadata Types" page.

<p style="background:grey">TODO->image<br/></p>

> 2.2 In the Custom Metadata Types page, find the custom metadata record type related to fonts (named `Font`). Click the `Manage Records` link next to it.

<p style="background:grey">TODO->image<br/></p>

> 2.3 In the font management page, click the `New` button to create a new font record.

<p style="background:grey">TODO->image<br/></p>

> 2.4 In the new font record form, fill in the information for the new font:<br/>

`Label`: The name used to uniquely identify the font within Salesforce.<br/>
`Font Name`: The name that will be displayed in the designer's style font dropdown menu.<br/>
`Font URL`: The URL pointing to the custom font file. Ensure the URL is accessible and the font file is uploaded.<br/>
<mark>**Note**</mark>: Ensure the font file format is compatible, such as .woff, .woff2, .ttf, or .otf.

Click `Save` to save the new font record.<br/>

<p style="background:grey">TODO->image<br/></p>

#### **3. Verify Custom Font**

After saving the font record, return to the font dropdown in the designer's style settings. You should be able to see the newly added custom font option. Select this font and preview its effect in the designer.

<p style="background:grey">TODO->image<br/></p>

<br/>
<br/>
<br/>