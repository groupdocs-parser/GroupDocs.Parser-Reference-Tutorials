---
title: Word文書内のテキストをキーワードで検索
linktitle: Word文書内のテキストをキーワードで検索
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して Word 文書内のテキストを検索する方法を学習します。特定のキーワードを効率的に抽出します。
type: docs
weight: 18
url: /ja/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、C# で Word 文書内の特定のテキストを検索する方法について説明します。GroupDocs.Parser は、開発者が Word 文書を含むさまざまな文書形式からテキストとメタデータを抽出できるようにする強力なライブラリです。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. 開発環境: Visual Studio または互換性のある他の IDE をインストールします。
2.  GroupDocs.Parserライブラリ: GroupDocs.Parser for .NETライブラリを以下のサイトからダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/parser/net/).
3. サンプル Word 文書: テキスト検索に使用するサンプル Word 文書を準備します。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル Word 文書へのパスを渡すことでクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここにコードが入ります
}
```
## ステップ2: キーワードを検索する
次に、`Search`方法の`Parser`ドキュメント内の特定のキーワードを検索するクラス。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
交換する`"keyword"`ドキュメント内で検索するテキストを入力します。
## ステップ3: 検索結果を反復処理する
検索結果を反復処理するには、`foreach`それぞれにアクセスするためのループ`SearchResult`物体。
```csharp
foreach (SearchResult result in searchResults)
{
    //各検索結果を処理するコード
}
```
## ステップ4: 検索結果の詳細にアクセスする
ループ内では、各検索結果の位置とテキストにアクセスできます。`Position`そして`Text`の特性`SearchResult`物体。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
このコードスニペットはインデックス（`Position`) と見つかったテキスト (`Text`) をコンソールに表示します。

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Word 文書内の特定のテキストを検索する方法を学習しました。このライブラリは、さまざまなドキュメント形式からコンテンツをプログラムで抽出および操作するための便利な方法を提供します。

## よくある質問
### GroupDocs.Parser は Word 以外のドキュメント形式も処理できますか?
はい、GroupDocs.Parser は PDF、Excel、PowerPoint など、幅広い形式をサポートしています。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを申請するには、[GroupDocs 購入ページ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser に関する追加サポートや質問はどこで受けられますか?
訪問[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)コミュニティのサポートとディスカッションのため。
### 購入前に GroupDocs.Parser を無料で試すことはできますか?
はい、無料試用版をこちらからダウンロードできます。[GroupDocs リリースページ](https://releases.groupdocs.com/).