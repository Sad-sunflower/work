<h5 id="start"></h5>

### 上級関数応用

<aside>
💡 上級関数機能を使用すると、テキスト、スタイル、テーブル要素を柔軟に処理でき、さまざまな複雑な印刷ニーズに対応できます。
</aside>
<br>

### **1. テキスト/ロングテキスト：書式設定関数{formatter}**

<mark>**注意**</mark>：templateDataのデータのみアクセス可能であり、scriptで動的に計算されたフィールドを集計することはできません。

#### 1.1 なぜ使用するのか？
書式設定関数を使用すると、データを特定の形式に変換することができます。例えば、日付の形式を変更する、千位の区切りを追加するなどです。<br/>
また、データを計算したり処理したりする必要がある場合にも便利です。例えば、テーブルの特定の列の合計を計算することができます。<br/>

#### 1.2 パラメータの説明
`title`：要素のタイトルデータ。<br/>
`value`：具体的な要素の値。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`templateData`：すべての印刷データ。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素を直接特定するのに使用します。<br/>

#### 1.3 例示のロジック
> templateData内のテーブルdetaillistの[金 額]列の合計値を計算する。<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)
```
function formatter(title,value,options,templateData,target){
  let amount = 0;
  for (let index = 0; index < templateData?.detaillist?.length; index++) {
      amount += 1*templateData.detaillist[index].amount;
  }
  return amount;
}
```

#### 1.4 例示の効果
![上級関数機能_書式設定関数](../_images/jp/上級関数機能_書式設定関数.gif)
<br>
<br>
<br>

### **2. テキスト/ロングテキスト：スタイル関数{styler}**

#### 2.1 なぜ使用するのか？
テキストやロングテキスト要素に特定のスタイルを適用する場合に、スタイル関数を使用します。例えば、特定のフォント、色、または整列方法を設定したい場合に役立ちます。

#### 2.2 パラメータの説明
`value`：具体的な要素の値。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素を直接特定するのに使用します。<br/>
`templateData`：すべての印刷データ。<br/>

#### 2.3 例示のロジック
> 縦書きモード、左から右に書く。
```
function styler(value, options, target, templateData) {
    return {
        writingMode: 'vertical-lr', 
    };
}
```

#### 2.4 例示の効果
![上級関数機能_スタイル関数](../_images/jp/上級関数機能_スタイル関数.gif)
<br>
<br>
<br>

### **3. テーブル列：下部の集約書式設定関数{tableSummaryFormatter}**

#### 3.1 なぜ使用するのか？
テーブルのボトムに特定の列の合計、平均値、その他の統計情報を表示したい場合に、下部の集約書式設定関数を使用します。これにより、データの概要や統計を提供するのに役立ちます。

#### 3.2 パラメータの説明
`column`：現在の列の関連属性オブジェクト。これにより、その列の名前、値などにアクセスできます。<br/>
`fieldPageData`：現在の列のすべての行データを含む配列。<br/>
`tableData`：現在のテーブルのすべての行データを含む配列で、広範なデータのコンテキストにアクセスするために使用します。<br/>
`options`：現在のテーブルのすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>

#### 3.3 例示のロジック
> "数量合計：" + {集計値}を表示します。集計値：列の数値を累計し、千位の区切り記号を追加して、小数を表示しません。【htmlスタイル：中央揃え、ライトブルーの背景、赤いフォント】<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)

```
function tableSummaryFormatter(column, fieldPageData, tableData, options) {
    let sum = fieldPageData.reduce((acc, cur) => acc + parseInt(cur), 0); 
    let formattedSum = sum.toLocaleString(); 
    return `<td style="text-align:center;background-color:lightblue;color:red;">数量合計：${formattedSum}</td>`; 
}
```

#### 3.4 例示の効果
![上級関数機能_ボトム集計フォーマット関数](../_images/jp/上級関数機能_下部の集約書式設定関数.gif)
<br>
<br>
<br>

### **4. テーブル 列：セルレンダリング関数{renderFormatter}**

#### 4.1 なぜ使用するのか？
renderFormatter関数を使用すると、データの特性に基づいてカスタムレンダリングが可能です。例えば、色のマーク、日付のフォーマット、通貨値やパーセンテージなどです。特に、在庫管理者が在庫不足の商品をすばやく識別する必要がある場合、renderFormatter関数を使用してこれらの商品の在庫量をハイライト表示できます。

#### 4.2 パラメータの説明
`value`：セルの印刷データ値。<br/>
`row`：現在の行データのオブジェクト。row.列名を使用して現在の行の特定の列の値を照会できます。<br/>
`colIndex`：現在の列のテーブル内でのインデックス位置。0から始まります。<br/>
`options`：現在のテーブルのすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`rowIndex`：現在の行のテーブル内でのインデックス位置。0から始まります。<br/>

#### 4.3 例示のロジック
> [商品名 ／ 品名]列、列の文字の後に行番号を追加します。【htmlスタイル：赤いフォント】<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)
```
function renderFormatter(value, row, colIndex, options, rowIndex) {
    return `<td style="color:red;">${value} 行番号：${rowIndex + 1}</td>`;
}
```

#### 4.4 例示の効果
![上級関数機能_セルのレンダリング関数](../_images/jp/上級関数機能_セルのレンダリング関数.gif)
<br>
<br>
<br>

### **5. テーブル 列：セルの書式設定関数{formatter2}**

#### 5.1 なぜ使用するのか？
テーブルの特定の列に計算または処理されたデータを表示する必要がある場合、formatter2関数が非常に役立ちます。例えば、従業員のパフォーマンス情報を含むテーブルがあり、従業員の名前、売上高、売上目標、および達成率（売上高と売上目標の比率）を表示する場合です。formatter2関数を使用して達成率を計算すると、ユーザーが手動で計算する手間が省けます。

