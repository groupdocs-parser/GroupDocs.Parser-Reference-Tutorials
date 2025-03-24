---
title: プレーンテキストの抽出
linktitle: プレーンテキストの抽出
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからプレーン テキストを抽出する方法を学びます。テキスト抽出をアプリケーションに統合するための簡単な手順です。
weight: 14
url: /ja/net/formatted-text-extraction/extract-plain-text/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してさまざまなドキュメント形式からプレーン テキストを抽出する方法について説明します。GroupDocs.Parser は、開発者がドキュメントをシームレスに操作し、テキストとメタデータを効率的に抽出できるようにする強力なライブラリです。このガイドでは、このライブラリを .NET アプリケーションに統合して利用するために必要な手順について説明します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. Visual Studio: 開発マシンに Visual Studio をインストールします。
2.  GroupDocs.Parserライブラリ: GroupDocs.Parser for .NETを以下のサイトからダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/parser/net/).
3. サンプル ドキュメント: テキスト抽出用のサンプル ドキュメント (DOCX、PDF、TXT など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Parser の機能にアクセスするために必要な名前空間を C# プロジェクトに含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーを初期化する
インスタンスを作成する`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    //テキスト抽出のコードはここに記述します
}
```
## ステップ2: フォーマットされたテキストを抽出する
以内`using`ブロックの`Parser`、フォーマットされたテキストを抽出します。`GetFormattedText`方法`PlainText`モード。
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    //抽出したテキストを読み取って処理するコード
}
```
## ステップ3: 抽出したテキストを読む
使用`TextReader`抽出されたプレーンテキストを読み取って出力するインスタンス。
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからプレーン テキストを抽出する基本について説明しました。これらの手順に従うことで、テキスト抽出機能を .NET アプリケーションにシームレスに統合できます。

## よくある質問
### GroupDocs.Parser は複数のドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、DOCX、PDF、TXT など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser を使用してテキストとともにメタデータを抽出できますか?
はい、GroupDocs.Parser では、テキスト コンテンツと、作成者、作成日などのメタデータの両方を抽出できます。
### GroupDocs.Parser の無料トライアルはありますか?
はい、GroupDocs.Parserの無料トライアルにアクセスできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のテクニカル サポートはどこで受けられますか?
技術的なサポートについては、GroupDocs.Parser をご覧ください。[フォーラム](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを取得するには、GroupDocs.Parserにアクセスしてください。[一時ライセンスページ](https://purchase.groupdocs.com/temporary-license/).