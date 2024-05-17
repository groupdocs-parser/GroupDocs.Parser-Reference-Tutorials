---
title: ドキュメントページからハイパーリンクを抽出する
linktitle: ドキュメントページからハイパーリンクを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからハイパーリンクを抽出する方法を学習します。C# でのハイパーリンク抽出のステップバイステップ ガイド。
type: docs
weight: 11
url: /ja/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからハイパーリンクを抽出する方法を段階的に説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式を解析し、テキスト、メタデータ、その他の要素を抽出できるようにする強力なライブラリです。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: 開発マシンに Visual Studio をインストールします。
-  GroupDocs.Parserライブラリ: GroupDocs.Parserライブラリをダウンロードして参照してください。次の場所から入手できます。[ここ](https://releases.groupdocs.com/parser/net/).
- サンプル ドキュメント: テスト用のハイパーリンクを含むサンプル ドキュメント (DOCX、PDF など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Parser 機能を使用するために必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーインスタンスを作成する
インスタンス化する`Parser`サンプル ドキュメントへのパスを持つクラス。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここにコードが入ります...
}
```
## ステップ2: ハイパーリンク抽出のサポートを確認する
続行する前に、ドキュメントがハイパーリンクの抽出をサポートしていることを確認してください。
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## ステップ3: ドキュメント情報を取得する
ドキュメントに関する基本情報を取得し、ページが含まれているかどうかを確認します。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ステップ4: ドキュメントページを反復処理する
ドキュメントの各ページを反復処理します。
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //現在のページからハイパーリンクを抽出します
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    //抽出されたハイパーリンクを反復処理する
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); //読みやすくするために空白行を入れる
    }
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからハイパーリンクを抽出する基本について説明しました。パーサーを初期化し、ハイパーリンクのサポートを確認し、ドキュメント情報を取得し、ドキュメント ページを反復処理してハイパーリンクを効率的に抽出する方法を学習しました。

## よくある質問
### 異なるドキュメント形式からハイパーリンクを抽出できますか?
はい、GroupDocs.Parser はハイパーリンク抽出のために DOCX、PDF、PPTX などのさまざまな形式をサポートしています。
### GroupDocs.Parser は既存の .NET アプリケーションに簡単に統合できますか?
はい、GroupDocs.Parser はわかりやすく設計されており、.NET プロジェクトに簡単に統合できます。
### GroupDocs.Parser を使用してハイパーリンクとともに他のメタデータを抽出できますか?
はい、ハイパーリンク以外にも、このライブラリを使用してドキュメントからテキスト、画像、メタデータを抽出できます。
### GroupDocs.Parser は暗号化されたドキュメントやパスワードで保護されたドキュメントを処理できますか?
GroupDocs.Parser は、パスワードが提供されている場合、パスワードで保護されたドキュメントを解析できます。
### 購入前にテストできる試用版はありますか?
はい、無料試用版をダウンロードできます[ここ](https://releases.groupdocs.com/).