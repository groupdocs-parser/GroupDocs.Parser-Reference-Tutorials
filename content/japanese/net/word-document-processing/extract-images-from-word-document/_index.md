---
title: Word文書から画像を抽出する
linktitle: Word文書から画像を抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して Word 文書から画像を抽出する方法を学びます。このチュートリアルでは、画像を .NET に統合するための手順を順を追って説明します。
weight: 11
url: /ja/net/word-document-processing/extract-images-from-word-document/
---

# Word文書から画像を抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Word 文書から画像を抽出する方法を学習します。GroupDocs.Parser は、Word (DOCX) を含むさまざまな文書形式からテキスト、メタデータ、画像などを解析して抽出できる強力な .NET ライブラリです。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- マシンに Visual Studio がインストールされています。
- C# プログラミングの基礎知識。
- GroupDocs.Parser for .NETライブラリがインストールされています。ダウンロードはこちらから[ここ](https://releases.groupdocs.com/parser/net/).
## 名前空間のインポート
まず、GroupDocs.Parser 機能を使用するには、C# プロジェクトに必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
ここで、Word 文書から画像を抽出するプロセスを簡単な手順に分解してみましょう。
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`クラスは、Word 文書へのパスを入力として提供します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //画像抽出用のコードはここに記載します
}
```
## ステップ2: Word文書から画像を抽出する
次に、`GetImages()`方法の`Parser`ドキュメントから画像を抽出するオブジェクト。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ステップ3: 画像保存オプションを定義する
抽出した画像を保存するためのオプションを指定します。たとえば、画像形式 (PNG など) を選択したり、その他の設定を構成したりできます。
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ステップ4: 抽出した画像を反復処理して保存する
抽出された各画像を反復処理し、指定されたオプションを使用してファイルに保存します。
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    //画像をPNGファイルに保存する
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Word 文書から画像を抽出する方法を学習しました。これらの手順に従うことで、文書解析機能と画像抽出機能を .NET アプリケーションに簡単に統合できます。

## よくある質問
### GroupDocs.Parser は Word 以外のドキュメント形式から画像を抽出できますか?
はい、GroupDocs.Parser は PDF、PowerPoint、Excel など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
テスト目的の一時ライセンスは以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser for .NET に関する詳細なドキュメントはどこで入手できますか?
完全なドキュメントを参照できます[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser の無料トライアルはありますか?
はい、無料トライアルでGroupDocs.Parserの機能を試すことができます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser に関するサポートを受けたり質問したりするにはどうすればよいですか?
ご質問は[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).