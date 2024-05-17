---
title: 抽出されたデータ内のテーブルの操作
linktitle: 抽出されたデータ内のテーブルの操作
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからテーブル データを抽出する方法を学習します。定義済みのテンプレートを使用して構造化コンテンツを効率的に解析します。
type: docs
weight: 12
url: /ja/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント内のテーブルからデータを抽出する方法について説明します。GroupDocs.Parser は、開発者が PDF、DOCX、XLSX などのさまざまなファイル形式からテキスト、メタデータ、構造化コンテンツを解析して抽出できるようにする強力なツールです。具体的には、定義済みのテンプレートを使用してテーブル データを効率的に抽出することに焦点を当てます。
## 前提条件
始める前に、以下のものが用意されていることを確認してください。
- マシンに Visual Studio がインストールされています。
- C# および .NET フレームワークの基本的な理解。
- NuGet パッケージ マネージャー経由でインストールされた GroupDocs.Parser ライブラリ。

## 名前空間のインポート
まず、GroupDocs.Parser および関連機能を使用するために必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ステップ1: テーブルテンプレートを作成する
テーブルからデータを抽出するには、まず、抽出するテーブルの構造を表すテンプレートを定義します。ドキュメント内でのテーブルの位置とサイズを指定します。
```csharp
//テーブルパラメータ（場所とサイズ）を定義する
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
//パラメータ付きのテーブルテンプレートを作成する
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## ステップ2: テンプレートを定義する
定義したテーブル テンプレートを含むテンプレートを作成します。このテンプレートは、テーブル データを抽出するときに何を探すべきかをパーサーに指示します。
```csharp
//テーブルを使用してテンプレートを作成する
Template template = new Template(new TemplateItem[] { table });
```
## ステップ3: ドキュメントを解析してテーブルデータを抽出する
GroupDocs.Parser の Parser クラスを利用して、定義したテンプレートを使用して特定のドキュメントを解析します。
```csharp
//サンプルファイルへのパスを指定します
string filePath = "YourSampleFile.pdf";
//Parserクラスのインスタンスを作成する
using (Parser parser = new Parser(filePath))
{
    //テンプレートに従ってドキュメントを解析する
    DocumentData data = parser.ParseByTemplate(template);
    //抽出されたすべてのデータを反復処理する
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        //抽出されたフィールドがテーブルであるかどうかを確認する
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        //テーブル行を反復処理する
        for (int row = 0; row < area.RowCount; row++)
        {
            //テーブル列を反復処理する
            for (int column = 0; column < area.ColumnCount; column++)
            {
                //セルの値を取得する
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                //セルの値を出力します（nullの場合は空の文字列）
                Console.Write(cellValue == null ? "" : cellValue.Text);
                //列間にタブスペースを印刷する
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            //各行を印刷した後、次の行に移動する
            Console.WriteLine();
        }
    }
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテーブル データを抽出する方法について説明しました。テンプレートを定義し、解析メソッドを利用することで、開発者はさまざまなファイル形式からテーブルなどの構造化データを効率的に抽出できます。

## よくある質問
### GroupDocs.Parser はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いファイル形式をサポートしています。
### ドキュメント内の特定の領域からデータを抽出できますか?
はい、ドキュメント内の特定の領域 (表など) を抽出対象とするテンプレートを定義できます。
### GroupDocs.Parser は大きなドキュメントに適していますか?
はい、GroupDocs.Parser は大きなドキュメントを効率的に処理するように最適化されており、開発者はデータをシームレスに抽出できます。
### GroupDocs.Parser は構造化データとともにテキスト抽出をサポートしていますか?
はい、構造化データの抽出 (テーブルなど) に加えて、GroupDocs.Parser はドキュメントからプレーンテキストとメタデータを抽出できます。
### GroupDocs.Parser の統合に関するサポートや支援を受けるにはどうすればよいですか?
サポートとディスカッションについては、GroupDocsコミュニティフォーラムをご覧ください。[ここ](https://forum.groupdocs.com/c/parser/17).