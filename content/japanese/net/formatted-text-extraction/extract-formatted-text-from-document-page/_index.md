---
title: ドキュメントページから書式設定されたテキストを抽出する
linktitle: ドキュメントページから書式設定されたテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、ドキュメント ページから書式設定されたテキストを抽出します。効率的で信頼性の高いテキスト抽出ソリューションです。
weight: 11
url: /ja/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメント ページから書式設定されたテキストを抽出するプロセスについて説明します。このライブラリを使用すると、PDF、Word、Excel などのさまざまなドキュメント形式からテキストを効率的に解析して抽出できます。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio がシステムにインストールされています。
- C# プログラミングの基礎知識。
-  GroupDocs.Parser for .NETライブラリ。ダウンロードできます。[ここ](https://releases.groupdocs.com/parser/net/).

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートすることから始めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //コードはここに記入します
}
```
## ステップ2: フォーマットされたテキストの抽出がサポートされているかどうかを確認する
テキスト抽出を続行する前に、ドキュメントがフォーマットされたテキスト抽出をサポートしているかどうかを確認してください。
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## ステップ3: ドキュメント情報を取得する
ページ数など、ドキュメントに関する情報を取得します。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ステップ4: ドキュメントページを反復処理して書式設定されたテキストを抽出する
ドキュメントの各ページを反復処理し、指定されたオプション (Markdown 形式など) を使用してフォーマットされたテキストを抽出します。
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 結論
これで、GroupDocs.Parser for .NET を使用してドキュメント ページから書式設定されたテキストを抽出する方法がわかりました。このライブラリは、さまざまなファイル形式からテキストを抽出するための強力で使いやすいソリューションを提供します。

## よくある質問
### GroupDocs.Parser はさまざまなファイル形式を処理できますか?
はい、GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser は .NET Core と互換性がありますか?
はい、GroupDocs.Parser は .NET Core と .NET Framework をサポートしています。
### GroupDocs.Parser は抽出中にテキストの書式を保持しますか?
はい、GroupDocs.Parser はテキストを抽出するときにスタイルやフォントなどの書式を保持できます。
### GroupDocs.Parser を使用して画像とメタデータを抽出できますか?
はい、GroupDocs.Parser を使用すると、ドキュメントから画像、メタデータ、テキストを抽出できます。
### GroupDocs.Parser のサポートを受けるにはどうすればよいですか?
サポートを受けるには[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).