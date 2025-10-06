---
title: Excel ドキュメントからテキストを HTML として抽出する
linktitle: Excel ドキュメントからテキストを HTML として抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して Excel ドキュメントからテキストを抽出し、HTML に変換する方法を学習します。
weight: 13
url: /ja/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# Excel ドキュメントからテキストを HTML として抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Excel ドキュメントからテキストを抽出し、HTML 形式に変換する方法について説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式を操作して、テキストとメタデータを効率的に抽出できるようにする強力なライブラリです。
## 前提条件
始める前に、次の設定がされていることを確認してください。
- Visual Studio がシステムにインストールされています。
- C# プログラミングの基本的な理解。
-  .NET用のGroupDocs.Parserライブラリ。ここからダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/).
## 名前空間のインポート
まず、GroupDocs.Parser 機能にアクセスするために必要な名前空間を C# プロジェクトに含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser` Excel ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //追加のコードはここに記載します
}
```
交換する`"YourSampleFile.xlsx"` Excel ファイルへのパスを入力します。
## ステップ2: テキストをHTMLとして抽出する
以内`using`ブロックの`Parser`たとえば、`GetFormattedText` HTML モードでフォーマットされたテキストを抽出する方法。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //追加のコードはここに記載します
    }
}
```
## ステップ3: 抽出したHTMLテキストを読み取って印刷する
次に、抽出したHTMLテキストを`TextReader`コンソールに出力します。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
このコードを実行すると、Excel ドキュメントからテキストが抽出され、コンソールに HTML 形式で表示されます。
## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Excel ドキュメントからテキストを抽出し、HTML 形式に変換する方法を学習しました。このライブラリは、さまざまなドキュメント形式を簡単に操作する方法を提供し、開発者がアプリケーションでテキスト抽出タスクを効率的に処理できるようにします。

## よくある質問
### GroupDocs.Parser は Excel 以外のドキュメント形式も処理できますか?
はい、GroupDocs.Parser は PDF、Word、PowerPoint など、幅広いファイル形式をサポートしています。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Parser はテキスト抽出中に書式を保持しますか?
はい、GroupDocs.Parser はテキスト抽出時にフォント、スタイル、レイアウトなどの書式設定を保持できます。
### GroupDocs.Parser を使用してドキュメントからメタデータを抽出できますか?
はい、GroupDocs.Parser を使用すると、サポートされているドキュメント タイプから作成者、作成日などのメタデータを抽出できます。
### GroupDocs.Parser の無料トライアルはありますか?
はい、無料トライアルはここからダウンロードできます。[ここ](https://releases.groupdocs.com/).