#### 5.2 パラメータの説明
`value`：セルの印刷データ値。<br/>
`row`：現在の行データのオブジェクト。row.列名を使用して現在の行の特定の列の値を照会できます。<br/>
`colIndex`：現在の列のテーブル内でのインデックス位置。0から始まります。<br/>
`options`：現在のテーブルのすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>

#### 5.3 例示のロジック
> [金額]が60000を超えるデータの場合、[数量]列の値に6を追加します。<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)

```
function formatter2(value, row, colIndex, options) {
    if(row.amount > 60000) {
        return Number(row.quantity) + 6;
    }
    return value;
}
```

#### 5.4 例示の効果
![上級関数機能_セルの書式設定関数](../_images/jp/上級関数機能_セルの書式設定関数.gif)
<br>
<br>
<br>

### **6. テーブル 列：セルのスタイル関数{styler2}**

#### 6.1 なぜ使用するのか？
styler2関数を使用することで、セルに対して動的に異なるスタイル（色、フォント、罫線など）を適用できます。

#### 6.2 パラメータの説明
`value`：セルの印刷データ値。<br/>
`row`：現在の行データのオブジェクト。row.列名を使用して現在の行の特定の列の値を照会できます。<br/>
`colIndex`：現在の列のテーブル内でのインデックス位置。0から始まります。<br/>
`options`：現在のテーブルのすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>

#### 6.3 例示のロジック
> [数量]テキストデータが"200"のセルは、フォントの色を赤に設定し、テキストの左右中央揃えにします。<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)

```
function styler2(value, row, index, options) {
  if (row.quantity === '200') {
    return {color: 'red', textAlign: 'center'};
  }
}
```

#### 6.4 例示の効果
![上級関数機能_セルのスタイル関数](../_images/jp/上級関数機能_セルのスタイル関数.gif)
<br>
<br>
<br>

### **7. テーブル 列：ヘッダーのスタイル関数{stylerHeader}**

#### 7.1 なぜ使用するのか？
stylerHeader関数を使用することで、テーブルヘッダーに動的に異なるスタイル（色、フォント、罫線など）を適用できます。

#### 7.2 パラメータの説明
`options`：現在のテーブルのすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>

#### 7.3 例示のロジック
> 現在の列(商品名 ／ 品名)のテーブルヘッダーのフォント色を赤に設定し、テキストの左右中央揃えにし、フォントを斜体にします。</br>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)

```
function stylerHeader(options) {
    return {color: 'red', textAlign: 'right', fontStyle: 'italic'};
}
```

#### 7.4 例示の効果
![上級関数機能_ヘッダーのスタイル関数](../_images/jp/上級関数機能_ヘッダーのスタイル関数.gif)
<br>
<br>
<br>

### **8. テーブル：スタイル関数{styler}**

#### 8.1 なぜ使用するのか？
styler関数を使用することで、テーブル全体に対して動的に異なるスタイル（色、フォント、罫線など）を適用できます。

#### 8.2 パラメータの説明
`value`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`target`：テーブル要素のDOM情報を含むオブジェクト。後続のスタイル設定時に直接ターゲット要素を特定するために使用されます。<br/>
`templateData`：すべての印刷データ。<br/>

#### 8.3 例示のロジック
> 現在のテーブルの罫線を「2px solid yellow」に設定します。

```
function styler(value, options, target, templateData){
  return {"border":"2px solid yellow"};
}
```

#### 8.4 例示の効果
![上級関数機能_テーブル_スタイル関数](../_images/jp/上級関数機能_テーブル_スタイル関数.gif)
<br>
<br>
<br>

### **9. テーブル：行のスタイル関数{rowStyler}**

#### 9.1 なぜ使用するのか？
rowStyler関数を使用することで、テーブル行に対して動的に異なるスタイル（色、フォント、罫線など）を適用できます。

#### 9.2 パラメータの説明
`value`：現在の行データのオブジェクト。value.列名を使用して現在の行の特定の列の値を照会できます。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`rowIndex`：現在の行のテーブル内でのインデックス位置。0から始まります。<br/>

#### 9.3 例示のロジック
> 奇数行の背景色を浅い青、フォントの色を濃い青に設定します。

```
function rowStyler(value, options, rowIndex) {
    return rowIndex % 2 === 0 ? { 'background-color': '#add8e6', 'color': '#00008b' } : {};
}
```

#### 9.4 例示の効果
![上級関数機能_行のスタイル関数](../_images/jp/上級関数機能_行のスタイル関数.gif)
<br>
<br>
<br>

### **10. テーブル：テーブルのフッター関数{footerFormatter}**

#### 10.1 なぜ使用するのか？
footerFormatter関数を使用することで、テーブルのフッターの内容をカスタマイズし、テーブルの底部に動的にデータの集計情報や統計データを反映させることができます。

#### 10.2 パラメータの説明
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`rowsData`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`data`：テーブルの各ページのデータ。<br/>
`templateData`：すべての印刷データ。<br/>

#### 10.3 例示のロジック
> テーブルフッターを生成します。<br/>
> フッター内容として、2つのtdタグを返します：<br/>
  > 1. "数量集計："；【HTMLスタイル：左右中央揃え、2列にわたる】<br/>
  > 2. {数量集計値}、数値型の数量値を累計し、非数値や空行は含まない。【HTMLスタイル：左揃え、3列にわたる】<br/>

> テーブルフィールド情報：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)<br/>

```
function footerFormatter(options, rowsData, data, templateData) {
  let totalQuantity = 0;
  rowsData.forEach(row => {
    const quantity = Number(row.quantity);
    if (!isNaN(quantity)) {
      totalQuantity += quantity;
    }
  });
  return `<tr><td colspan="2" style="text-align:center;">数量集計：</td><td colspan="2" style="text-align:left;">${totalQuantity}</td></tr>`;
}
```

#### 10.4 例示の効果
![上級関数機能_テーブルのフッター関数](../_images/jp/上級関数機能_テーブルのフッター関数.gif)
<br>
<br>
<br>

### **11. テーブル：行/列のマージ関数{rowsColumnsMerge}**

