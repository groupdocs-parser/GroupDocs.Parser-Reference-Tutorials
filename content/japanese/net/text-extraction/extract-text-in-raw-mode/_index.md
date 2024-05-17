---
title: 生モードでテキストを抽出
linktitle: 生モードでテキストを抽出
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出する方法を学習します。.NET アプリケーション内で簡単かつ効率的でシームレスなテキスト抽出を実現します。
type: docs
weight: 19
url: /ja/net/text-extraction/extract-text-in-raw-mode/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、さまざまなドキュメント形式から効率的にテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者が PDF、Word、Excel、PowerPoint などのドキュメントからテキストとメタデータを抽出し、.NET アプリケーション内でのテキスト抽出タスクを簡素化できるようにする強力なライブラリです。
## 前提条件
このチュートリアルに進む前に、次の前提条件が設定されていることを確認してください。
- マシンにインストールされている Visual Studio またはその他の .NET 開発環境。
- C# プログラミング言語に関する基本的な知識。
- GroupDocs.Parser for .NET ライブラリへのアクセス。

## 名前空間のインポート
まず、C# プロジェクトに GroupDocs.Parser に必要な名前空間をインポートしてください。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ステップ 1: GroupDocs.Parser を初期化する
テキスト抽出を開始するには、`Parser`クラスにサンプル ドキュメントへのパスを渡します。
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    //ここでテキスト抽出を続行します
}
```
## ステップ2: 生のテキストを抽出する
以内`using`ブロックするには、`GetText`方法`TextOptions`ドキュメントから生のテキストを抽出するには:
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    //文書のテキストを読み続ける
}
```
## ステップ3: ドキュメントからテキストを読み取る
さて、`TextReader`ドキュメントから抽出されたテキストを読み取るオブジェクト:
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 結論
これらの手順に従うことで、GroupDocs.Parser for .NET を使用してドキュメントから生のテキストを効果的に抽出できます。このチュートリアルでは、.NET アプリケーション内でこのライブラリを活用してシームレスなテキスト抽出を行うための基本的なガイドを提供します。

## よくある質問
### GroupDocs.Parser はどのようなファイル形式をサポートしていますか?
GroupDocs.Parser は、PDF、Microsoft Word、Excel、PowerPoint など、幅広いファイル形式をサポートしています。
### GroupDocs.Parser を使用してテキストとともにメタデータを抽出できますか?
はい、GroupDocs.Parser では、サポートされているドキュメント形式からテキストとメタデータの両方を抽出できます。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser は従来の .NET Framework に加えて .NET Core とも互換性があります。
### GroupDocs.Parser はパスワードで保護されたドキュメントを処理できますか?
はい、正しいパスワードが提供されていれば、GroupDocs.Parser はパスワードで保護されたドキュメントを処理できます。
### GroupDocs.Parser を Web アプリケーションに統合できますか?
確かに、GroupDocs.Parser は、.NET テクノロジを使用して開発された Web アプリケーションにシームレスに統合できます。