---
title: ストリームからドキュメントを読み込む
linktitle: ストリームからドキュメントを読み込む
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser を使用して .NET のさまざまなドキュメント形式からテキストを抽出する方法を学習します。コード例を使用したステップバイステップ ガイド。
type: docs
weight: 12
url: /ja/net/document-loading/load-document-from-stream/
---
## 導入
.NET アプリケーションでのドキュメント処理の分野では、さまざまなファイル形式からテキストを抽出することが一般的な要件です。GroupDocs.Parser for .NET は、さまざまなドキュメントからテキストをシームレスに解析して抽出するための強力なソリューションを提供します。このチュートリアルでは、GroupDocs.Parser を使用してドキュメントからテキストを抽出するプロセスを段階的に説明します。
## 前提条件
GroupDocs.Parser for .NET の使用を開始する前に、次の設定がされていることを確認してください。
- 開発環境: Visual Studio またはその他の .NET 開発環境。
-  GroupDocs.Parser for .NETパッケージ: GroupDocs.Parser for .NETライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/parser/net/).
- ドキュメント サンプル: テキスト抽出用のサンプル ドキュメントを用意します。
## 名前空間のインポート
GroupDocs.Parser 機能にアクセスするには、まず必要な名前空間を .NET プロジェクトにインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

次の手順では、ストリームから GroupDocs.Parser を使用してドキュメントからテキストを抽出する方法を示します。
## ステップ1: ストリームからドキュメントを読み込む
```csharp
//ストリームを作成する
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    //ストリームを使用してParserクラスのインスタンスを作成する
    using (Parser parser = new Parser(stream))
    {
        //テキストをリーダーに抽出する
        using (TextReader reader = parser.GetText())
        {
            //文書からテキストを印刷する
            //テキスト抽出がサポートされていない場合、リーダーはnullになります
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
この例では、
- ドキュメントファイルのファイルストリームを開きます（`YourSampleFile.docx`）。
- 初期化する`Parser`ストリームを持つインスタンス。
- 使用`parser.GetText()`取得する`TextReader`抽出されたテキストが含まれます。
- ドキュメント形式でテキスト抽出がサポートされていない場合は、抽出されたテキストまたはメッセージを印刷します。
## 結論
GroupDocs.Parser for .NET は、さまざまなドキュメント形式からのテキスト抽出を簡素化し、開発者がアプリケーション内でテキスト コンテンツを効率的に処理および利用できるようにします。このチュートリアルで説明されている手順に従うことで、ドキュメント テキスト抽出機能を .NET プロジェクトにシームレスに統合できます。

## よくある質問
### GroupDocs.Parser for .NET ではどのようなドキュメント形式がサポートされていますか?
GroupDocs.Parser は、DOCX、PDF、XLSX、PPTX、EPUB など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Parser はドキュメントから画像やメタデータを抽出できますか?
はい、GroupDocs.Parser はさまざまな種類のドキュメントから画像、メタデータ、テキストを抽出できます。
### GroupDocs.Parser は .NET Core アプリケーションと互換性がありますか?
はい、GroupDocs.Parser は .NET Framework アプリケーションと .NET Core アプリケーションの両方と互換性があります。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスは以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser の詳細なサポートやドキュメントはどこで見つかりますか?
追加のサポートについては、[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17)または、[ドキュメンテーション](https://reference.groupdocs.com/parser/net/).