#### 11.1 なぜ使用するのか？
テーブル内に同じ値を持つ行（例えば商品名）が多数存在する場合、rowsColumnsMerge関数を使用してこれらの行や列を結合し、テーブルの表示効果を最適化できます。

#### 11.2 パラメータの説明
`data`：現在の行データのオブジェクト。data.列名を使用して現在の行の特定の列の値を照会できます。<br/>
`column`：現在の列の関連プロパティオブジェクトで、その列の名前や値などにアクセスできます。<br/>
`colIndex`：現在の列がテーブル内で持つインデックス位置。0から始まります。<br/>
`rowIndex`：現在の行がテーブル内で持つインデックス位置。0から始まります。<br/>
`tableData`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`templateData`：すべての印刷データ。<br/>

#### 11.3 例示のロジック
> [商品名 ／ 品名]列で内容が一致するデータを行結合します。<br/>

> テーブルフィールド：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)<br/>

```
function rowsColumnsMerge(data, column, colIndex, rowIndex, tableData, templateData) {
    if (column.field === 'productName') { 
        if (rowIndex === 0 || data.productName !== tableData[rowIndex - 1].productName) {
            let mergeCount = 1;
            for (let i = rowIndex + 1; i < tableData.length && tableData[i].productName === data.productName; i++) {
                mergeCount++;
            }
            return [mergeCount, 1]; 
        } else {
            return [0, 1]; 
        }
    }
    return [1, 1]; 
}
```

#### 11.4 例示の効果
![上級関数機能_行/列のマージ関数](../_images/jp/上級関数機能_行、列のマージ関数.gif)
<br>
<br>
<br>

<h4 id="self-group1"></h4>

### **12. テーブル：グループフィールド関数{groupFieldsFormatter}**

<mark>**注意**</mark>：`グループヘッダーの書式設定関数`と`グループフッターの書式設定関数`を併用する必要があります。

#### 12.1 なぜ使用するのか？
groupFieldsFormatter関数を使用することで、テーブル内のデータを指定したフィールドでグループ化できます。これにより、異なるグループ間のデータの違いや傾向をより明確に把握し、データの背後にある意味をより良く理解することができます。

#### 12.2 パラメータの説明
`type`：現在のテーブル要素の基本プロパティ。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`data`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>

#### 12.3 例示のロジック
> [月]フィールドでグループ化します。<br/>

> テーブルフィールド：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)<br/>

```
function groupFieldsFormatter(type, options, data) {
    return ['month'];
}
```

#### 12.4 例示の効果
![上級関数機能_グループフィールド関数](../_images/jp/上級関数機能_グループフィールド関数.gif)
<br>
<br>
<br>

<h4 id="self-group2"></h4>

### **13. テーブル：グループヘッダーの書式設定関数{groupFormatter}**

<mark>注意</mark>：`グループフィールド関数`と併用する必要があります。

#### 13.1 なぜ使用するのか？
groupFormatter関数を使用することで、テーブル内のグループヘッダーの表示内容やスタイルをカスタマイズし、特定のビジネスニーズや視覚デザイン要件を満たすことができます。

#### 13.2 パラメータの説明
`colTotal`：テーブルの総列数。<br/>
`tableData`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`templateData`：すべての印刷データ。<br/>
`groupData`：現在のグループのグループフィールド名とグループデータのオブジェクト。groupData.rowsでグループデータを照会できます。groupData.XXXで現在のグループフィールド情報を取得できます。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`numberFormat`：データをカスタマイズして書式設定するための関数。<br/>
`columnsFormats`：配列タイプで、配列内のオブジェクトには以下の3つのプロパティが含まれます：
- `columnsFormats[index].colnumIndex`：現在の列がテーブル内で持つインデックス位置。0から始まります。<br/>
- `columnsFormats[index].format`：列のデータ形式。例えば'#,##0'。<br/>
- `columnsFormats[index].dataType`：列のデータ型。<br/>

<div id="groupFormatter"></div>

#### 13.3 例示のロジック
> テーブルを[月]でグループ化し、グループヘッダーを生成します。<br/>
> グループヘッダーの内容：{グループフィールド値}+"月のデータは以下の通りです："。【HTMLスタイル：改行なし、一行で全列を占める、中央揃え、青色の文字】<br/>

> テーブルフィールド：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)<br/>

```
function groupFormatter(colTotal, tableData, templateData, groupData, options, numberFormat, columnsFormats) {
    return `<td class="hi-td-center" style="color: blue; text-align: center;" colspan="${colTotal}">${groupData.month}月のデータは以下の通りです：</td>`;
}
```

#### 13.4 例示の効果
![上級関数機能_グループヘッダーの書式設定関数](../_images/jp/上級関数機能_グループヘッダーの書式設定関数.gif)
<br>
<br>
<br>

<h4 id="self-group3"></h4>

### **14. テーブル：グループフッターの書式設定関数{groupFooterFormatter}**

<mark>注意</mark>：`グループフィールド関数`と併用する必要があります。

#### 14.1 なぜ使用するのか？
groupFooterFormatter関数を使用することで、テーブル内のグループフッターの表示内容やスタイルをカスタマイズし、特定のビジネスニーズや視覚デザイン要件を満たすことができます。

#### 14.2 パラメータの説明
`colTotal`：テーブルの総列数。<br/>
`tableData`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`templateData`：すべての印刷データ。<br/>
`groupData`：現在のグループのグループフィールド名とグループデータのオブジェクト。groupData.rowsでグループデータを照会できます。groupData.XXXで現在のグループフィールド情報を取得できます。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`numberFormat`：データをカスタマイズして書式設定するための関数。<br/>
`columnsFormats`：配列タイプで、配列内のオブジェクトには以下の3つのプロパティが含まれます：<br/>
- `columnsFormats[index].colnumIndex`：現在の列がテーブル内で持つインデックス位置。0から始まります。<br/>
- `columnsFormats[index].format`：列のデータ形式。例えば'#,##0'。<br/>
- `columnsFormats[index].dataType`：列のデータ型。<br/>

