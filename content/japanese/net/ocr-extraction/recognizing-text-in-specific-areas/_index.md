---
title: 特定の領域のテキストを認識する
linktitle: 特定の領域のテキストを認識する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、OCR 機能を使用してドキュメント内の特定の領域からテキストを抽出する方法を学習します。
weight: 13
url: /ja/net/ocr-extraction/recognizing-text-in-specific-areas/
---

# 特定の領域のテキストを認識する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、ドキュメント内の特定の領域からテキストを認識して抽出する方法について説明します。GroupDocs.Parser は、開発者が PDF、Word、Excel、PowerPoint などのさまざまなドキュメント形式を操作できるようにする強力なドキュメント解析ライブラリです。具体的には、GroupDocs.Parser の OCR (光学式文字認識) 機能を活用して、ドキュメント内の定義された領域からテキストを抽出することに焦点を当てます。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
1. Visual Studio IDE: マシンに Visual Studio がインストールされていることを確認してください。
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETを以下のサイトからダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/parser/net/).
3. ドキュメント サンプル: テキストを抽出するサンプル ファイル (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートします。
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

GroupDocs.Parser for .NET を使用して、プロセスを詳細な手順に分解してみましょう。
## ステップ1: OCRコネクタを使用してパーサー設定を作成する
まず、インスタンスを作成します`ParserSettings`クラスを作成し、OCRコネクタで初期化します。`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## ステップ2: 設定を使用してパーサーをインスタンス化する
次に、インスタンスを作成します`Parser`クラスに、以前に作成した`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    //コード スニペットは続きます...
}
```
交換する`"YourSampleFile.pdf"`対象ドキュメントへのパスを入力します。
## ステップ3: テキスト領域の抽出オプションを構成する
インスタンスを作成する`PageTextAreaOptions`OCRベースのテキスト抽出を有効にするには:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
セット`true`OCR を有効にしてテキスト認識精度を向上させます。
## ステップ4: テキスト領域を抽出する
呼び出す`parser.GetTextAreas(options)`ドキュメントからテキスト領域を抽出するには:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## ステップ5: 抽出されたテキスト領域を処理する
抽出されたテキスト領域を反復処理し、テキスト、位置、およびサイズの情報を取得します。
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## 結論
このチュートリアルでは、OCR 機能を備えた GroupDocs.Parser for .NET を使用して、ドキュメント内の特定の領域からテキストを抽出するプロセスを説明しました。これらの手順に従うことで、GroupDocs.Parser の解析機能を効果的に活用し、テキスト抽出タスクをプログラムで処理できます。

## よくある質問
### GroupDocs.Parser はスキャンされたドキュメントからテキストを抽出できますか?
はい、GroupDocs.Parser は、ドキュメント内のスキャンされた画像からテキストを抽出するための OCR をサポートしています。
### GroupDocs.Parser ではどのドキュメント形式がサポートされていますか?
GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX、TXT など、幅広い形式をサポートしています。
### GroupDocs.Parser はドキュメントのバッチ処理に適していますか?
はい、GroupDocs.Parser は、ドキュメントの解析と抽出のバッチ処理タスクを効率的に処理できます。
### GroupDocs.Parser を使用してテキスト抽出オプションをカスタマイズできますか?
はい、GroupDocs.Parser は、特定の要件に基づいてテキスト抽出をカスタマイズするためのさまざまなオプションを提供します。
### GroupDocs.Parser はドキュメントからメタデータを抽出するためのサポートを提供していますか?
はい、GroupDocs.Parser では、サポートされているドキュメント形式から作成者、作成日などのメタデータを抽出できます。