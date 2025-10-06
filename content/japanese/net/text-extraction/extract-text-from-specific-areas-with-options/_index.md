---
title: オプションを使用して特定の領域からテキストを抽出する
linktitle: オプションを使用して特定の領域からテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメント内の特定の領域からテキストを抽出する方法を学習します。このチュートリアルで、高度なテキスト抽出オプションを調べます。
weight: 14
url: /ja/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# オプションを使用して特定の領域からテキストを抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、カスタマイズ可能なオプションを使用してドキュメント内の特定の領域からテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式からテキストを簡単に解析および抽出できるようにする強力なライブラリです。
## 前提条件
コーディングに入る前に、次のものを用意しておいてください。
1. 開発環境: Visual Studio またはその他の .NET 開発 IDE をインストールします。
2.  GroupDocs.Parserライブラリ: GroupDocs.Parser for .NETをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル ファイル: テキストを抽出するサンプル ドキュメント (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Parser クラスとメソッドにアクセスするために必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
インスタンスを初期化する`Parser`サンプル ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //テキスト領域抽出のコードはここに記述します
}
```
## ステップ2: テキスト領域の抽出オプションを定義する
作成する`PageTextAreaOptions`テキスト抽出の基準を指定します。
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
この例では、
- `"\\s[a-z]{2}\\s"`小文字のみを含むテキスト領域に一致する正規表現パターンです。
- `new Rectangle(new Point(0, 0), new Size(300, 100))`ページ上のテキストを抽出する四角形 (位置とサイズ) を定義します。
## ステップ3: テキスト領域を抽出する
定義されたオプションを使用して、指定された条件を満たすテキスト領域を抽出します。
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## ステップ4: 抽出されたテキスト領域をチェックして反復する
テキスト領域の抽出がサポートされているかどうかを確認し、抽出された領域を反復処理します。
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント内の特定の領域からテキストを抽出する方法について説明しました。このライブラリは、さまざまなドキュメント形式を解析するための広範な機能を提供するため、テキスト抽出タスクに役立つツールとなります。

## よくある質問
### GroupDocs.Parser はスキャンされたドキュメントからテキストを抽出できますか?
はい、GroupDocs.Parser はスキャンされたドキュメントの OCR ベースのテキスト抽出をサポートしています。
### GroupDocs.Parser は複数のドキュメント形式と互換性がありますか?
はい、PDF、DOCX、XLSX、PPTX、その他の一般的な形式からテキストを解析して抽出できます。
### GroupDocs.Parser は .NET Core をサポートしていますか?
はい、GroupDocs.Parser は .NET Core および .NET Framework と互換性があります。
### GroupDocs.Parser を使用してテキストとともにメタデータを抽出できますか?
はい、ドキュメントからテキストコンテンツとメタデータの両方を抽出できます。
### GroupDocs.Parser の試用版はありますか?
はい、無料トライアルをご利用いただけます[ここ](https://releases.groupdocs.com/).