#### 14.3 例示のロジック
> テーブルを[月]でグループ化し、グループフッターを生成します。<br/>
> グループフッターの内容として、4つのtdタグを返します：<br/>
> 1. "集計："；【HTMLスタイル：赤色の文字、左右中央揃え、2列にわたる】<br/>
> 2. 数量カウント：{グループ内のレコードの数量集計値}、数値型の数量値を累計；【HTMLスタイル：左揃え、1列にわたる】<br/>
> 3. 単価合計：{グループ内のレコードの単価集計値}、数値型の単価値を累計；【HTMLスタイル：左揃え、1列にわたる】<br/>
> 4. 金額合計：{グループ内のレコードの金額集計値}、数値型の金額値を累計；【HTMLスタイル：左揃え、1列にわたる】<br/>

> テーブルフィールド：productName(商品名 ／ 品名),quantity(数量),unitPrice(単価),amount(金額),month(月)<br/>

```
function groupFooterFormatter(colTotal, tableData, templateData, groupData, options, numberFormat, columnsFormats) {
    let quantitySum = 0;
    let unitPriceSum = 0;
    let amountSum = 0;
    groupData.rows.forEach(function(data) {
        quantitySum += parseInt(data.quantity, 10); 
        unitPriceSum += parseFloat(data.unitPrice); 
        amountSum += parseFloat(data.amount); 
    });
    return `
        <td class="hi-td-center" colspan="2" style="color: red; text-align: center;">集計：</td>
        <td class="hi-td-left" style="text-align: left;">数量カウント：${quantitySum}</td>
        <td class="hi-td-left" style="text-align: left;">単価合計：${unitPriceSum.toFixed(2)}</td>
        <td class="hi-td-left" style="text-align: left;">金額合計：${amountSum.toFixed(2)}</td>`;
}
```

#### 14.4 例示の効果
![上級関数機能_グループフッターの書式設定関数](../_images/jp/上級関数機能_グループフッターの書式設定関数.gif)
<br>
<br>
<br>

### **15. テーブル：複数テーブルのフッター関数{gridColumnsFooterFormatter}**

#### 15.1 なぜ使用するのか？
データ分析、レポート生成などの場面で、この関数を使用することで、テーブルのフッターにカスタマイズされた統計情報を含む複数のフッターを追加できます。この機能は、テーブルデータの総計やその他の統計情報をユーザーに示す際に非常に有用です。大量のデータを閲覧するユーザーにとって、明確な総計や統計情報はデータの規模や特徴を迅速に把握する助けとなります。

#### 15.2 パラメータの説明
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`rowsData`：現在のテーブルのすべての行データの配列で、広範なデータコンテキストにアクセスするために使用されます。<br/>
`templateData`：すべての印刷データ。<br/>
`pageData`：現在のテーブルのすべての行データの配列（空行データを含む）で、広範なデータコンテキストにアクセスするために使用されます。<br/>

#### 15.3 例示のロジック
> テーブルのレコード数をカウントし、複数のフッターを生成する【HTMLスタイル：赤色の文字】。<br/>

```
function gridColumnsFooterFormatter(options, rowsData, templateData, pageData) {
    let rowCount = rowsData.length;
    return `<span style="color:red;">${rowCount} 行</span>`; 
}
```

#### 15.4 例示の効果
![上級関数機能_複数テーブルのフッター関数](../_images/jp/上級関数機能_複数テーブルのフッター関数.gif)
<br>
<br>
<br>

### **16. グラフ：レンダリング関数{eChartsOption}**

#### 16.1 なぜ使用するのか？
eChartsOption関数を使用することで、ニーズに応じてグラフの設定フィールドをカスタマイズし、データを正確に表示できるようにします。例えば、販売データのレポートがあり、異なる期間における製品の販売額を示す必要がある場合、縦棒グラフを使用してこれらのデータを表示し、eChartsOption関数を通じてグラフの設定をカスタマイズできます。

#### 16.2 パラメータの説明
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`templateData`：すべての印刷データ。<br/>
`echarts`：echarts.jsのコンポーネント。<br/>
`chart`：echarts.jsが初期化された後の現在の要素のechartsプロパティ。<br/>
`columns`：配列型、現在のグラフ要素に対応するテーブル要素のすべての列情報。<br/>

####  ① 縦棒グラフ
###### 例示のロジック
```
1. データレイアウト：積み重ねしない。
2. X軸設定：タイトル（options.customTitle）フィールドが空でない場合は「,」で区切ってタイトルとして使用し、タイトル（options.customTitle）フィールドが空の場合はテーブルのタイトルを使用する。
3. Y軸設定：フィールド値。
4. スタイル要件：
 - カラースキーム：棒の色はテーブルの記録分類に従って、浅い青から深い青まで。
 - フォント：Arialフォント、フォントサイズは12pt、色は濃い灰色(#444444)。
 - 背景とグリッドライン：背景はクリーム色(#F8F8F8)、Y軸とX軸のグリッドラインは細い点線、色は薄い灰色(#DDDDDD)。
 ```

###### サンプルコード

