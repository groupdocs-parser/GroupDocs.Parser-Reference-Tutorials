---
title: Word 文書からテキストを HTML として抽出する
linktitle: Word 文書からテキストを HTML として抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出し、HTML として保存する方法を学びます。コード例を使用したステップバイステップのチュートリアルです。
weight: 16
url: /ja/net/word-document-processing/extract-text-from-word-document-as-html/
type: docs
---
# Word 文書からテキストを HTML として抽出する

## 導入
GroupDocs.Parser for .NET は、開発者がさまざまなファイル形式からテキストとメタデータをシームレスに抽出できるようにする強力なドキュメント解析ライブラリです。このチュートリアルでは、GroupDocs.Parser を利用して Word ドキュメントからテキストを抽出し、それを HTML として保存することに焦点を当てます。このプロセスは、コンテンツ分析、インデックス作成、ドキュメントを Web 対応形式に変換するなどのタスクに不可欠です。このガイドを読み終えると、.NET アプリケーションで GroupDocs.Parser を効率的に使用する方法を明確に理解できるようになります。
## 前提条件
このチュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
- C# プログラミングの基礎知識。
- 開発マシンに Visual Studio がインストールされています。
-  GroupDocs.Parser for .NETライブラリ。ここからダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/).
- テスト目的でサンプル Word 文書にアクセスします。
## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出し、HTML として保存するには、次の詳細な手順に従います。
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル Word 文書へのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ステップ 2 に進みます...
}
```
交換する`"YourSampleFile.docx"`Word 文書へのパスを入力します。
## ステップ2: フォーマットされたテキストをHTMLとして抽出する
次に、`GetFormattedText`方法とともに`FormattedTextOptions`テキストを HTML 形式で抽出するには:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //フォーマットされたテキストをリーダーに抽出する
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //ステップ 3 に進みます...
    }
}
```
## ステップ3: 抽出したHTMLを読み取って出力する
最後に、抽出したHTMLコンテンツを`TextReader`コンソールに出力します:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //フォーマットされたテキストをリーダーに抽出する
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //フォーマットされたテキストをHTMLとして印刷する
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出し、HTML として保存する方法について説明しました。このライブラリは、文書の内容を解析するための簡単で効率的な方法を提供するため、.NET アプリケーションでの文書処理タスクにとって非常に役立つツールとなります。

## よくある質問
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを申請するには[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser の詳細なドキュメントはどこで見つかりますか?
詳細なドキュメントが利用可能[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser の無料トライアルはありますか?
はい、無料試用版にアクセスできます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のサポートを受けるにはどうすればよいですか?
サポートフォーラムにアクセスする[ここ](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser はどのような種類のドキュメントをサポートしていますか?
GroupDocs.Parser は、Word、PDF、Excel、PowerPoint など、さまざまなドキュメント形式をサポートしています。