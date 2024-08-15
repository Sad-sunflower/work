<h5 id="start"></h5>

### Vertical Text Display

<aside>
💡 This guide will teach you how to easily set text to display vertically in our designer.
</aside>
<br>

#### **1. Open the Designer**

> Open the designer via the eDocument DX Tab's Quick Start or New Template Data options.

#### **2. Set Text to Vertical Alignment**

> In the designer, select the text element you want to display vertically.
> Open the properties panel for that element and switch to the "Advanced" tab.
> In the "Style Function" input box, paste the following code to set the text to vertical alignment:

```
function styler(value, options, target, templateData) {
    return {
        writingMode: 'vertical-lr', 
    };
}
```

![Vertical Text Display_Set Text to Vertical Alignment](../_images/zh-cn/文本纵向显示_设定文本纵向排列.gif)

#### **3. Preview Print Effect**
> Click the preview icon to view the print effect of the template.

![Vertical Text Display_Preview Print Effect](../_images/zh-cn/文本纵向显示_预览打印效果.gif)

#### **4. Save Template**
> After naming the template, click the save icon.

![Vertical Text Display_Save Template](../_images/zh-cn/文本纵向显示_保存模板.gif)