---
title: 文書から書式設定されたテキストを抽出する
linktitle: 文書から書式設定されたテキストを抽出する
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントから書式設定されたテキストを抽出する方法を学習します。アプリケーション用のシンプルで効率的なテキスト抽出。
type: docs
weight: 10
url: /ja/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、さまざまな種類のドキュメントから書式設定されたテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者がドキュメントを簡単かつ効率的に操作できるようにする強力なライブラリです。このガイドを読み終えると、テキスト抽出機能を .NET アプリケーションにシームレスに統合できるようになります。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: システムに Visual Studio がインストールされていることを確認してください。
-  GroupDocs.Parser for .NET: GroupDocs.Parserライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
- ドキュメント サンプル: テキスト抽出用のサンプル ドキュメント (PDF、DOCX など) を準備します。
## 名前空間のインポート
まず、C# コードに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ステップ1: パーサークラスのインスタンスを作成する
まず初期化する`Parser`サンプル ドキュメントへのパスを含むオブジェクト。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //テキスト抽出コードはここに記載します
}
```
交換する`"YourSampleFile.pdf"`ドキュメント ファイルへのパスを入力します。

## ステップ2: フォーマットされたテキストを抽出する
以内`using`ブロックするには、`GetFormattedText`文書からフォーマットされたテキストを抽出するメソッド。希望する出力形式（HTMLなど）を指定するには、`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //フォーマットされたテキストをリーダーに抽出する
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //抽出がサポートされているかどうかを確認する
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            //抽出したテキストを読み取って表示する
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## 結論
おめでとうございます! GroupDocs.Parser for .NET を使用してドキュメントから書式設定されたテキストを抽出する方法を学習しました。この多目的ライブラリにより、アプリケーション内でのテキスト処理と分析の可能性が広がります。

## よくある質問
### Q: GroupDocs.Parser はパスワードで保護されたドキュメントからテキストを抽出できますか?
A: はい、GroupDocs.Parser はパスワードで保護されたドキュメントからのテキストの抽出をサポートしています。
### Q: GroupDocs.Parser ではどのドキュメント形式がサポートされていますか?
A: GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX など、幅広い形式をサポートしています。
### Q: GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
 A: 臨時免許証は以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### Q: GroupDocs.Parser はドキュメントからの画像抽出をサポートしていますか?
A: はい、GroupDocs.Parser はテキスト抽出とともに画像抽出もサポートしています。
### Q: GroupDocs.Parser に関する追加サポートや質問はどこで受けられますか?
 A: をご覧ください[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)サポートとディスカッションのため。