```
function eChartsOption(options, templateData) {
    let histogramTable = templateData?.histogramTable || [];
    let categories = []; // X軸データカテゴリ
    let seriesData = []; // シリーズデータ
    let colorPalette = ['#87CEFA', '#1E90FF']; // 淡い青から濃い青へのカラーグラデーション

    histogramTable.forEach((item, index) => {
        for (let key in item) {
            if (categories.indexOf(key) === -1) {
                categories.push(key);
            }
            if (!seriesData[index]) {
                seriesData[index] = {
                    name: key,
                    type: 'bar',
                    stack: null, // スタックしない
                    data: [],
                    itemStyle: {
                        color: colorPalette[index % colorPalette.length] // 色を循環して使用
                    }
                };
            }
            seriesData[index].data.push(item[key]);
        }
    });

    let xAxisData = options.customTitle ? options.customTitle.split(',') : categories;

    let option = {
        backgroundColor: '#F8F8F8', // 背景色：アイボリー
        textStyle: {
            fontFamily: 'Arial',
            fontSize: 12,
            color: '#444444' // フォントスタイル
        },
        xAxis: {
            type: 'category',
            data: xAxisData,
            axisLine: {lineStyle: {color: '#DDDDDD', type: 'dashed'}}, // X軸のグリッド線
            axisTick: {show: false},
            axisLabel: {textStyle: {color: '#444444'}}
        },
        yAxis: {
            type: 'value',
            splitLine: {lineStyle: {color: '#DDDDDD', type: 'dashed'}} // Y軸のグリッド線
        },
        series: seriesData
    };

    return option;
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_縦棒グラフ](../_images/jp/上級関数機能_レンダリング関数_縦棒グラフ.gif)
<br>
<br>
<br>

#### ② 折れ線グラフ
###### 例示のロジック
```
1. X軸設定：タイトル（`options.customTitle`）フィールドが空でない場合は「,」で区切ってタイトルとして使用し、タイトル（`options.customTitle`）フィールドが空の場合はテーブルのタイトルを使用する。
2. Y軸設定：フィールド値。
3. スタイル要件：
 - カラースキーム：線の色はテーブルの記録分類に従って、異なる色を表示します。
 - 線上に値を表示します。
