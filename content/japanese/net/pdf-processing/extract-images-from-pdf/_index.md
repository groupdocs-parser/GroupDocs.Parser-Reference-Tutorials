---
title: PDFから画像を抽出する
linktitle: PDFから画像を抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して PDF ドキュメントから画像を抽出する方法を学習します。コード例付きのステップバイステップ ガイドです。
weight: 12
url: /ja/net/pdf-processing/extract-images-from-pdf/
type: docs
---
# PDFから画像を抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して PDF ドキュメントから画像を抽出する方法について説明します。GroupDocs.Parser は、開発者が .NET 環境で PDF、DOCX、PPTX などのさまざまなドキュメント形式を操作できるようにする強力なライブラリです。これらの手順に従うと、PDF ファイルから簡単に画像を抽出できるようになります。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
- システムにVisual Studioがインストールされている
- C#プログラミングの基礎知識
-  GroupDocs.Parser for .NET ライブラリ (ダウンロード[ここ](https://releases.groupdocs.com/parser/net/）)

## 名前空間のインポート
まず、C# コード ファイルに必要な名前空間を含めます。
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
//Parserクラスのインスタンスを作成する
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //画像を抽出するコードはここに記述します
}
```
## ステップ2: PDFから画像を抽出する
以内`using`ブロック、活用する`GetImages`方法の`Parser`PDF ドキュメントから画像のコレクションを取得するためのインスタンス。
```csharp
// PDFから画像を抽出する
IEnumerable<PageImageArea> images = parser.GetImages();
```
## ステップ3: 画像保存オプションを設定する
抽出した画像を保存する方法を指定するためのオプションを定義します。ここでは、画像を PNG 形式で保存します。
```csharp
// PNG形式で画像を保存するオプションを作成する
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## ステップ4: 抽出した画像を反復処理して保存する
各画像を反復処理して`images`コレクションを抽出し、順番に PNG ファイルに保存します。
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
このチュートリアルでは、GroupDocs.Parser for .NET を使用して PDF ドキュメントから画像を抽出する方法を説明しました。これらの手順に従うことで、画像抽出機能を .NET アプリケーションにシームレスに統合できます。

## よくある質問
### GroupDocs.Parser は他のドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いドキュメント形式をサポートしています。
### 画像抽出オプションを変更できますか?
もちろんです! GroupDocs.Parser には、画像形式や品質設定など、画像抽出をカスタマイズするためのさまざまなオプションが用意されています。
### GroupDocs.Parser を商用利用する場合、ライセンスは必要ですか?
はい、GroupDocs.Parser を本番環境で使用するには商用ライセンスが必要です。詳細はこちら[ここ](https://purchase.groupdocs.com/buy).
### 追加のサポートや支援はどこで受けられますか?
 GroupDocs.Parser にアクセスしてください[フォーラム](https://forum.groupdocs.com/c/parser/17)コミュニティのサポートとガイダンスのため。
### GroupDocs.Parser の無料トライアルはありますか?
はい、無料トライアルは以下から入手できます。[ここ](https://releases.groupdocs.com/) GroupDocs.Parser の機能を調べます。