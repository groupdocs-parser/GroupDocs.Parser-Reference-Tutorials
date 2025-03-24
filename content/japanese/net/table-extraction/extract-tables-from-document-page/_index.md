---
title: ドキュメントページから表を抽出する
linktitle: ドキュメントページから表を抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、プログラムによってドキュメントからテーブルを抽出する方法を学習します。この包括的なチュートリアルでは、ステップバイステップのガイダンスを提供します。
weight: 11
url: /ja/net/table-extraction/extract-tables-from-document-page/
---

# ドキュメントページから表を抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント ページからテーブルを抽出する方法について説明します。GroupDocs.Parser は、開発者が PDF、DOCX、XLSX などのさまざまなドキュメント形式を操作できるようにする強力なライブラリです。その機能を活用することで、これらのドキュメントからテーブルなどの構造化データを効率的に抽出し、プログラムで情報を操作および分析できるようになります。
## 前提条件
始める前に、次のものを用意してください。
- マシンに Visual Studio がインストールされています。
- C# および .NET 開発に関する基本的な理解。
-  GroupDocs.Parser for .NETライブラリ。ここからダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/).
- 抽出用のテーブルを含むサンプル ドキュメント (PDF、DOCX など) にアクセスします。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
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
インスタンス化する`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //コードはここに続きます...
}
```
## ステップ2: ドキュメントテーブル抽出のサポートを確認する
続行する前に、ドキュメントがテーブル抽出をサポートしているかどうかを確認してください。
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## ステップ3: テーブルレイアウトを定義する
ドキュメントから抽出する表のレイアウトを定義します。ドキュメントの構造に応じて列の幅と行の高さを指定します。
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  //列幅
    new double[] { 325, 340, 365, 395 });         //行の高さ
```
## ステップ4: テーブル抽出オプションを構成する
指定されたレイアウトを使用してテーブル抽出のオプションを作成します。
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## ステップ5: ドキュメント情報を取得する
ページ数を含むドキュメントに関する情報を取得します。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ステップ6: ドキュメントページを反復処理する
ドキュメントの各ページを反復処理してテーブルを抽出します。
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //現在のページから表を抽出します
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    //抽出されたテーブルを反復処理する
    foreach (PageTableArea table in tables)
    {
        //テーブルの行を反復処理する
        for (int row = 0; row < table.RowCount; row++)
        {
            //テーブルの列を反復処理する
            for (int column = 0; column < table.ColumnCount; column++)
            {
                //表のセルを取得する
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    //表セルのテキストを印刷する
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント ページからテーブルを抽出するプロセスについて説明しました。提供されている手順に従うことで、テーブル抽出機能を .NET アプリケーションにシームレスに統合し、ドキュメント内の構造化データの効率的な処理と操作が可能になります。

## よくある質問
### GroupDocs.Parser はあらゆる種類のドキュメントからテーブルを抽出できますか?
GroupDocs.Parser は、PDF、DOCX、XLSX などのさまざまなドキュメント形式をサポートしており、互換性のあるファイル タイプからのテーブル抽出を可能にします。
### GroupDocs.Parser for .NET は大規模なドキュメント処理に適していますか?
はい、GroupDocs.Parser は大きなドキュメントを効率的に処理するように設計されているため、大規模なデータセットの処理に適しています。
### GroupDocs.Parser はテーブル抽出中に書式を保持しますか?
はい、GroupDocs.Parser は、表の抽出中にセルの境界線、テキスト スタイル、配置などの書式設定の詳細を保持します。
### コンテンツ基準に基づいて特定のテーブルを抽出できますか?
GroupDocs.Parser は、レイアウト テンプレートまたは抽出のコンテンツ条件に基づいて特定のテーブルをターゲットにする柔軟なオプションを提供します。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser は .NET Framework 環境と .NET Core 環境の両方と互換性があります。