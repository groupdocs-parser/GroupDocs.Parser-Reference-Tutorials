---
title: ドキュメントから画像を抽出する
linktitle: ドキュメントから画像を抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用すると、ドキュメントから画像を簡単に抽出できます。ドキュメント処理機能と画像抽出タスクを効率的に合理化します。
type: docs
weight: 11
url: /ja/net/image-extraction/extract-images-from-document/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントから画像を抽出する方法について説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式からテキスト、メタデータ、画像などを抽出できるようにする強力なライブラリです。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- Visual Studio: マシンに Visual Studio をインストールします。
-  GroupDocs.Parser for .NET: GroupDocs.Parserをダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/parser/net/).
- サンプル ドキュメント: 画像を抽出するサンプル ドキュメント (PDF、DOCX など) を準備します。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル ドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにコードを入力してください
}
```
交換する`"YourSampleFile.pdf"`ドキュメント ファイルへのパスを入力します。
## ステップ2: ドキュメントから画像を抽出する
次に、`GetImages()`方法。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
の`GetImages()`メソッドはコレクションを返します`PageImageArea`ドキュメント内で見つかった画像を表すオブジェクト。
## ステップ3: 画像抽出サポートを確認する
画像を反復処理する前に、ドキュメントで画像抽出がサポートされているかどうかを確認します。
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
この手順により、ドキュメントに抽出可能な画像が含まれていることが保証されます。
## ステップ4: 抽出した画像を反復処理する
次に、抽出された画像を反復処理して、ページ インデックス、四角形の座標、画像の種類など、各画像の詳細情報にアクセスします。
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
このループは、抽出された各画像の場所や種類などの情報を出力します。

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してプログラムでドキュメントから画像を抽出する方法を学習しました。これらの手順に従うことで、ドキュメント画像抽出機能を .NET アプリケーションにシームレスに統合できます。

## よくある質問
### GroupDocs.Parser はすべてのドキュメント形式から画像を抽出できますか?
GroupDocs.Parser は、PDF、DOCX、XLSX など、さまざまな形式から画像を抽出できます。
### GroupDocs.Parser の無料トライアルはありますか?
はい、GroupDocs.Parserの無料トライアルは以下からご利用いただけます。[Webサイト](https://releases.groupdocs.com/).
### GroupDocs.Parser のドキュメントはどこにありますか?
 GroupDocs.Parserの詳細なドキュメントは以下にあります。[ここ](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
臨時免許証は、[一時ライセンスページ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser のサポートはどこで受けられますか?
技術サポートと支援については、[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).