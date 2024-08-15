<h5 id="start"></h5>

### 上級開発応用

<aside>
💡 開発者はカスタム開発を通じて業務オブジェクトのデータを抽出し、実際のニーズに応じて必要なデータフィールドを選択できます。この柔軟性により、具体的な業務要件に基づいてデータ抽出プロセスをカスタマイズし、必要なデータのみを抽出することで、データの冗長性を回避し、データ処理の効率と正確性を向上させることができます。
</aside>
<br>

#### **1. デザイナーを開く**

> eDocument DXタブのクイックスタートまたは新しいテンプレートデータの作成からデザイナーを開きます。

#### **2. テンプレートを選択または新規作成**

> ﾃﾝﾌﾟﾚｰﾄ ｻﾝﾌﾟﾙでテンプレートを選択するか、空白テンプレートを新規作成します。ここでは請求書を例にします。

![上級開発応用_テンプレートを選択または新規作成](../_images/jp/上級開発応用_テンプレートを選択または新規作成.gif)

#### **3. テンプレートを保存する**

> デザインが完了したら、左上にテンプレート名を入力し、保存ボタンをクリックするかショートカットキー（Ctrl / Command + S）を使用してテンプレートを保存します。

![上級開発応用_テンプレートを保存する](../_images/jp/上級開発応用_テンプレートを保存する.gif)

#### **4. データモデルの抽出とApexクラスの作成**

> 4.1 "ApexClassデータモデル"アイコンをクリックし、生成されたApexクラス定義の内容をコピーします。

![上級開発応用_Apexクラスをコピー](../_images/jp/上級開発応用_Apexクラスをコピー.gif)

> 4.2 Salesforceの開発環境で、新しいApexクラスを作成し、コピーしたコードを貼り付けます。

![上級開発応用_クラス作成手順](../_images/jp/上級開発応用_クラス作成手順.gif)

