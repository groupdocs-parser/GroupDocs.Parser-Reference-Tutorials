---
title: Word文書からテキストを抽出する
linktitle: Word文書からテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出する方法を学習します。コード例を使用したステップバイステップ ガイド。
weight: 15
url: /ja/net/word-document-processing/extract-text-from-word-document/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者が Word 文書、PDF など、さまざまな文書形式を操作できるようにする強力な .NET ライブラリです。このガイドを読み終えると、簡単な C# コードを使用して Word ファイルからテキストを効率的に抽出できるようになります。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
- Visual Studio (または任意の C# 開発環境)
- GroupDocs.Parser for .NETライブラリがインストールされている（ダウンロード[ここ](https://releases.groupdocs.com/parser/net/）)
- C#プログラミングの基礎知識

## 名前空間のインポート
まず、GroupDocs.Parser 機能にアクセスするために、C# プロジェクトに必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず、`Parser`クラスは、Word 文書へのパスを提供します。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //テキスト抽出のコードはここに記入します
}
```
交換する`"YourSampleFile.docx"`実際の Word 文書へのパスを入力します。
## ステップ 2: テキストを TextReader に抽出する
以内`using`ブロックの`Parser`たとえば、`GetText()`テキストコンテンツを抽出する方法`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    //テキスト処理コードはここに記入します
}
```
## ステップ3: 抽出したテキストを読み取って表示する
さて、`TextReader`ブロックを使用すると、Word 文書から抽出したテキストを読み取って印刷できます。
```csharp
using (TextReader reader = parser.GetText())
{
    //抽出したテキストを読んで印刷する
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
おめでとうございます! GroupDocs.Parser for .NET を使用して Word 文書からテキストを抽出する方法を学習しました。このシンプルでありながら強力なライブラリを使用すると、テキスト抽出機能を .NET アプリケーションに効率的に統合できます。

## よくある質問
### GroupDocs.Parser は .NET のすべてのバージョンと互換性がありますか?
はい、GroupDocs.Parser for .NET は .NET Framework 4.6.1 以降のバージョンと互換性があります。
### 暗号化またはパスワードで保護された Word 文書からテキストを抽出できますか?
GroupDocs.Parser は、パスワードで保護された Word 文書からのテキストの抽出をサポートしています。
### GroupDocs.Parser は Word 文書以外の文書形式もサポートしていますか?
はい、GroupDocs.Parser は PDF、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
 GroupDocs.Parserの一時ライセンスをリクエストできます[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser に関する追加サポートや質問はどこで受けられますか?
 GroupDocs.Parserフォーラムにアクセスしてください[ここ](https://forum.groupdocs.com/c/parser/17)サポートとディスカッションのため。