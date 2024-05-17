---
title: 画像をファイルに抽出する
linktitle: 画像をファイルに抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、PDF や DOCX などのさまざまなドキュメント タイプから画像を簡単に抽出します。ドキュメント解析タスクを簡素化します。
type: docs
weight: 13
url: /ja/net/image-extraction/extract-images-to-files/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、PDF、Word、Excel、PowerPoint などのさまざまなドキュメント形式から画像を抽出する方法を学習します。GroupDocs.Parser は、開発者がドキュメントからテキスト、メタデータ、画像などを簡単に解析して抽出できるようにする強力なライブラリです。このガイドでは、C# を使用して画像を抽出し、個別のファイルとして保存するプロセスについて説明します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. Visual Studio: システムに Visual Studio がインストールされていることを確認してください。
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル ドキュメント: 画像を抽出するサンプル ドキュメント (PDF、DOCX、XLSX など) を準備します。

## 名前空間のインポート
まず、C# コードに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーインスタンスを作成する
インスタンス化する`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにコードが入ります
}
```
## ステップ2: ドキュメントから画像を抽出する
使用`GetImages()`方法の`Parser`ドキュメントから画像を取得するためのオブジェクト。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ステップ3: 画像抽出のサポートを確認する
ドキュメントが画像抽出をサポートしているかどうかを確認します。
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## ステップ4: 画像保存オプションを設定する
フォーマットを指定します（`ImageFormat`抽出した画像を保存するファイル形式（例：PNG）を選択します。
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ステップ5: 画像を反復して保存する
抽出された画像をループし、各画像をファイルに保存します。
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
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、C# でドキュメントから画像を抽出する方法を学習しました。この強力なライブラリは、さまざまなファイル形式からデータを解析および抽出するプロセスを簡素化するため、.NET アプリケーションでのドキュメント処理タスクに不可欠なツールとなります。

## よくある質問
### パスワードで保護された文書から画像を抽出できますか?
はい、GroupDocs.Parser は、解析中に正しいパスワードを入力すると、パスワードで保護されたドキュメントから画像を抽出できます。
### 画像抽出ではどのドキュメント形式がサポートされていますか?
GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX、EPUB など、幅広い形式をサポートしています。
### 画像抽出中に例外を処理するにはどうすればよいですか?
コードにエラー処理を実装して、画像の抽出中に発生する可能性のある例外をキャッチして管理できます。
### GroupDocs.Parser はドキュメントのバッチ処理に適していますか?
はい、GroupDocs.Parser を使用すると、複数のドキュメントを一括処理し、画像やその他のデータを効率的に抽出できます。
### GroupDocs.Parser はスキャンされたドキュメントの OCR 機能を提供しますか?
GroupDocs.Parser は現在 OCR (光学式文字認識) をサポートしていませんが、ドキュメントからの構造化データの解析に優れています。