例コードは以下の通りです：
```
/**
 * ECP_DataSourceDto
 */
@JsonAccess(serializable='always')
public with sharing class ECP_DataSourceDto extends eprint.ECP_CommDto {
    public ECP_DataSourceDto() {
        detaillist = new List<DetaillistClass>(); // init detaillist
    }
    public String no { get; set; } // テキスト
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

#### **5. アクションの設定**

> Visualforceページの作成、プレビュー印刷ボタンの設定、カスタム開発のApexクラスの作成については、[アクション設定](c-actionOverview#start)を参照してください。

#### **6. カスタム開発**

> 6.1 アクション設定で作成したApexクラスにカスタム開発ロジックを追加します。

![上級開発応用_カスタム開発](../_images/jp/上級開発応用_カスタム開発.png)

サンプルコードは以下の通りです：
```
public with sharing class OrderPreviewPrint {
    public OrderPreviewPrint (ApexPages.StandardController controller) {}
    public String dataSource { get; set; }
    public String dataSourcePlus { get; set; }
    public String zipDataSource { get; set; }

    public void initAction() {
        // データソースをカスタマイズする必要がある場合、このJSONフィールドを設定してください。
        dataSource = dataJson();
        // 画面で部分的にカスタムデータソースを選択に追加する必要がある場合、このJSONフィールドを設定してください。
        dataSourcePlus = '{}';
        // オブジェクトによるPDF ZIPのダウンロードが必要な場合、このJSONフィールドを設定してください
        // このようにデータを設定する必要があります:  zipDataSource = JSON.serialize(Map<ObjectId, Map<PDFName, dataSource JSON>)
       zipDataSource = '{}';
    }

    /**
     * これはJSONデータを生成するApexメソッドです
     * @return 注文データを含むJSON文字列を返します
     */
    private String dataJson() {
        // データソース情報を格納するために、ECP_DataSourceDtoオブジェクトのリストを作成します
        List<ECP_DataSourceDto> dataSourceList = new List<ECP_DataSourceDto>();
        
        // ECP_DataSourceDtoオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto dataSource = new ECP_DataSourceDto();
        dataSource.no = '100012'; // 注文番号を設定
        dataSource.reqGuestName = 'AC株式会社北京支社'; // 顧客名を設定
        dataSource.sign = 'https://ecloudsoft.github.io/ecprint/sample/imgs/テストスタンプ.png'; // サイン画像のURLを設定
        dataSource.reqPostNo = '355-0007'; // 郵便番号を設定
        dataSource.reqAddress = '北京市朝陽区999号301'; // 顧客住所を設定
        dataSource.reqCharge = 'ソフトウェア部門 張三'; // 担当者の部署と名前を設定
        
        // 注文明細を格納するために、ECP_DataSourceDto.DetaillistClassオブジェクトのリストを作成します
        dataSource.detaillist = new List<ECP_DataSourceDto.DetaillistClass>();
        
        // ECP_DataSourceDto.DetaillistClassオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto.DetaillistClass detail1 = new ECP_DataSourceDto.DetaillistClass();
        detail1.productName = 'リンゴ'; // 商品名を設定
        detail1.quantity = '10'; // 数量を設定
        detail1.unitPrice = '7'; // 単価を設定
        detail1.amount = '70'; // 金額を設定
        // 注文明細をデータソースの明細リストに追加します
        dataSource.detaillist.add(detail1);

        // ECP_DataSourceDto.DetaillistClassオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto.DetaillistClass detail2 = new ECP_DataSourceDto.DetaillistClass();
        detail2.productName = 'バナナ'; // 商品名を設定
        detail2.quantity = '15'; // 数量を設定
        detail2.unitPrice = '5'; // 単価を設定
        detail2.amount = '75'; // 金額を設定
        // 注文明細をデータソースの明細リストに追加します
        dataSource.detaillist.add(detail2);

        // ECP_DataSourceDto.DetaillistClassオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto.DetaillistClass detail3 = new ECP_DataSourceDto.DetaillistClass();
        detail3.productName = 'オレンジ'; // 商品名を設定
        detail3.quantity = '8'; // 数量を設定
        detail3.unitPrice = '6'; // 単価を設定
        detail3.amount = '48'; // 金額を設定
        // 注文明細をデータソースの明細リストに追加します
        dataSource.detaillist.add(detail3);

        // ECP_DataSourceDto.DetaillistClassオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto.DetaillistClass detail4 = new ECP_DataSourceDto.DetaillistClass();
        detail4.productName = 'ぶどう'; // 商品名を設定
        detail4.quantity = '12'; // 数量を設定
        detail4.unitPrice = '10'; // 単価を設定
        detail4.amount = '120'; // 金額を設定
        // 注文明細をデータソースの明細リストに追加します
        dataSource.detaillist.add(detail4);

        // ECP_DataSourceDto.DetaillistClassオブジェクトを作成し、その属性を設定します
        ECP_DataSourceDto.DetaillistClass detail5 = new ECP_DataSourceDto.DetaillistClass();
        detail5.productName = 'スイカ'; // 商品名を設定
        detail5.quantity = '3'; // 数量を設定
        detail5.unitPrice = '20'; // 単価を設定
        detail5.amount = '60'; // 金額を設定
        // 注文明細をデータソースの明細リストに追加します
        dataSource.detaillist.add(detail5);
        
        // データソースオブジェクトをデータソースリストに追加します
        dataSourceList.add(dataSource);
        
        // データソースリストをJSON文字列に変換して返します
        return ECP_CommDto.ListToJson(dataSourceList);
    }
}
```

#### **7. Visualforceページコードの修正**

> 7.1 extensions、action、およびdataSourceの処理を追加します。extensionsの値はApexクラスの名前に設定します。

![上級開発応用_VFPageコードの修正](../_images/jp/上級開発応用_VFPageコードの修正.gif)

#### **8. プレビュー**

> ボタンをクリックすると、選択したテンプレートが新しいウィンドウに表示されます。<br/>

![上級開発応用_プレビュー](../_images/jp/上級開発応用_プレビュー.gif)

#### **9. 印刷**

> 「print」ボタンをクリックすると、テンプレートが印刷されます。<br/>

<mark>**注意**</mark>：印刷を行う前に、デバイスが印刷クライアントに接続されていることを確認してください。接続されていない場合は、[印刷端末](download.md)を参照してください。

![上級開発応用_印刷](../_images/jp/上級開発応用_印刷.png)
