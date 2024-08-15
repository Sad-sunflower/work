<h5 id="start"></h5>

### 富文本框内容打印

<aside>
💡 富文本框内容打印功能让您能够在设计账票时轻松地将富文本内容嵌入打印数据中，并在打印预览时以HTML格式自动展示。通过绑定HTML代码到富文本框，系统能够自动解析并展示这些代码所包含的格式，如超链接、斜体、颜色等。在处理HTML数据时，请注意将所有双引号替换为单引号，或用占位符amp;quot;来代替，以避免解析冲突。
</aside>
<br>

#### **实例说明：**
假设，您正在为订单设计模板，该模板需展示商品描述，涉及加粗、斜体、颜色等富文本格式，并需嵌入商品页面的超链接。通过富文本框内容打印功能，您可以直接将HTML格式的商品描述嵌入模板，确保打印预览时以最佳效果展示。这样，客户在收到打印订单时，可以直观地了解商品详情，并直接点击链接查看更多信息。

#### **1. 打开设计器**

> 通过eDocument DX Tab的快速开始、新建模板数据或者编辑下方既存模板的方式打开设计器。

#### **2. 新建模板**

> 将HTML元素拖拽至面板中。

![富文本内容打印_新建模板](../_images/zh-cn/富文本内容打印_新建模板.gif)

#### **3. 设定HTML的字段属性**

> 设定HTML的字段名称。

![富文本内容打印_设定HTML的字段属性](../_images/zh-cn/富文本内容打印_设定HTML的字段属性.gif)

#### **4. 设定格式化函数**

> 选中HTML元素，打开其属性面板并切换到"高级"标签页。<br/>

> 在"格式化函数"输入框中点击，打开函数窗口。通过利用AI生成格式化函数方式或者自己编写(请参考高级函数应用中关于<a href="/#/zh-cn/ad-highlevel.md#self-format1" target="_blank">格式化函数</a>的说明)方式来作成函数。

![富文本内容打印_设定格式化函数](../_images/zh-cn/富文本内容打印_设定格式化函数.gif)

#### 5. 自定义编写代码
> 5.1 示例代码逻辑：
```
function formatter (value, options, templateData) {
  return `
    <body style="font-family: Arial, sans-serif; line-height: 1.6; margin: 20px; background-color: #f9f9f9; color: #333;">
        <h1 style="color: #FF6347;">苹果</h1>
        <div style="font-size: 1.1em; margin-bottom: 20px;">
            <p>苹果是一种非常受欢迎的水果，因其<em>美味</em>和<em>健康</em>的特性而广受喜爱。它们不仅富含维生素，还具有<em style="color: #FF4500;">抗氧化</em>和<em style="color: #FF4500;">防癌</em>的功效。</p>
            <p>点击下面的链接了解更多关于苹果的信息：</p>
            <a href="https://e-cloudsoft2-dev-ed.develop.lightning.force.com/lightning/r/Product2/01tGB00000DSHDXYA5/view" target="_blank" style="display: inline-block; margin-top: 15px; padding: 10px 20px; background-color: #FF6347; color: white; text-decoration: none; border-radius: 5px;">了解更多</a>
        </div>
        <img src="https://sad-sunflower.github.io/work/testImage/apple.png" alt="苹果图片" style="max-width: 100%; height: auto; border-radius: 10px; margin-top: 20px;">
    </body>`;
}
```

> 5.2 复制代码块到"格式化函数"的右侧函数代码区域，并点击"确定"保存设置。
 
![富文本内容打印_自定义编写代码_复制代码](../_images/zh-cn/富文本内容打印_自定义编写代码_复制代码.png)
 
> 5.3 点击预览查看效果。

![富文本内容打印_自定义编写代码_预览](../_images/zh-cn/富文本内容打印_自定义编写代码_预览.gif)

#### **6. 保存模板**

> 完成设计后，在左上角输入模板名称，并点击保存按钮或使用快捷键(Ctrl / Command + S)保存您的模板。

![富文本内容打印_保存模板](../_images/zh-cn/富文本内容打印_保存模板.gif)

#### **7. 查看和管理模板**

> 在模板Tab中，您可以将"最近查看的数据（固定列表）"修改为"全选"后即可查看所有保存的模板，并进行编辑或删除等操作。

![富文本内容打印_查看和管理模板](../_images/zh-cn/富文本内容打印_查看和管理模板.gif)