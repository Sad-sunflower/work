<h5 id="start"></h5>

### 高级开发应用

<aside>
💡 开发者可以通过自定义开发来抽取业务对象的数据，并且可以根据实际需求自行选择需要抽取的数据字段。这种灵活性使得开发者能够根据具体业务需求定制数据提取流程，确保只提取所需的数据，避免不必要的数据冗余，提高数据处理的效率和准确性。
</aside>
<br>

#### **1. 打开设计器**

> 通过eDocument DX Tab的快速开始或新建模板数据的方式打开设计器。

#### **2. 选择或新建模板**

> 在模板中心中，选择一个模板或新建一个空白模板。这里以请求书为例。

![高级开发应用_选择或新建模板](../_images/zh-cn/高级开发应用_选择或新建模板.gif)

#### **3. 保存模板**

> 设计完成后，在左上角输入模板名称，并点击保存按钮或使用快捷键(Ctrl / Command + S)保存您的模板。

![高级开发应用_保存模板](../_images/zh-cn/高级开发应用_保存模板.gif)

#### **4. 抽取并创建ApexClass数据模型**

> 4.1 点击"ApexClass数据模型"图标，复制生成的Apex类定义内容。

![高级开发应用_复制Apex类](../_images/zh-cn/高级开发应用_复制Apex类.gif)

> 4.2 在Salesforce开发环境中，创建一个新的Apex类，并将之前复制的代码粘贴进去。

![高级开发应用_创建class流程](../_images/zh-cn/高级开发应用_创建class流程.gif)

示例代码如下：
```
/**
 * ECP_DataSourceDto
 */
@JsonAccess(serializable='always')
public with sharing class ECP_DataSourceDto extends eprint.ECP_CommDto {
    public ECP_DataSourceDto() {
        detaillist = new List<DetaillistClass>(); // init detaillist
    }
    public String no { get; set; } // 文本
    public String reqGuestName { get; set; } // 請求先
    public String sign { get; set; } // sign
    public String reqPostNo { get; set; } // 〒
    public String reqAddress { get; set; } // 請求先の住所
    public String reqCharge { get; set; } // 担当者
    public List<DetaillistClass> detaillist { get; set; } // detaillist
    @JsonAccess(serializable='always')
    public class DetaillistClass {
        public String productName { get; set; } // productName
        public String quantity { get; set; } // quantity
        public String unitPrice { get; set; } // unitPrice
        public String amount { get; set; } // amount
    }
}
```

#### **5. Action配置**

