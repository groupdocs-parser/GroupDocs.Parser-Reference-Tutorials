---
title: URLからドキュメントを読み込む
linktitle: URLからドキュメントを読み込む
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出する方法を学習します。このチュートリアルでは、URL からドキュメントを読み込み、テキストを抽出する手順を段階的に説明します。
type: docs
weight: 13
url: /ja/net/document-loading/load-document-from-url/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出する方法について説明します。GroupDocs.Parser は、PDF、Word、Excel などのさまざまなドキュメント形式からテキスト、メタデータ、およびその他の情報を抽出するための強力なツールです。URL からドキュメントを読み込み、そのテキスト コンテンツを抽出するプロセスを段階的に説明します。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
1. Visual Studio: システムに Visual Studio をインストールします。
2.  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETを以下のサイトからダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/parser/net/).
3. C# の基本的な理解: C# プログラミング言語に精通していること。

## 名前空間のインポート
まず、C# コードに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

まず、URL からドキュメントを読み込み、そのテキスト コンテンツを抽出する方法を説明します。
## ステップ1: ドキュメントのURLを指定する
テキストを抽出するドキュメントの URL を指定します。
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## ステップ2: パーサーインスタンスを作成する
インスタンス化する`Parser`ドキュメント URL を持つクラス:
```csharp
using (Parser parser = new Parser(uri))
{
    //ここにコードを入力してください
}
```
## ステップ3: ドキュメントからテキストを抽出する
内部`using`ブロック、使用`parser.GetText()`ドキュメントからテキストを抽出するには:
```csharp
using (TextReader reader = parser.GetText())
{
    //ここにコードを入力してください
}
```
## ステップ4: 抽出したテキストを表示する
ドキュメントから抽出したテキストを読んで印刷します。
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出する基本について説明しました。これらの手順に従うことで、ドキュメントのテキスト抽出機能を C# アプリケーションに簡単に統合できます。

## よくある質問
### GroupDocs.Parser はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、PDF、Word、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser を使用してテキストとともにメタデータを抽出できますか?
はい、GroupDocs.Parser を使用すると、ドキュメントからメタデータ、テキスト、その他の情報を抽出できます。
### GroupDocs.Parser の試用版はありますか?
はい、GroupDocs.Parserの無料試用版は以下から入手できます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のドキュメントはどこにありますか?
 GroupDocs.Parserの詳細なドキュメントが利用可能です[ここ](https://reference.groupdocs.com/parser/net/).
### GroupDocs.Parser のテクニカル サポートを受けるにはどうすればよいですか?
GroupDocs.Parserフォーラムで技術サポートを求めたり質問したりできます。[ここ](https://forum.groupdocs.com/c/parser/17).