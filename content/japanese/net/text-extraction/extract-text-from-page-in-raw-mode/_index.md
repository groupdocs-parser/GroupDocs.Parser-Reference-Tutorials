---
title: ページからテキストをRawモードで抽出する
linktitle: ページからテキストをRawモードで抽出する
second_title: GroupDocs.Parser .NET API
description: この包括的なチュートリアルでは、Groupdocs.Parser for .NET を使用してドキュメント ページから効率的にテキストを抽出する方法を学習します。
weight: 17
url: /ja/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## 導入
このチュートリアルでは、Groupdocs.Parser for .NET を使用して、ドキュメント ページからテキストを raw モードで抽出する方法を学習します。このライブラリは、さまざまなファイル形式からコンテンツを解析および抽出するための効率的なツールを提供し、開発者がドキュメント テキスト抽出を .NET アプリケーションに組み込むことを可能にします。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
- C#および.NETプログラミングの基礎知識
- マシンに Visual Studio がインストールされている
- Groupdocs.Parser for .NET ライブラリへのアクセス
- テスト用のサンプルドキュメントファイル

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーを初期化する
まず、`Parser`サンプル ドキュメント ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにあなたのコード
}
```
## ステップ2: ドキュメント情報を取得する
ドキュメントに関する情報を取得するには`GetDocumentInfo()`方法。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ステップ3: ページを反復処理してテキストを抽出する
ドキュメントの各ページを反復処理し、テキスト コンテンツを抽出します。
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //ページからテキストを抽出する
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 結論
Groupdocs.Parser for .NET を使用して、ドキュメント ページからテキストを raw モードで抽出する方法を学びました。これは、さまざまなファイル形式のテキスト コンテンツを分析または処理する必要があるアプリケーションにとって強力な機能になります。

## よくある質問
### Groupdocs.Parser for .NET はすべてのファイル形式と互換性がありますか?
Groupdocs.Parser は、PDF、DOCX、XLSX、PPTX、EPUB など、幅広いファイル形式をサポートしています。
### このライブラリを使用してテキストとともにメタデータを抽出できますか?
はい、Groupdocs.Parser を使用すると、ドキュメントからテキストとメタデータの両方を抽出できます。
### テスト用に試用版はありますか?
はい、無料試用版は以下からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### Groupdocs.Parser のテクニカル サポートを受けるにはどうすればよいですか?
技術的なサポートについては、[Groupdocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).
### Groupdocs.Parser for .NET のライセンスはどこで購入できますか?
ライセンスを購入することができます[ここ](https://purchase.groupdocs.com/buy).