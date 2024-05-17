---
title: 正規表現によるテキスト検索 (Regex)
linktitle: 正規表現によるテキスト検索 (Regex)
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、ドキュメント内の正規表現を使用してテキストを検索する方法を学習します。特定のコンテンツを簡単に抽出します。
type: docs
weight: 23
url: /ja/net/text-extraction/search-text-by-regex/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、ドキュメント内のテキストを正規表現 (Regex) で検索する方法について詳しく説明します。GroupDocs.Parser は、開発者が PDF、DOCX、XLSX などのさまざまなファイル形式からテキストとメタデータを抽出できるようにする強力なライブラリです。正規表現を使用したテキストの検索は、ドキュメント内のパターンや特定のコンテンツを効率的に見つけるのに特に便利です。
## 前提条件
このチュートリアルに進む前に、次のものを用意してください。
1. Visual Studio: .NET 開発用の Visual Studio IDE をインストールします。
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル ファイル: 検索機能をテストするためのサンプル ドキュメント (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、C# コードに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
インスタンス化する`Parser`サンプル ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにコードが入ります
}
```
交換する`"YourSampleFile.pdf"`実際のファイルへのパスを入力します。
## ステップ2: 正規表現を使用して検索する
正規表現パターンを使用して検索を定義し、実行します。たとえば、ドキュメント内の数値シーケンス (整数など) を検索するには、次のようにします。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
この例では、`[0-9]+` 1 つ以上の数字に一致する正規表現パターンです。
## ステップ3: 検索サポートを確認する
ドキュメント タイプに対して検索操作がサポートされているかどうかを確認します。
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## ステップ4: 検索結果を反復処理する
検索結果を反復処理し、各一致を処理します。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
このループは、ドキュメント内で見つかった位置と一致するテキストを出力します。

## 結論
結論として、GroupDocs.Parser for .NET を活用すると、さまざまなドキュメント形式で正規表現を使用して効率的にテキストを検索できるようになります。このガイドに従うことで、開発者はドキュメント解析と正規表現ベースのテキスト抽出を .NET アプリケーションにシームレスに統合できます。

## よくある質問
### GroupDocs.Parser は暗号化されたドキュメント内を検索できますか?
いいえ、GroupDocs.Parser は暗号化されたドキュメントやパスワードで保護されたドキュメント内を検索することはできません。
### GroupDocs.Parser は OCR (光学式文字認識) をサポートしていますか?
いいえ、GroupDocs.Parser は OCR を実行しません。ドキュメントの内部構造からのテキスト抽出に依存します。
### 正規表現を使用して複雑なパターンを検索できますか?
はい、GroupDocs.Parser は本格的な正規表現をサポートしており、ドキュメント内での複雑なパターン マッチングが可能になります。
### テキスト抽出ではどのドキュメント形式がサポートされていますか?
GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広い形式をサポートしています。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser はクロスプラットフォーム開発用の .NET Core と互換性があります。