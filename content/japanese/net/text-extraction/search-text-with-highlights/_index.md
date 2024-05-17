---
title: ハイライト付きテキスト検索
linktitle: ハイライト付きテキスト検索
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメント内のテキストを検索および強調表示する方法を学びます。貴重な洞察を効率的に抽出します。
type: docs
weight: 24
url: /ja/net/text-extraction/search-text-with-highlights/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント内のテキストを検索し、検索結果を強調表示する方法について説明します。GroupDocs.Parser は、さまざまなドキュメント形式を操作し、テキストやメタデータなどを抽出できる強力なライブラリです。
## 前提条件
始める前に、以下のものを用意してください。
1.  GroupDocs.Parser for .NET: ライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
2. IDE: .NET 開発には Visual Studio または任意の推奨 IDE を使用します。
3. サンプル ファイル: テキスト検索用のサンプル ドキュメント (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、.NET プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーインスタンスを作成する
まずインスタンス化して`Parser`サンプル ファイルへのパスを含むクラス:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにあなたのコード
}
```
## ステップ2: ハイライトオプションを定義する
指定する`HighlightOptions`検索結果の強調表示方法を設定します。たとえば、15 文字のコンテキスト ウィンドウを設定するには、次のようにします。
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## ステップ3: テキストを検索する
次に、ドキュメント内でテキスト検索を実行します。検索するキーワードを入力します (例: "lorem")。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## ステップ4: 検索結果を処理する
検索結果を反復処理し、見つかったテキストをハイライトとともに表示します。
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント内のテキストを検索し、検索結果を強調表示する方法を学びました。この機能は、.NET アプリケーションでのテキストの抽出と分析に非常に役立ちます。

## よくある質問
### GroupDocs.Parser はさまざまなドキュメント形式の処理に適していますか?
はい、GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser を使用してドキュメントからメタデータを抽出できますか?
もちろんです! GroupDocs.Parser を使用すると、ドキュメントからメタデータ、テキスト、構造化データを抽出できます。
### GroupDocs.Parser に関するサポートや質問はどこで受けられますか?
訪問することができます[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)サポート関連のお問い合わせについては、
### GroupDocs.Parser の無料トライアルはありますか?
はい、アクセスできます[無料トライアル](https://releases.groupdocs.com/) GroupDocs.Parser の機能を評価します。
### GroupDocs.Parser のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます[ここ](https://purchase.groupdocs.com/buy)臨時免許も取得する[ここ](https://purchase.groupdocs.com/temporary-license/).