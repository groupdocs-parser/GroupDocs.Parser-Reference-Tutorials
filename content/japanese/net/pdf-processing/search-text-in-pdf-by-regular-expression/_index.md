---
title: 正規表現でPDF内のテキストを検索する
linktitle: 正規表現でPDF内のテキストを検索する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser で正規表現を使用して PDF ドキュメント内の特定のテキストを検索します。PDF テキストを簡単に抽出、分析、操作します。
type: docs
weight: 19
url: /ja/net/pdf-processing/search-text-in-pdf-by-regular-expression/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して PDF ドキュメントからテキストを効率的に抽出する方法を説明します。GroupDocs.Parser は、開発者が PDF を含むさまざまなドキュメント形式からテキスト、メタデータ、構造化データを解析および抽出できるようにする強力なライブラリです。.NET アプリケーション内でデータ抽出、コンテンツ分析、または検索機能に取り組んでいる場合でも、GroupDocs.Parser はこれらのタスクをシームレスに処理するための包括的なツール セットを提供します。
## 前提条件
このチュートリアルに進む前に、次の前提条件が設定されていることを確認してください。
1. 開発環境: Visual Studio または任意の .NET 開発環境をインストールします。
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETライブラリをダウンロードしてインストールします。ライブラリとそのドキュメントは、[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル PDF ファイル: テキスト検索操作を実行するために使用するサンプル PDF ファイルを準備します。

## 名前空間のインポート
まず、GroupDocs.Parser 機能にアクセスするために、.NET プロジェクトに必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル PDF ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("Path_to_Your_PDF_File.pdf"))
{
    //テキスト検索のコードはここに記入します
}
```
交換する`"Path_to_Your_PDF_File.pdf"`PDF ファイルへの実際のパスを入力します。
## ステップ2: 正規表現を使用してテキストを検索する
内部`using`ブロックの`Parser`たとえば、正規表現を使用してテキスト検索操作を実行します。この例では、大文字と小文字の一致を有効にして単語「the」を検索する方法を示します。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- `\\sthe\\s`: この正規表現は、周囲のスペース（単語境界）を含む正確な単語「the」を検索します。
- `new SearchOptions(true, false, true)`: これらのオプションは、大文字と小文字を区別して検索を実行するように設定します（`true`）、 単語全体 （`false`）、正規表現（`true`) マッチング。

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して正規表現で PDF ドキュメント内のテキストを検索する方法について説明しました。このライブラリは複雑なドキュメント解析タスクを簡素化し、.NET アプリケーション内でテキスト データを抽出および操作しやすくします。

## よくある質問
### GroupDocs.Parser は PDF 以外のドキュメント形式も処理できますか?
はい、GroupDocs.Parser は DOCX、XLSX、PPTX などのさまざまなドキュメント形式をサポートしています。
### GroupDocs.Parser に関するその他のリソースやサポートはどこで見つかりますか?
訪問することができます[GroupDocs.Parser ドキュメント](https://reference.groupdocs.com/parser/net/)そして、[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser の無料トライアルはありますか?
はい、アクセスできます[無料試用版](https://releases.groupdocs.com/) GroupDocs.Parser の機能を調べてみましょう。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
あなたは取得することができます[一時ライセンス](https://purchase.groupdocs.com/temporary-license/)購入前にテストするため。
### GroupDocs.Parser のライセンス版はどこで購入できますか?
 GroupDocs.Parserのライセンス版は以下から購入できます。[ここ](https://purchase.groupdocs.com/buy).