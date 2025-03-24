---
title: ローカルディスクからドキュメントを読み込む
linktitle: ローカルディスクからドキュメントを読み込む
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用して、さまざまなドキュメント形式からテキストを抽出する方法を学びます。C# を使用した簡単で効率的なテキスト抽出。
weight: 11
url: /ja/net/document-loading/load-document-from-local-disk/
---

# ローカルディスクからドキュメントを読み込む

## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出する方法について説明します。GroupDocs.Parser は、開発者がさまざまなドキュメント形式を解析し、プログラムでテキスト コンテンツを抽出できるようにする強力なライブラリです。このライブラリを使用してテキスト抽出を開始するために必要な手順について説明します。
## 前提条件
始める前に、次の前提条件がインストールされていることを確認してください。
- Visual Studio がシステムにインストールされています。
- C# プログラミング言語に関する基本的な知識。
-  GroupDocs.Parser for .NETライブラリがインストールされている（ダウンロード[ここ](https://releases.groupdocs.com/parser/net/)）。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## ステップ1: ローカルディスクからドキュメントを読み込む
まず、ローカルディスクからドキュメントを読み込み、`"Your Sample File"`対象ドキュメントへのパスを入力します。
```csharp
//ファイルパスを設定する
string filePath = "Your Sample File";
//filePathを使用してParserクラスのインスタンスを作成する
using (Parser parser = new Parser(filePath))
{
    //テキストをリーダーに抽出する
    using (TextReader reader = parser.GetText())
    {
        //文書から抽出したテキストを印刷する
        //テキスト抽出がサポートされていない場合、リーダーはnullになります
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## 手順の説明
1. ファイルパスの設定: テキストを抽出したいドキュメントへのパスを指定します（`filePath`変数）。
2. パーサーインスタンスの作成:`Parser`クラスに合格して`filePath`.
3. テキストの抽出:`GetText()`方法の`Parser`インスタンスを取得する`TextReader`ドキュメントから抽出されたテキストを含むオブジェクト。
4. 抽出されたテキストの読み取り:`ReadToEnd()`方法の`TextReader`ドキュメントから抽出されたテキスト コンテンツ全体を取得します。
5. サポートされていない形式の処理: ドキュメント形式がテキスト抽出をサポートしていない場合、`reader`オブジェクトは`null`、このシナリオに応じて対処することができます。

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してドキュメントからテキストを抽出するための最初の手順について説明しました。このライブラリはドキュメント解析のための広範な機能を提供しており、開発者はアプリケーション内でさまざまなファイル形式を効率的に操作できます。

## よくある質問
### GroupDocs.Parser はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Parser は、PDF、Microsoft Office ドキュメント (Word、Excel、PowerPoint) など、幅広い形式をサポートしています。
### GroupDocs.Parser を使用してテキストとともにメタデータを抽出できますか?
はい、GroupDocs.Parser では、サポートされているドキュメント形式からテキスト コンテンツとメタデータの両方を抽出できます。
### GroupDocs.Parser に関するその他のリソースやサポートはどこで見つかりますか?
訪問[GroupDocs.Parser ドキュメント](https://tutorials.groupdocs.com/parser/net/)詳細なAPIリファレンスについては、[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17)コミュニティサポートのため。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
リクエストすることができます[一時ライセンス](https://purchase.groupdocs.com/temporary-license/)評価およびテストの目的で。
### GroupDocs.Parser の無料トライアルはありますか?
はい、ダウンロードできます[無料トライアル](https://releases.groupdocs.com/)GroupDocs.Parser のバージョン。