```

###### サンプルコード

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // x軸データとシリーズデータを初期化
  let xAxisData = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
  let seriesData = [[150, 230, 224, 218, 135, 147, 260]];
  // optionsとtemplateDataの存在をチェック
  if (options && options.field && templateData) {
    // templateDataからフィールドデータ文字列を取得
    let fieldDataStr = templateData[options.field];
    // fieldDataStrが存在し、かつ長さが0より大きい場合
    if (fieldDataStr && fieldDataStr.length > 0) {
      // x軸データをfieldDataStrの最初のオブジェクトのキーに設定
      xAxisData = Object.keys(fieldDataStr[0]);
      // カスタムタイトルがある場合
      if (options.customTitle) {
        // カスタムタイトル配列でx軸データを置き換える
        let customTitles = options.customTitle.split(',');
        xAxisData = customTitles.map(item => {
          return item;
        });
      } 
      // そうでなければ、列定義がある場合
      else if (columns && columns.length > 0) {
        // 列定義のタイトルに基づいてx軸データを置き換える
        xAxisData = xAxisData.map(item => {
          const matchColumn = columns.find(column => column.field === item);
          return (matchColumn && matchColumn.title) ? matchColumn.title : item;
        });
      }
      // seriesDataをクリア
      seriesData = [];
      // fieldDataStrをループして、各オブジェクトの値をseriesDataにプッシュ
      fieldDataStr.forEach(item => {
        seriesData.push(Object.values(item));
      });
    }
  }
  // 各シリーズデータに対してオブジェクトを作成し、タイプを「line」に設定
  let series = seriesData.map(function(data) {
    return {
      data: data,
      type: "line",
    };
  });
  // optionオブジェクトを構築
  let option = {
    xAxis: {
      type: "category",  // x軸タイプをカテゴリ型に設定
      data: xAxisData,   // x軸データを設定
    },
    yAxis: {
      type: "value",     // y軸タイプを数値型に設定
    },
    series: series,      // シリーズデータを設定
    tooltip: {
      trigger: 'axis'    // 折れ線上に値を表示
    }
  };
  // optionオブジェクトを返す
  return option;
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_折れ線グラフ](../_images/jp/上級関数機能_レンダリング関数_折れ線グラフ.gif)
<br>
<br>
<br>

#### ③ 円グラフ
###### 例示のロジック
```
1. ラベル：タイトル（`options.customTitle`）フィールドが空でない場合は「,」で区切ってラベルとして使用し、タイトル（`options.customTitle`）フィールドが空の場合はテーブルのタイトルをラベルとして使用する。
2. スタイル要件：エッジが滑らかで、ハイライト時に拡大します。
```

###### サンプルコード

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // シリーズデータを初期化してデフォルトの円グラフ値に設定
  let seriesData = [
    { value: 1048, name: "Search Engine" },
    { value: 735, name: "Direct" },
    { value: 580, name: "Email" },
    { value: 484, name: "Union Ads" },
    { value: 300, name: "Video Ads" },
  ];
  // optionsとtemplateDataが存在し、かつfieldプロパティが存在するか確認
  if (options && options.field && templateData) {
    // templateDataから指定されたfieldのデータを取得
    let fieldDataStr = templateData[options.field];
    // fieldDataStrが存在し、かつ長さが0より大きい場合
    if (fieldDataStr && fieldDataStr.length > 0) {
      // シリーズデータをクリア
      seriesData = [];
      // カスタムタイトルがある場合
      if (options.customTitle) {
        // カンマで区切られたカスタムタイトル配列を使用してseriesDataを生成
        let customTitles = options.customTitle.split(',');
        let values = Object.values(fieldDataStr[0]);
        seriesData = customTitles.map((item, index) => {
          return { value: values[index], name: item };
        });
      } 
      // それ以外で列定義がある場合
      else if (columns && columns.length > 0) {
        // 列定義のタイトルに基づいてseriesDataを生成
        Object.keys(fieldDataStr[0]).forEach(key => {
          const matchColumn = columns.find(column => column.field === key);
          const name = matchColumn && matchColumn.title ? matchColumn.title : key;
          seriesData.push({ value: fieldDataStr[0][key], name });
        });
      } 
      // カスタムタイトルや列定義がない場合
      else {
        // fieldDataStrのキーと値を使用して直接seriesDataを生成
        Object.keys(fieldDataStr[0]).forEach(key => {
          seriesData.push({ value: fieldDataStr[0][key], name: key });
        });
      }
    }
  }
  // optionオブジェクトを構築
  let option = {
    series: [
      {
        type: 'pie',                // グラフタイプを円グラフに設定
        radius: ['40%', '70%'],     // 円グラフの内外半径を設定
        avoidLabelOverlap: false,   // ラベルの重なりを避ける
        itemStyle: {
          borderRadius: 10,         // 境界の角丸を設定
          borderColor: '#fff',      // 境界の色を設定
          borderWidth: 2            // 境界の幅を設定
        },
        label: {
          show: true,               // ラベルを表示
          position: 'outside',      // ラベルの位置を外部に設定
          formatter: '{b}: {d}%',   // ラベルフォーマット：名前と割合を表示
          textStyle: { fontSize: 12 } // ラベル文字サイズを設定
        },
        emphasis: { scale: 1.1 },    // 強調スタイルを設定し、1.1倍に拡大
        data: seriesData            // 円グラフデータを設定
      }
    ]
  };
  // optionオブジェクトを返す
  return option;
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_円グラフ](../_images/jp/上級関数機能_レンダリング関数_円グラフ.gif)
<br>
<br>
<br>

#### ④ レーダーグラフ
###### 例示のロジック
```
1. タイトルの出所：タイトル（`options.customTitle`）フィールドが空でない場合は「,」で区切ってラベルとして使用し、タイトル（`options.customTitle`）フィールドが空の場合はテーブルのタイトルをラベルとして使用する。
2. スタイル要件：Arialフォント、フォントサイズは12pt、フォントカラーは黒色。
```

###### サンプルコード

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // 初期化レーダーチャートの指標データとシリーズデータ
  let indicatorData = [
    { name: "Sales" },
    { name: "Administration" },
    { name: "Information Technology" },
    { name: "Customer Support" },
    { name: "Development" },
    { name: "Marketing" },
  ];
  let seriesData = [
    { value: [4200, 3000, 20000, 35000, 50000, 18000] },
    { value: [5000, 14000, 28000, 26000, 42000, 21000] },
  ];
  // optionsとtemplateDataが存在し、field属性が存在するかを確認
  if (options && options.field && templateData) {
    // templateDataから指定されたfieldのデータを取得
    let fieldDataStr = templateData[options.field];
    // fieldDataStrが存在し、かつ長さが0より大きい場合
    if (fieldDataStr && fieldDataStr.length > 0) {
      // 指標データをクリア
      indicatorData = [];
      // fieldDataStrのキーを基に指標データを生成
      indicatorData = Object.keys(fieldDataStr[0]).map(key => ({ name: key }));
      // カスタムタイトルがある場合
      if (options.customTitle) {
        // カスタムタイトルの配列を生成し、indicatorDataを設定
        let customTitles = options.customTitle.split(',');
        indicatorData = customTitles.map(item => {
          return { name: item };
        });
      } 
      // そうでなければ、列定義がある場合
      else if (columns && columns.length > 0) {
        // 列定義に基づいてindicatorDataを生成
        indicatorData = indicatorData.map(item => {
          const matchColumn = columns.find(column => column.field === item.name);
          return { name: (matchColumn && matchColumn.title) ? matchColumn.title : item.name };
        });
      }
      // シリーズデータをクリア
      seriesData = [];
      // fieldDataStrを基にシリーズデータを生成
      seriesData = fieldDataStr.map(item => {
        return { value: Object.values(item) };
      });
    }
  }
  // optionオブジェクトの構築
  let option = {
    radar: {
      indicator: indicatorData,  // レーダーチャートの指標データを設定
      axisName: {
        fontSize: 12,            // 指標名称のフォントサイズを設定
        fontFamily: 'Arial',     // 指標名称のフォントを設定
        color: 'black'           // 指標名称の色を設定
      }
    },
    series: [
      {
        name: "Budget vs spending", // シリーズ名称を設定
        type: "radar",              // グラフタイプをレーダーチャートに設定
        data: seriesData,           // シリーズデータを設定
      },
    ],
    textStyle: {
      fontFamily: 'Arial',          // 全体のフォントを設定
      fontSize: 12,                 // 全体のフォントサイズを設定
      color: 'black'                // 全体のフォント色を設定
    },
    legend: {
      textStyle: {
        fontFamily: 'Arial',        // 凡例のフォントを設定
        fontSize: 12,               // 凡例のフォントサイズを設定
        color: 'black'              // 凡例のフォント色を設定
      }
    }
  };
  // optionオブジェクトを返す
  return option;
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_レーダーグラフ](../_images/jp/上級関数機能_レンダリング関数_レーダーグラフ.gif)
<br>
<br>
<br>

#### ⑤ 散布グラフ
###### 例示のロジック
```
1. データ列：データ列（`options.dataColumns`）フィールドが空でない場合は「,」で区切ってデータソースとして使用し、データ列（`options.dataColumns`）フィールドが空の場合はデフォルトのテーブルをデータソースとして使用する。
2. スタイル要件：散布点の値を表示します。
```

###### サンプルコード

```
function eChartsOption(options, templateData, echarts, chart, columns) {
    // 初期化系列データを空配列とする
    let seriesData = [];
    // options の dataColumns 属性からデータ列を取得
    let dataColumns = options.dataColumns ? options.dataColumns.split(',') : null;
    // 使用する列を決定。dataColumns が存在する場合はそれを使用し、存在しない場合は templateData の列を使用
    const useColumns = dataColumns || Object.keys(templateData?.scatterPlotTable[0]);
    // 使用する列数が偶数でない場合、警告を発し最後の要素を削除
    if (useColumns.length % 2 !== 0) {
        console.warn('データ列の数は偶数である必要があります。各データペアがx軸とy軸にマッピングされるようにします。');
        useColumns.pop(); // 最後の要素を削除して偶数にする
    }
    // templateData の scatterPlotTable を走査
    templateData?.scatterPlotTable.forEach(item => {
        // 2つずつデータを処理し、x軸とy軸にマッピング
        for (let i = 0; i < useColumns.length; i += 2) {
            const xKey = useColumns[i];
            const yKey = useColumns[i + 1];
            seriesData.push({
                value: [item[xKey], item[yKey]], // 散点のxとyの値を設定
                symbolSize: function(val) {
                    return val[1] ? 10 : 5; // yの値に基づいて散点のサイズを調整
                },
                label: {
                    show: true, // ラベルを表示
                    formatter: '{c}', // ラベルの内容を散点の値に設定
                    position: 'top', // ラベルの位置をトップに設定
                },
            });
        }
    });
    // eCharts の設定オブジェクトを返す
    return {
        xAxis: {
            type: 'value', // x軸のタイプを数値型に設定
        },
        yAxis: {
            type: 'value', // y軸のタイプを数値型に設定
        },
        series: [{
            data: seriesData, // シリーズデータを設定
            type: 'scatter', // グラフのタイプを散布図に設定
            symbolSize: function(val) {
                return val[1] ? 10 : 5; // yの値に基づいて散点のサイズを調整
            },
            label: {
                show: true, // ラベルを表示
                formatter: '{c}', // ラベルの内容を散点の値に設定
                position: 'top', // ラベルの位置をトップに設定
            },
        }],
        textStyle: {
            fontFamily: 'Arial', // グローバルフォントをArialに設定
            fontSize: 12, // グローバルフォントサイズを12に設定
            color: 'black', // グローバルフォントカラーを黒に設定
        },
    };
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_散布グラフ](../_images/jp/上級関数機能_レンダリング関数_散布グラフ.gif)
<br>
<br>
<br>

