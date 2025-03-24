---
title: ドキュメントページ領域から画像を抽出する
linktitle: ドキュメントページ領域から画像を抽出する
second_title: GroupDocs.Parser .NET API
description: Groupdocs.Parser for .NET を使用してドキュメントから画像を正確に抽出する方法を学びます。正確な画像抽出のために特定の領域をターゲットにする方法を学びます。
weight: 10
url: /ja/net/image-extraction/extract-images-from-document-page-area/
---
## 導入
このチュートリアルでは、Groupdocs.Parser for .NET を使用してドキュメント ページの特定の領域から画像を抽出する方法を学習します。このプロセスにより、ドキュメント内の定義された座標と寸法に基づいて、画像を正確にターゲットにして取得できます。
## 前提条件
始める前に、次のものがあることを確認してください。
- マシンに Visual Studio がインストールされている
- Groupdocs.Parser for .NETライブラリ。ダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/)
- 画像抽出に使用するサンプル文書ファイル
## 名前空間のインポート
Groupdocs.Parser 機能にアクセスするには、まず C# コードに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーインスタンスを初期化する
インスタンスを作成する`Parser`クラスを指定し、サンプル ドキュメント ファイルへのパスを指定します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここにコードを入力してください
}
```
## ステップ2: 抽出オプションを定義する
抽出オプションを定義して、画像を抽出する領域を指定します。`PageAreaOptions`そして提供する`Rectangle`ページ上の目的の領域を表します。
```csharp
PageAreaOptions options = new PageAreaOptions(new Rectangle(new Point(340, 150), new Size(300, 100)));
```
この例では、
- `(340, 150)`エリアの左上隅の座標を表す
- `300`エリアの幅です
- `100`エリアの高さです
## ステップ3: 画像を抽出する
呼び出し`GetImages`方法の`Parser`インスタンスに定義された`PageAreaOptions` これは列挙可能なコレクションを返します`PageImageArea`抽出された画像を含むオブジェクト。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages(options);
```
## ステップ4: 抽出サポートを確認する
指定されたドキュメントに対して抽出操作がサポートされているかどうかを確認します。`images`コレクションは`null`画像の抽出はサポートされていません。
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## ステップ5: 抽出した画像を反復処理する
ループする`images`抽出された各画像を処理するコレクション。抽出された画像は`PageImageArea`オブジェクト、ページ インデックス、四角形の詳細、画像の種類などを提供します。
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
    //各画像に対してさらに処理を施すことができる
}
```
## 結論
おめでとうございます! Groupdocs.Parser for .NET を使用して、ドキュメントの特定の領域から画像を抽出する方法を学習しました。このアプローチにより、定義された座標に基づいて正確な画像抽出が可能になり、ドキュメントからターゲットを絞った画像を取得できるようになります。

## よくある質問
### この方法を使用して PDF ファイルから画像を抽出できますか?
はい、Groupdocs.Parser は PDF ファイルを含むさまざまなドキュメント形式からの画像抽出をサポートしています。
### 画像抽出中に例外を処理するにはどうすればよいですか?
抽出プロセス中に発生する可能性のある例外を処理するには、try-catch ブロックを使用できます。
### Groupdocs.Parser for .NET の試用版はありますか?
はい、無料トライアルをご利用いただけます[ここ](https://releases.groupdocs.com/).
### Groupdocs.Parser は暗号化されたドキュメントやパスワードで保護されたドキュメントからの抽出をサポートしていますか?
はい、Groupdocs.Parser は適切な権限を持つパスワードで保護されたドキュメントからの抽出を処理できます。
### Groupdocs.Parser の技術サポートはどこで受けられますか?
技術サポートやディスカッションについては、[Groupdocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).