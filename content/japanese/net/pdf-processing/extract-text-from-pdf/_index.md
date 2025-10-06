---
title: PDFからテキストを抽出する
linktitle: PDFからテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して PDF ドキュメントからテキストを抽出する方法を学びます。開発者向けのステップバイステップのチュートリアルです。
weight: 14
url: /ja/net/pdf-processing/extract-text-from-pdf/
type: docs
---
# PDFからテキストを抽出する

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して PDF ドキュメントからテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者が PDF、Microsoft Office などのさまざまなドキュメント形式からテキスト、メタデータ、構造化データを抽出できるようにする強力な API です。
## 前提条件
始める前に、次のものがあることを確認してください。
- マシンに Visual Studio がインストールされています。
-  GroupDocs.Parser for .NETがインストールされています。ダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/).
- C# プログラミングの基礎知識。

## 名前空間のインポート
まず、C# コードに必要な名前空間をインポートすることから始めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ステップ1: パーサークラスのインスタンスを作成する
インスタンス化する`Parser`サンプル PDF ファイルへのパスを指定してクラスを作成します。
```csharp
//Parserクラスのインスタンスを作成する
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにコードを入力してください
}
```
## ステップ2: PDFからテキストを抽出する
以内`Parser`たとえば、`GetText()`PDF からテキストを抽出する方法:
```csharp
//テキストをリーダーに抽出する
using (TextReader reader = parser.GetText())
{
    //ここにコードを入力してください
}
```
## ステップ3: 抽出したテキストを読んで印刷する
さて、抽出したテキストを読んでみましょう`TextReader`そしてそれを印刷します:
```csharp
//抽出したテキストを印刷する
Console.WriteLine(reader.ReadToEnd());
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NETを使用してPDF文書からテキストを抽出する基本について説明しました。`Parser`クラスを使用してテキストを抽出し、抽出したコンテンツを印刷します。この API は、PDF やその他のドキュメント形式をプログラムで処理するための簡単な方法を提供します。

## よくある質問
### GroupDocs.Parser は PDF 以外のドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は DOCX、XLSX、PPTX など、幅広い形式をサポートしています。
### ライセンスを購入する前に GroupDocs.Parser を試すことはできますか?
はい、無料試用版を入手できます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のドキュメントはどこにありますか?
詳細なドキュメントが利用可能[ここ](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser のテクニカル サポートを受けるにはどうすればよいですか?
サポートフォーラムで助けを求めることができます[ここ](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを取得できる[ここ](https://purchase.groupdocs.com/temporary-license/).