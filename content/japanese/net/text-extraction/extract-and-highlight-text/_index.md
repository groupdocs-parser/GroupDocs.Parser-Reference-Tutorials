---
title: テキストの抽出と強調表示
linktitle: テキストの抽出と強調表示
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出し、強調表示する方法を学びます。.NET プロジェクトで効率的にテキストを抽出するための簡単な手順です。
weight: 11
url: /ja/net/text-extraction/extract-and-highlight-text/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出し、強調表示する方法について説明します。GroupDocs.Parser は、さまざまなドキュメント形式を解析し、高度なテキスト抽出操作を実行できる強力なライブラリです。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: .NET 開発用に Visual Studio をインストールします。
-  GroupDocs.Parser for .NET: GroupDocs.Parser for .NETをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
- サンプル ファイル: テキスト抽出用のサンプル ドキュメントを用意します。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートすることから始めます。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサーインスタンスを作成する
インスタンス化する`Parser`サンプルファイルのパスでクラスを作成します:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //ここに抽出と強調表示のロジックを追加します
}
```
## ステップ2: テキストを抽出して強調表示する
さて、`using`ブロックでは、テキストを抽出して強調表示できます。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //最大3語で位置2のハイライトを抽出します
    HighlightItem highlight = parser.GetHighlight(2, true, new HighlightOptions(3));
    //ハイライト抽出がサポートされているかどうかを確認する
    if (highlight == null)
    {
        Console.WriteLine("Highlight extraction isn't supported");
        return;
    }
    //抽出したハイライトを印刷する
    Console.WriteLine($"At {highlight.Position}: {highlight.Text}");
}
```

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出し、強調表示する基本的な方法について説明しました。このライブラリの機能をさらに詳しく調べて、より高度なテキスト抽出タスクを実行することもできます。

### よくある質問
### GroupDocs.Parser for .NET はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Parser は、DOCX、PDF、TXT など、幅広いファイル形式をサポートしています。
### GroupDocs.Parser を使用してドキュメントから特定のセクションまたは要素を抽出できますか?
はい、GroupDocs.Parser を使用すると、テキスト、画像、表、メタデータを正確に抽出できます。
### GroupDocs.Parser は大きなドキュメントに適していますか?
はい、GroupDocs.Parser は大きなドキュメントを効率的に処理するように最適化されています。
### GroupDocs.Parser 関連のクエリのサポートはどこで受けられますか?
訪問[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)コミュニティのサポートとディスカッションのため。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
あなたは[一時ライセンスはこちら](https://purchase.groupdocs.com/temporary-license/)テスト目的のため。