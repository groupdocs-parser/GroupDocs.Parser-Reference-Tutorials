---
title: ドキュメントから表を抽出する
linktitle: ドキュメントから表を抽出する
second_title: GroupDocs.Parser .NET API
description: Groupdocs.Parser for .NET を使用してドキュメントからテーブルを抽出する方法を学びます。この機能の統合に関する詳細なガイドに従ってください。
type: docs
weight: 10
url: /ja/net/table-extraction/extract-tables-from-document/
---
## 導入
Groupdocs.Parser for .NET は、ドキュメント解析を容易にする包括的なライブラリであり、ドキュメントからテーブル、テキスト、メタデータなどの貴重な情報を抽出できます。このチュートリアルでは、Groupdocs.Parser API を使用してドキュメントからテーブルを抽出することに特に焦点を当てます。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio がシステムにインストールされています。
- .NET Framework または .NET Core がインストールされています。
- C# プログラミングの基礎知識。

## 名前空間のインポート
まず、Groupdocs.Parser クラスとメソッドにアクセスするために必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## ステップ1: パーサークラスのインスタンスを作成する
新しいインスタンスを初期化する`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここにコードを入力してください
}
```
## ステップ2: テーブル抽出のサポートを確認する
ドキュメントがテーブル抽出をサポートしているかどうかを確認するには、`Features`の財産`Parser`クラス。
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## ステップ3: テーブルレイアウトを定義する
抽出したいテーブルのレイアウトを定義するには、`TemplateTableLayout`ドキュメントの構造に基づいて列の幅と行の高さを指定します。
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## ステップ4: テーブル抽出オプションを設定する
作成する`PageTableAreaOptions`定義されたレイアウトを使用して、テーブルを抽出する方法を指定します。
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## ステップ5: テーブルを抽出する
活用する`GetTables`方法の`Parser`指定されたオプションに基づいてドキュメントからテーブルを抽出するクラス。
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## ステップ 6: テーブル データの反復処理とアクセス
抽出されたテーブルとそれぞれの行と列を反復処理して、セル データにアクセスします。
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## 結論
このチュートリアルでは、Groupdocs.Parser for .NET を使用してドキュメントからテーブルを効率的に抽出する方法について説明しました。このライブラリの機能を活用することで、テーブル抽出を .NET アプリケーションにシームレスに統合できます。

## よくある質問
### Groupdocs.Parser はさまざまなドキュメント形式を処理できますか?
はい、Groupdocs.Parser は、DOCX、PDF、XLSX など、幅広いドキュメント形式をサポートしています。
### Groupdocs.Parser for .NET の試用版はありますか?
はい、無料トライアルはここからダウンロードできます。[ここ](https://releases.groupdocs.com/).
### Groupdocs.Parser 関連のクエリのサポートを受けるにはどうすればよいですか?
訪問することができます[Groupdocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)援助をお願いします。
### Groupdocs.Parser のライセンスはどこで購入できますか?
ライセンスは以下から購入できます[ここ](https://purchase.groupdocs.com/buy).
### 評価目的で一時ライセンスを取得するにはどうすればよいですか?
臨時免許証を取得できます[ここ](https://purchase.groupdocs.com/temporary-license/).