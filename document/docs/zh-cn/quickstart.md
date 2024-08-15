#### 1. App下载
*从Appexchange市场[下载](appDownload.md)应用程序。*

#### 2. 用户权限设定
- 打开salesforce的用户->权限集，选择"eDocument DX管理者"。

![权限设定_权限集](../_images/zh-cn/权限设定_权限集.png)

- 选择"管理分配"。
![权限设定_管理分配](../_images/zh-cn/权限设定_管理分配.png)

- 点击"添加分配"。
![权限设定_添加分配](../_images/zh-cn/权限设定_添加分配.png)

- 勾选需要添加权限的用户（需要使用app的用户），点击"下一步"。
![权限设定_勾选需要添加权限的用户](../_images/zh-cn/权限设定_勾选需要添加权限的用户.png)

- 点击"分配"，设定完成。
![权限设定_点击分配设定完成](../_images/zh-cn/权限设定_点击分配设定完成.png)

#### 3. 进入设计器
*从首页点击"开始设计"或"新建"进入模版设计器。*
![快速开始_进入设计器](../_images/zh-cn/快速开始_进入设计器.png)

#### 4. 切换语言
*在设计器右上角，切换您的语言。*
![快速开始_切换语言](../_images/zh-cn/快速开始_切换语言.png)

#### 5. 选择请求书模板
*5.1 点击"模板中心"图标，浏览预置的模版。*
![快速开始_选择请求书模板](../_images/zh-cn/快速开始_选择请求书模板.png)

*5.2 选择请求书模版，点击确认。*
![快速开始_选择请求书模板_确定](../_images/zh-cn/快速开始_选择请求书模板_确定.png)

#### 6. 定制与修改模板
*对选定的模板进行编辑和定制，例如，给表格金额列添加聚合功能，统计金额平均值。*
![快速开始_定制与修改模板](../_images/zh-cn/快速开始_定制与修改模板.png)

#### 7. 预览打印效果
*7.1 点击预览图标，查看模板的打印效果。*
![快速开始_预览打印效果6.1](../_images/zh-cn/快速开始_预览打印效果6.1.png)

*7.2 在预览画面下，可以直接导出为PDF文件或在浏览器中直接进行打印操作。模板中心提供的模板包含测试数据，方便用户预览。*
![快速开始_预览打印效果6.2](../_images/zh-cn/快速开始_预览打印效果6.2.png)

#### 8. 保存模板
*为模板命名后，点击保存图标。*
![快速开始_保存模板](../_images/zh-cn/快速开始_保存模板.png)

#### 9. 设定模板的数据
*9.1 点击"数据源设定"tab，点击"新建"按钮。*
![快速开始_设定模板的数据9.1](../_images/zh-cn/快速开始_设定模板的数据9.1.png)

*9.2 选择模板想要绑定的主对象，以请求书为例，主对象选择订单信息。*
![快速开始_设定模板的数据9.2](../_images/zh-cn/快速开始_设定模板的数据9.2.png)

*9.3 选择模板要绑定的子对象，以请求书为例，子对象选择订单下的商品信息。*
![快速开始_设定模板的数据9.3](../_images/zh-cn/快速开始_设定模板的数据9.3.png)

*9.4 选择对象要绑定的模板，选择step6创建好的请求书模板。*
![快速开始_设定模板的数据9.4](../_images/zh-cn/快速开始_设定模板的数据9.4.png)

*9.5 拖拽对象字段到相应的模板字段中，将模板中的字段与对象字段映射起来，点击保存。此时的模板已经绑定好数据。*
![快速开始_设定模板的数据9.5](../_images/zh-cn/快速开始_设定模板的数据9.5.png)

#### 10. 新建云打印或本地打印服务配置
云打印请参考[云打印服务](sc-cloudPrint.md#start)配置。
本地打印请参考[本地打印服务](sc-localPrint.md#start)配置。

#### 11. 新建Action配置
*11.1 点击"Action设定"tab，点击"新建"按钮。*
![快速开始_新建Action配置11.1](../_images/zh-cn/快速开始_新建Action配置11.1.png)

*11.2 添加配置信息，点击"保存"按钮。[配置说明详见Action配置](c-actionOverview.md#start)*

![快速开始_新建Action配置11.2](../_images/zh-cn/快速开始_新建Action配置11.2.png)

*11.3 完成设置后，系统将为您生成示例代码。*
![快速开始_新建Action配置11.3](../_images/zh-cn/快速开始_新建Action配置11.3.gif)

#### 12. 创建Visualforce Page

*12.1 在Salesforce中创建新的Visualforce Page文件。*
![快速开始_创建VFPage12.1](../_images/zh-cn/快速开始_创建VFPage12.1.gif)

*12.2 在对象中创建新的预览按钮。*
![快速开始_创建预览按钮12.2](../_images/zh-cn/快速开始_创建预览按钮12.2.gif)

*12.3 在Salesforce中创建新的Apex Class文件。*
![快速开始_创建ApexClass12.3](../_images/zh-cn/快速开始_创建ApexClass12.3.gif)

#### 13. 预览打印设置

*在对象页面中，确保按钮可见。*

![快速开始_预览打印设置](../_images/zh-cn/快速开始_预览打印设置.gif)

#### 14. 预览

*点击"订单打印"按钮，将在新窗口中显示所选模板。*

![快速开始_预览](../_images/zh-cn/快速开始_预览.gif)

#### 15. 打印

*点击"print"按钮，将对模板打印。*

<mark>**注意**</mark>：进行打印前，请确保您的设备已连接打印客户端。如没有连接请参考[打印终端](download.md)。

![快速开始_打印](../_images/zh-cn/快速开始_打印.png)

