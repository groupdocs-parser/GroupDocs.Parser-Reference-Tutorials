---
title: キーワードでテキストを検索
linktitle: キーワードでテキストを検索
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、ドキュメント内のテキストをキーワードで検索する方法を学びます。関連するコンテンツを効率的に簡単に抽出します。
weight: 21
url: /ja/net/text-extraction/search-text-by-keyword/
type: docs
---
# キーワードでテキストを検索

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、ドキュメント内のキーワードでテキストを検索する方法について詳しく説明します。GroupDocs.Parser は、開発者が PDF、Microsoft Office ドキュメントなどのさまざまなファイル形式からテキスト、メタデータ、およびその他の情報を抽出できるようにする強力なライブラリです。これらのドキュメント内で特定のキーワードを検索することは、大量のテキスト データを処理するアプリケーションにとって不可欠な場合があります。
## 前提条件
始める前に、次の設定がされていることを確認してください。
1. 開発環境: Visual Studio または任意の推奨 .NET IDE。
2.  GroupDocs.Parser for .NET: ライブラリをダウンロードするには、[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル ファイルへのアクセス: キーワード検索機能をテストするためのサンプル ファイル (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、プロジェクトに必要な名前空間を含める必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`クラスを指定し、サンプル ファイルへのパスを指定します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //キーワードを検索
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    //検索結果を反復処理する
    foreach (SearchResult result in searchResults)
    {
        //索引と見つかったテキストを印刷する
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## ステップ2: キーワードを検索する
以内`using`ブロック、呼び出し`Search`方法`parser`オブジェクトに、必要なキーワードを引数として渡します。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
交換する`"test"`文書内で検索したいキーワードを入力します。
## ステップ3: 検索結果を反復処理する
次に、`Search`方法を使用する`foreach`ループ。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
それぞれ`SearchResult`物体`result`、その`Position`（インデックス）と`Text`(見つかったテキスト)

## 結論
このチュートリアルでは、GroupDocs.Parser for .NETを使用して、ドキュメント内のキーワードでテキストを簡単に検索する方法を説明しました。`Search`方法の`Parser`クラスを使用すると、特定の検索用語に基づいて関連するテキスト スニペットを効率的に取得できます。

## よくある質問
### GroupDocs.Parser はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いファイル形式をサポートしています。
### GroupDocs.Parser を使用して高度なテキスト抽出操作を実行できますか?
もちろんです! テキスト検索以外にも、GroupDocs.Parser ではメタデータ抽出、構造化テキスト抽出などが可能になります。
### GroupDocs.Parser の詳細なドキュメントはどこで見つかりますか?
完全なドキュメントを見る[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 関連のクエリについてサポートや支援を受けるにはどうすればよいですか?
サポートとディスカッションについては、GroupDocs フォーラムをご覧ください。[ここ](https://forum.groupdocs.com/c/parser/17).
### 購入前に GroupDocs.Parser を評価できる試用版はありますか?
はい、無料トライアルにアクセスできます[ここ](https://releases.groupdocs.com/).