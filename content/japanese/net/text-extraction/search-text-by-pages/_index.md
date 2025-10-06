---
title: ページによるテキスト検索
linktitle: ページによるテキスト検索
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してページごとにテキストを検索する方法を学習します。.NET アプリケーションのドキュメントから特定のコンテンツを効率的に抽出します。
weight: 22
url: /ja/net/text-extraction/search-text-by-pages/
type: docs
---
# ページによるテキスト検索

## 導入
.NET 開発の世界では、ドキュメントからテキストを効率的に解析して抽出することが重要なタスクです。GroupDocs.Parser for .NET は、さまざまなドキュメント形式を扱うための強力な機能を提供し、開発者が特定のコンテンツをシームレスに検索して抽出できるようにします。このチュートリアルでは、GroupDocs.Parser を利用して .NET アプリケーションでページごとにテキストを検索するプロセスについて説明します。
## 前提条件
このチュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
- C# および .NET フレームワークの基本的な理解
- システムにVisual Studioがインストールされている
- GroupDocs.Parser for .NETライブラリがインストールされている（ダウンロード先：[ここ](https://releases.groupdocs.com/parser/net/）)
- 検索機能をテストするためのサンプルファイル
## 名前空間のインポート
まず、GroupDocs.Parser 機能にアクセスするために必要な名前空間をプロジェクトに含めます。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まずインスタンス化して`Parser`サンプル ファイルへのパスを含むクラス:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここにコードを入力してください
}
```
## ステップ2: ページ番号でテキストを検索する
活用する`Search`文書内の特定のキーワードとページ番号を検索する方法:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## ステップ3: 検索サポートを確認する
ドキュメント タイプに対して検索操作がサポートされているかどうかを確認します。
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## ステップ4: 検索結果を反復処理する
検索結果を反復処理して、インデックス位置、ページ番号、見つかったテキストを取得します。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してページによるテキスト検索を実装する方法について説明しました。これらの手順に従うことで、ドキュメントの解析および検索機能を .NET アプリケーションに効率的に統合できます。

## よくある質問
### GroupDocs.Parser はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、DOCX、PDF、XLSX、PPTX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser を使用してドキュメントから画像とメタデータを抽出できますか?
はい、GroupDocs.Parser を使用すると、ドキュメントから画像、メタデータ、テキストを抽出できます。
### GroupDocs.Parser の詳細なドキュメントはどこで見つかりますか?
ドキュメントにアクセスできます[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを申請できます[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser に関するサポートや支援はどこで受けられますか?
サポートとディスカッションについては、GroupDocs.Parser フォーラムをご覧ください。[ここ](https://forum.groupdocs.com/c/parser/17).