#### ⑥ ファンネルグラフ
###### 例示のロジック
```
1.  ラベル：タイトル（`options.customTitle`）フィールドが空でない場合は「,」で区切ってラベルとして使用し、タイトル（`options.customTitle`）フィールドが空の場合はテーブルのタイトルをラベルとして使用する。
2.  スタイル要件：
 - カラースキーム：ファネルチャートの色は表のレコード分類に従い、異なる色を表示します。
```

###### サンプルコード

```
function eChartsOption(options, templateData, echarts, chart, columns) {
  // グラフの初期データとシリーズデータの設定
  let legendData = ["Show", "Click", "Visit", "Inquiry"];
  let seriesData = [
    { value: 60, name: "Visit" },
    { value: 40, name: "Inquiry" },
    { value: 20, name: "Order" },
    { value: 80, name: "Click" },
    { value: 100, name: "Show" },
  ];
  // optionsとtemplateDataが存在し、かつfield属性が存在するか確認
  if (options && options.field && templateData) {
    // templateDataから指定されたfieldのデータを取得
    let fieldDataStr = templateData[options.field];
    // fieldDataStrが存在し、長さが0より大きい場合
    if (fieldDataStr && fieldDataStr.length > 0) {
      // fieldDataStrのキー名を初期のグラフの凡例データとして取得
      var names = Object.keys(fieldDataStr[0]);
      legendData = Object.keys(fieldDataStr[0]);
      // カスタムタイトルがある場合
      if (options.customTitle) {
        // カンマで区切られたカスタムタイトルの配列でlegendDataを置き換え
        let customTitles = options.customTitle.split(',');
        legendData = customTitles.map(item => {
          return item;
        });
      } 
      // それ以外の場合、列の定義がある場合
      else if (columns && columns.length > 0) {
        // 列の定義に基づいてlegendDataを置き換え
        legendData = legendData.map(item => {
          const matchColumn = columns.find(column => column.field === item);
          return (matchColumn && matchColumn.title) ? matchColumn.title : item;
        });
      }
      // シリーズデータを空にする
      seriesData = [];
      // fieldDataStrをループしてseriesDataを生成
      fieldDataStr.forEach(item => {
        legendData.forEach((data, index) => {
          var dataObject = {};
          dataObject['value'] = item[names[index]];
          dataObject['name'] = data;
          seriesData.push(dataObject);
        });
      });
    }
  }
  // optionオブジェクトを構築
  let option = {
    legend: {
      data: legendData, // 凡例データを設定
    },
    series: [
      {
        name: "Funnel",          // シリーズ名
        type: "funnel",          // グラフの種類を漏斗図に設定
        left: "10%",             // グラフの左マージンを設定
        top: 60,                 // グラフの上マージンを設定
        bottom: 60,              // グラフの下マージンを設定
        width: "80%",            // グラフの幅を設定
        min: 0,                  // 最小値を設定
        max: 100,                // 最大値を設定
        minSize: "0%",           // 最小サイズを設定
        maxSize: "100%",         // 最大サイズを設定
        sort: "descending",      // ソート順序を降順に設定
        gap: 2,                  // 漏斗図要素間の間隔を設定
        label: {
          show: true,            // ラベルを表示
          position: "inside"     // ラベル位置を内部に設定
        },
        labelLine: {
          length: 10,            // ラベルラインの長さ
          lineStyle: {
            width: 1,            // ラベルラインの幅
            type: "solid"        // ラベルラインのタイプ
          },
        },
        itemStyle: {
          borderColor: "#fff",   // ボーダーの色を設定
          borderWidth: 1,        // ボーダーの幅を設定
        },
        emphasis: {
          label: {
            fontSize: 20,        // 強調状態のラベルのフォントサイズを設定
          },
        },
        data: seriesData,        // シリーズデータを設定
      },
    ],
  };
  // optionオブジェクトを返す
  return option;
}
```

###### 例示の効果
![上級関数機能_レンダリング関数_ファンネルグラフ](../_images/jp/上級関数機能_レンダリング関数_ファンネルグラフ.gif)
<br>
<br>
<br>

<h4 id="self-format1"></h4>

### **17. HTML：書式設定関数{formatter}**

