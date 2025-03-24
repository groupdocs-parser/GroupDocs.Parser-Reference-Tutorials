---
title: Excel シートから Raw モードでテキストを抽出する
linktitle: Excel シートから Raw モードでテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: この包括的なチュートリアルでは、GroupDocs.Parser for .NET を使用して Excel シートからテキストを抽出する方法を学びます。ダウンロードして解析を開始します。
weight: 15
url: /ja/net/excel-document-processing/extract-text-from-excel-sheet-in-raw-mode/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を Raw モードで使用して Excel シートからテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者が Excel ファイルを含むさまざまなドキュメント形式を使用してテキストを抽出および分析できるようにする強力な API です。前提条件を確認し、名前空間をインポートし、各手順を分解して、Excel シートからテキストを抽出するプロセスを説明します。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- Visual Studio: マシンに Visual Studio IDE をインストールします。
-  GroupDocs.Parser for .NET: GroupDocs.Parserをダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/parser/net/).
- サンプル Excel ファイル: テキスト抽出に使用するサンプル Excel ファイルを準備します。

## 名前空間のインポート
GroupDocs.Parser の機能にアクセスするには、まず必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル Excel ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //テキスト抽出のコードはここに記入します
}
```
## ステップ2: ドキュメント情報を取得する
ドキュメント情報を取得するには、`GetDocumentInfo()`方法：
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ステップ3: シートを反復処理する
Excel ファイル内の各シートをループします。
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.RawPageCount));
    
    //各シートからテキストを抽出するためのコードをここに記述します
}
```
## ステップ4: 各シートからテキストを抽出する
各シートからテキストを抽出する`TextReader`:
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Excel シートからテキストを抽出する方法について説明しました。上記の手順に従うことで、Excel ファイルからテキスト データを効率的に取得し、.NET アプリケーションでさらに処理または分析することができます。

## よくある質問
### GroupDocs.Parser は他のドキュメント形式からテキストを抽出できますか?
はい、GroupDocs.Parser は、Word、PDF、PowerPoint など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser は大きな Excel ファイルの処理に適していますか?
はい、GroupDocs.Parser は大きなドキュメントを効率的に処理するように設計されています。
### GroupDocs.Parser に関する詳細なドキュメントはどこで見つかりますか?
参照するには[ドキュメンテーション](https://tutorials.groupdocs.com/parser/net/)詳細な情報と例については、こちらをご覧ください。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
訪問[このリンク](https://purchase.groupdocs.com/temporary-license/)一時ライセンスを申請します。
### GroupDocs.Parser はカスタマー サポートを提供していますか?
はい、サポートを求めたり質問したりすることができます。[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17).