---
title: オプションを使用してドキュメントからバーコードを抽出する
linktitle: オプションを使用してドキュメントからバーコードを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからバーコードを抽出する方法を学びます。コード例と FAQ を含む包括的なチュートリアル。
type: docs
weight: 14
url: /ja/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからバーコードを抽出するプロセスについて説明します。GroupDocs.Parser は、PDF、Microsoft Word、Excel などのさまざまなドキュメント形式からテキスト、メタデータ、バーコードを抽出できる強力なライブラリです。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. 開発環境: マシンに Visual Studio がインストールされていることを確認します。
2.  GroupDocs.Parserライブラリ: GroupDocs.Parser for .NETライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
3. サンプル ドキュメント: 抽出用のバーコードを含むサンプル ドキュメント (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Parser 機能を利用するには、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル ドキュメントへのパスを渡すことでクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //次のステップで追加するコード
}
```
## ステップ2: バーコード抽出サポートを確認する
次に、ドキュメントがバーコード抽出をサポートしているかどうかを確認します。`Features`の財産`Parser`実例。
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## ステップ3: バーコード抽出オプションを定義する
次に、バーコード抽出のオプションを指定します。`BarcodeOptions`品質モードやバーコードの種類などのパラメータを設定できます。
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## ステップ4: ドキュメントからバーコードを抽出する
使用`GetBarcodes`方法の`Parser`定義されたオプションに基づいてバーコードを抽出するクラス。
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## ステップ5: 抽出したバーコードを反復して表示する
最後に、抽出されたバーコードを反復処理し、ページ インデックスと値を表示します。
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NETを使用してドキュメントからバーコードを抽出する方法を学びました。このプロセスでは、`Parser`たとえば、抽出オプションを定義し、抽出されたバーコードを反復処理します。GroupDocs.Parser は、さまざまなドキュメント形式からのバーコード抽出タスクを簡素化し、.NET アプリケーション内での効率的なドキュメント処理を可能にします。

## よくある質問
### GroupDocs.Parser は PDF ドキュメントからバーコードを抽出できますか?
はい、GroupDocs.Parser は、DOCX、XLSX などの他の形式とともに、PDF ドキュメントからのバーコード抽出をサポートしています。
### GroupDocs.Parser はどのようなバーコード タイプをサポートしていますか?
GroupDocs.Parser は、QR コード、コード 39、コード 128 など、さまざまなバーコード タイプをサポートしています。
### GroupDocs.Parser を商用利用する場合、ライセンスは必要ですか?
はい、商用利用には有効なライセンスが必要です。ライセンスは以下から取得できます。[ここ](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser はドキュメントのバッチ処理に適していますか?
はい、GroupDocs.Parser は、テキスト抽出、メタデータ取得、バーコード抽出のためのドキュメントのバッチ処理を効率的に処理できます。
### GroupDocs.Parser のテクニカル サポートはどこで受けられますか?
テクニカルサポートを受けたり、質問したりすることができます。[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17).