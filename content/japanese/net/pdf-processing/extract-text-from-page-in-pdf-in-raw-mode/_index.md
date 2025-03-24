---
title: PDF のページからテキストを Raw モードで抽出する
linktitle: PDF のページからテキストを Raw モードで抽出する
second_title: GroupDocs.Parser .NET API
description: C# で GroupDocs.Parser を使用して PDF からテキストを抽出します。この強力な .NET ライブラリを使用して、効率的な PDF テキスト抽出を学習します。
weight: 16
url: /ja/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、raw モードを使用して PDF ドキュメントのページからテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式をプログラムで操作できるようにする強力なツールです。
## 前提条件
このチュートリアルを開始する前に、次のものを用意してください。
- マシンに Visual Studio がインストールされています。
- C# プログラミングの基礎知識。
- GroupDocs.Parser for .NETライブラリは、[ここからダウンロード](https://releases.groupdocs.com/parser/net/).
- テスト用のサンプル PDF ファイル。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートしてください。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`サンプル PDF ファイルへのパスを指定してクラスを作成します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //ここにコードを入力してください
}
```
## ステップ 2: ドキュメント情報を取得し、ページを反復処理する
次に、ドキュメント情報を取得し、各ページを反復処理してテキストを抽出します。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //テキスト抽出のコードはここに記入します
}
```
## ステップ3: 各ページからテキストを抽出する
ループ内では、`GetText`各ページからテキストを抽出して印刷する方法。
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NETを使用してPDFページからrawモードでテキストを抽出する方法を学びました。このプロセスでは、`Parser`たとえば、文書情報を取得し、各ページを反復処理し、`GetText`方法。

## よくある質問
### GroupDocs.Parser for .NET とは何ですか?
GroupDocs.Parser for .NET は、開発者がさまざまなファイル形式からテキスト、メタデータ、およびその他の情報をプログラムで抽出できるようにするドキュメント解析 API です。
### GroupDocs.Parser for .NET をダウンロードするにはどうすればいいですか?
ライブラリは以下からダウンロードできます。[GroupDocsウェブサイト](https://releases.groupdocs.com/parser/net/).
### 無料トライアルはありますか？
はい、GroupDocs.Parser for .NETの無料トライアルはこちらからご利用いただけます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser for .NET のサポートはどこで見つかりますか?
技術サポートやコミュニティサポートについては、[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser for .NET のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます。[購入ページ](https://purchase.groupdocs.com/buy)または一時ライセンスを取得する[ここ](https://purchase.groupdocs.com/temporary-license/).