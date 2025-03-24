---
title: ドキュメントからハイパーリンクを抽出する
linktitle: ドキュメントからハイパーリンクを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからハイパーリンクを抽出する方法を学びます。このわかりやすいガイドを使用して、C# アプリケーションを強化します。
weight: 10
url: /ja/net/hyperlink-extraction/extract-hyperlinks-from-document/
---

# ドキュメントからハイパーリンクを抽出する

## 導入
このチュートリアルでは、開発者がドキュメントからハイパーリンクを簡単に抽出できるようにする多目的ライブラリである GroupDocs.Parser for .NET の強力な機能について詳しく説明します。ハイパーリンクの抽出は、特に PDF や Word ドキュメントなどのテキストベースのファイルを処理する場合に、ドキュメント処理でよく必要になります。GroupDocs.Parser を使用すると、さまざまなドキュメント形式からハイパーリンクとそれに関連付けられた URL を効率的に識別して抽出できます。
## 前提条件
このチュートリアルを進める前に、次の前提条件を満たしていることを確認してください。
- C#プログラミングの基礎知識
- システムにVisual Studioがインストールされている
- GroupDocs.Parser for .NETライブラリはダウンロード可能です[ここ](https://releases.groupdocs.com/parser/net/)
## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

ここで、各例を複数のステップに分解して、GroupDocs.Parser for .NET を使用したハイパーリンク抽出のプロセスを説明します。
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ハイパーリンク抽出のコードはここに記入します
}
```
交換する`"YourSampleFile.docx"`対象ドキュメントへのパスを入力します。
## ステップ2: ハイパーリンク抽出のサポートを確認する
ハイパーリンクを抽出する前に、ドキュメント形式がハイパーリンクの抽出をサポートしているかどうかを確認することが重要です。
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
このステップにより、指定されたドキュメントに対してハイパーリンクの抽出が実行可能であることが保証されます。
## ステップ3: ハイパーリンクを抽出する
ドキュメントからハイパーリンクを抽出します。`GetHyperlinks()`方法：
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
この行は、`PageHyperlinkArea`ハイパーリンク情報を含むオブジェクト。
## ステップ4: 抽出されたハイパーリンクを反復処理する
抽出されたハイパーリンクのコレクションを反復処理し、そのテキストと URL を取得します。
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    //ハイパーリンクテキストを印刷する
    Console.WriteLine(hyperlink.Text);
    
    //ハイパーリンクURLを印刷する
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); //読みやすくするために空白行を追加します
}
```
繰り返し処理することで`hyperlinks`コレクションでは、各ハイパーリンクのテキストと URL にアクセスして印刷できます。
## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからハイパーリンクを抽出する方法について説明しました。このライブラリが提供する機能を活用することで、開発者はハイパーリンク抽出機能を C# アプリケーションに簡単に統合できます。

## よくある質問
### GroupDocs.Parser はさまざまなドキュメント形式からのハイパーリンク抽出を処理できますか?
はい、GroupDocs.Parser は、PDF、Word、Excel、PowerPoint など、さまざまなファイル形式からのハイパーリンク抽出をサポートしています。
### GroupDocs.Parser の無料トライアルはありますか?
はい、GroupDocs.Parserの無料トライアルをご利用いただけます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のドキュメントはどこにありますか?
 GroupDocs.Parserの詳細なドキュメントは以下にあります。[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
 GroupDocs.Parserの一時ライセンスを取得できます[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs はトラブルシューティングのサポートを提供していますか?
はい、GroupDocsでサポートやトラブルシューティングの支援を受けることができます。[フォーラム](https://forum.groupdocs.com/c/parser/17).