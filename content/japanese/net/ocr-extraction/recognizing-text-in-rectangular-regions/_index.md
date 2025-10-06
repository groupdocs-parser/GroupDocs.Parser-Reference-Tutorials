---
title: 長方形領域内のテキストの認識
linktitle: 長方形領域内のテキストの認識
second_title: GroupDocs.Parser .NET API
description: OCR 機能を備えた GroupDocs.Parser for .NET を使用して、ドキュメントの特定の領域内のテキストを認識する方法を学習します。
weight: 14
url: /ja/net/ocr-extraction/recognizing-text-in-rectangular-regions/
type: docs
---
# 長方形領域内のテキストの認識

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、ドキュメントの特定の長方形領域内のテキストを認識する方法について説明します。GroupDocs.Parser は、開発者が PDF、Word、Excel、PowerPoint などのさまざまなファイル形式からテキスト、メタデータなどを抽出できるようにする強力なライブラリです。
## 前提条件
始める前に、次の設定がされていることを確認してください。
-  GroupDocs.Parser for .NET: ライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
- 開発環境: Visual Studio またはその他の .NET IDE。
- サンプル ドキュメント: 認識するテキストを含むサンプル ファイル (PDF、DOCX など) を用意します。

## 名前空間のインポート
まず、必要な名前空間を C# コードにインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサー設定を初期化する
まず設定から始めましょう`ParserSettings`OCR コネクタを使用します。ここでは、Aspose OCR オンプレミス コネクタを使用します。
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ステップ2: パーサーインスタンスを作成する
次に、`Parser`以前に定義した設定を持つクラス:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    //コードはここに続きます
}
```
交換する`"YourSampleFile.pdf"`ドキュメントへのパスを入力します。
## ステップ3: OCR矩形を定義する
文書内でテキスト認識を実行する四角形を定義します。たとえば、`(0, 0)`幅のある`400`高さ`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## ステップ4: テキスト認識オプションを構成する
作成する`TextOptions`定義された四角形とともに OCR の使用を指定します。
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## ステップ5: OCRを使用してテキストを抽出する
使用`GetText`方法の`Parser`設定されたインスタンス`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    //抽出されたテキストを読み取るか、「サポートされていない」ケースを処理する
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を利用して、OCR を使用してドキュメント内の特定の長方形領域からテキストを抽出する方法を説明しました。このプロセスはさらにカスタマイズでき、さまざまなアプリケーションに統合して、テキスト抽出タスクを自動化できます。

## よくある質問
### GroupDocs.Parser はスキャンされたドキュメントからテキストを抽出できますか?
はい、GroupDocs.Parser はスキャンされたドキュメントからテキストを抽出するための OCR (光学式文字認識) をサポートしています。
### GroupDocs.Parser はどのようなファイル形式をサポートしていますか?
GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いファイル形式をサポートしています。
### テキスト抽出がサポートされていないドキュメントをどのように処理すればよいですか?
テキスト抽出がサポートされているかどうかは、以下を使用して確認できます。`TextReader`返されるインスタンス`parser.GetText(options)`.
### GroupDocs.Parser は大規模なテキスト抽出タスクに適していますか?
はい、GroupDocs.Parser は大規模なテキスト抽出タスクを効率的に処理するように設計されています。
### GroupDocs.Parser 関連の問題に関するサポートはどこで受けられますか?
サポートやディスカッションについては、[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).