> 创建Visualforce Page、配置预览打印按钮和创建自定义开发的Apex Class请参照[Action配置](c-actionOverview#start)

#### **6. 自定义开发**

> 6.1 在Action配置创建的Apex Class中添加自定义开发逻辑。

![高级开发应用_自定义开发](../_images/zh-cn/高级开发应用_自定义开发.png)

示例代码如下：
```
public with sharing class orderPrint {
    public orderPrint (ApexPages.StandardController controller) {}
    public String dataSource { get; set; }
    public String dataSourcePlus { get; set; }
    public String zipDataSource { get; set; }

    public void initAction() {
        // If you need to customize the data source, please set this JSON field.
        dataSource = dataJson();
        // If you need to add partially custom data sources to the selection on the screen, please set this JSON field.
        dataSourcePlus = '{}';
        // If you need to download pdf zip by object, please set this JSON field
        // You need to set data like this,  zipDataSource = JSON.serialize(Map<ObjectId, Map<PDFName, dataSource JSON>)
       zipDataSource = '{}';
    }

    /**
     * 这是一个生成 JSON 数据的 Apex 方法
     * @return 返回一个包含订单数据的 JSON 字符串
     */
    private String dataJson() {
        // 创建一个 ECP_DataSourceDto 对象的列表，用于存储数据源信息
        List<ECP_DataSourceDto> dataSourceList = new List<ECP_DataSourceDto>();
        
        // 创建一个 ECP_DataSourceDto 对象，并设置其属性
        ECP_DataSourceDto dataSource = new ECP_DataSourceDto();
        dataSource.no = '100012'; // 设置订单编号
        dataSource.reqGuestName = 'AC有限公司北京分公司'; // 设置客户名称
        dataSource.sign = 'https://ecloudsoft.github.io/ecprint/sample/imgs/テストスタンプ.png'; // 设置签名图片 URL
        dataSource.reqPostNo = '355-0007'; // 设置邮政编码
        dataSource.reqAddress = '北京市朝阳区999号301'; // 设置客户地址
        dataSource.reqCharge = '软件部门 张三'; // 设置负责人的部门和姓名
        
        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象的列表，用于存储订单明细
        dataSource.detaillist = new List<ECP_DataSourceDto.DetaillistClass>();
        
        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象，并设置其属性
        ECP_DataSourceDto.DetaillistClass detail1 = new ECP_DataSourceDto.DetaillistClass();
        detail1.productName = '苹果'; // 设置产品名称
        detail1.quantity = '10'; // 设置数量
        detail1.unitPrice = '7'; // 设置单价
        detail1.amount = '70'; // 设置金额
        // 将订单明细添加到数据源的明细列表中
        dataSource.detaillist.add(detail1);

        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象，并设置其属性
        ECP_DataSourceDto.DetaillistClass detail2 = new ECP_DataSourceDto.DetaillistClass();
        detail2.productName = '香蕉'; // 设置产品名称
        detail2.quantity = '15'; // 设置数量
        detail2.unitPrice = '5'; // 设置单价
        detail2.amount = '75'; // 设置金额
        // 将订单明细添加到数据源的明细列表中
        dataSource.detaillist.add(detail2);

        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象，并设置其属性
        ECP_DataSourceDto.DetaillistClass detail3 = new ECP_DataSourceDto.DetaillistClass();
        detail3.productName = '橙子'; // 设置产品名称
        detail3.quantity = '8'; // 设置数量
        detail3.unitPrice = '6'; // 设置单价
        detail3.amount = '48'; // 设置金额
        // 将订单明细添加到数据源的明细列表中
        dataSource.detaillist.add(detail3);

        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象，并设置其属性
        ECP_DataSourceDto.DetaillistClass detail4 = new ECP_DataSourceDto.DetaillistClass();
        detail4.productName = '葡萄'; // 设置产品名称
        detail4.quantity = '12'; // 设置数量
        detail4.unitPrice = '10'; // 设置单价
        detail4.amount = '120'; // 设置金额
        // 将订单明细添加到数据源的明细列表中
        dataSource.detaillist.add(detail4);

        // 创建一个 ECP_DataSourceDto.DetaillistClass 对象，并设置其属性
        ECP_DataSourceDto.DetaillistClass detail5 = new ECP_DataSourceDto.DetaillistClass();
        detail5.productName = '西瓜'; // 设置产品名称
        detail5.quantity = '3'; // 设置数量
        detail5.unitPrice = '20'; // 设置单价
        detail5.amount = '60'; // 设置金额
        // 将订单明细添加到数据源的明细列表中
        dataSource.detaillist.add(detail5);
        
        // 将数据源对象添加到数据源列表中
        dataSourceList.add(dataSource);
        
        // 将数据源列表转换为 JSON 字符串并返回
        return ECP_CommDto.ListToJson(dataSourceList);
    }
}
```

#### **7. 修改Visualforce Page代码**

> 7.1 添加extensions、action和dataSource的处理。extensions的值设置为Apex Class的Name。

![高级开发应用_修改VFPage代码](../_images/zh-cn/高级开发应用_修改VFPage代码.gif)

#### **8. 预览**

> 点击按钮，将在新窗口中显示所选模板。<br/>

![高级开发应用_预览](../_images/zh-cn/高级开发应用_预览.gif)

#### **9. 打印**

> 点击"print"按钮，将对模板打印。<br/>

<mark>**注意**</mark>：进行打印前，请确保您的设备已连接打印客户端。如没有连接请参考[打印终端](download.md)。

![高级开发应用_打印](../_images/zh-cn/高级开发应用_打印.png)