#### 17.1 なぜ使用するのか？
formatter関数を使用すると、特定の要件やデータ内容に基づいてデータの表示方法をカスタマイズできます。例えば、販売レポートに異なる形式の金額データが含まれている場合（ドルやユーロなど）、formatter関数を使ってこれらの金額データを統一した通貨形式に変換し、適切な通貨記号や千位区切りを追加できます。<br/>
また、リンクフィールドがある場合、formatter関数を使用してクリックすると指定されたアドレスにジャンプするように設定することもできます。

#### 17.2 パラメータの説明
`value`：具体的な要素の値。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`templateData`：すべての印刷データ。<br/>

#### 17.3 例示のロジック
> 1. データソース：templateDataのrichTextとrichImageをhtmlコンポーネントに表示します。<br/>
> 2. データ形式：<br/>
> - richTextデータ形式：テキスト<br/>
> - richImageデータ形式：画像のURL<br/>
> 3. 要件：<br/>
> - richTextの中の`プライバシーポリシー`テキストをリンクに設定し、クリックすると`https://www.opentext.com/ja-jp/about/privacy`にジャンプするようにします。<br/>

```
function formatter(value, options, templateData) {
    const richText = templateData.richText;
    const richImage = templateData.richImage;
    let htmlContent = `<div>${richText.replace('プライバシーポリシー', `<a href="https://www.opentext.com/ja-jp/about/privacy" target="_blank">プライバシーポリシー</a>`)}<br><img src="${richImage}" alt="Rich Image"></div>`;
    return htmlContent;
}
```

#### 17.4 例示の効果
![上級関数機能_HTML_書式設定関数](../_images/jp/上級関数機能_HTML_書式設定関数.gif)
<br>
<br>
<br>

### **18. 画像：書式設定関数{formatter}**

#### 18.1 なぜ使用するのか？
画像のサイズや比率を調整する必要がある場合、formatter関数は非常に有用です。例えば、報告書を印刷したり、PDF文書を生成したりする際、用紙のサイズやレイアウトの制約により、画像をページに合わせて縮小または拡大する必要があります。

#### 18.2 パラメータの説明
`title`：要素のタイトルデータ。<br/>
`value`：画像のURL。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`templateData`：すべての印刷データ。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素に直接アクセスできます。<br/>

#### 18.3 例示のロジック
> 画像サイズを50％縮小します。<br/>
```
function formatter(title, value, options, templateData, target) {
    if (!options.hasOwnProperty('isResized')) {
        options.isResized = true;
        options.width *= 0.5;
        options.height *= 0.5;
    }
    return value; 
}
```

#### 18.4 例示の効果
![上級関数機能_画像_書式設定関数](../_images/jp/上級関数機能_画像_書式設定関数.gif)
<br>
<br>
<br>

### **19. 画像：スタイル関数{styler}**

#### 19.1 なぜ使用するのか？
画像を美しく見せるために、styler関数を使用すると特定のスタイルを適用できます。例えば、商品画像に上下左右の罫線を追加し、罫線の色を青に設定することで、商品画像をより目立たせ、美しく表示することができます。

#### 19.2 パラメータの説明
`value`：画像のURL。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素に直接アクセスできます。<br/>
`templateData`：すべての印刷データ。<br/>

#### 19.3 例示のロジック
> 画像に上下左右の罫線を追加し、青色に設定します。<br/>
```
function styler(value, options, target, templateData) {
    return {
        'borderWidth': '1pt', 
        'borderColor': 'blue', 
        'borderStyle': 'solid', 
        'borderTop': '1pt solid blue',
        'borderBottom': '1pt solid blue',
        'borderLeft': '1pt solid blue',
        'borderRight': '1pt solid blue'
    };
}
```

#### 19.4 例示の効果
![上級関数機能_画像_スタイル関数](../_images/jp/上級関数機能_画像_スタイル関数.gif)
<br>
<br>
<br>

### **20. QRコード/バーコード：書式設定関数{formatter}**

#### 20.1 なぜ使用するのか？
QRコードやバーコードをカスタマイズするために、formatter関数を使用すると便利です。例えば、物流システムで、バーコードの値に他の識別子を関連付けたい場合、すべてのバーコード値の前に"ORD-"を追加することができます。

#### 20.2 パラメータの説明
`title`：要素のタイトルデータ。<br/>
`value`：具体的な要素の値。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`templateData`：すべての印刷データ。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素に直接アクセスできます。<br/>

#### 20.3 例示のロジック
> バーコード値の前に"ORD-"プレフィックスを追加します。

```
function formatter(title, value, options, templateData, target) { 
    var barcodeValue = 'ORD-' + value;
    return barcodeValue;
}
```

#### 20.4 例示の効果
![上級関数機能_QRコードバーコード_書式設定関数](../_images/jp/上級関数機能_QRコードバーコード_書式設定関数.gif)
<br>
<br>
<br>

### **21. QRコード/バーコード：スタイル関数{styler}**

#### 21.1 なぜ使用するのか？
styler関数を使用して、QRコードやバーコードの色、罫線、サイズなどのスタイルプロパティを制御できます。例えば、物流追跡システムでは、出荷済みのバーコードを緑色に設定し、返品または異常のバーコードを赤色に設定することができます。

#### 21.2 パラメータの説明
`value`：具体的な要素の値。<br/>
`options`：現在の要素のすべてのプロパティを含むオブジェクトで、ロジックの判断や特定情報の取得に使用します。<br/>
`target`：外部のdiv要素のDOM情報を含むオブジェクトで、後続のスタイル設定時にターゲット要素に直接アクセスできます。<br/>
`templateData`：すべての印刷データ。<br/>

#### 21.3 例示のロジック
> バーコードの色を緑色に設定します。また、上下左右の罫線を青色に設定します。<br/>
```
function styler(value, options, target, templateData) {
    return {
        color: 'green', 
        border: '1px solid blue' 
    };
}
```

#### 21.4  例示の効果
![上級関数機能_QRコードバーコード_スタイル関数](../_images/jp/上級関数機能_QRコードバーコード_スタイル関数.gif)
<br>
<br>
<br>