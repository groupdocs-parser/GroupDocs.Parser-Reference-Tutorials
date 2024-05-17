---
title: テンプレート内のリンクされた位置にあるフィールドの操作
linktitle: テンプレート内のリンクされた位置にあるフィールドの操作
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからデータを効率的に抽出する方法を学びます。コード例を使用したステップバイステップのチュートリアルです。
type: docs
weight: 12
url: /ja/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## 導入
GroupDocs.Parser for .NET は、ドキュメント解析とデータ抽出タスクを容易にするために設計された堅牢なライブラリです。PDF、DOCX、XLSX など、さまざまなファイル形式をサポートしています。その主な機能の 1 つはテンプレート ベースのデータ抽出です。これにより、ドキュメント内のフィールドを定義し、これらの定義済みテンプレートに基づいて特定のデータを抽出できます。
## 前提条件
始める前に、以下のものを用意してください。
- C#プログラミングの基礎知識
- システムにVisual Studioがインストールされている
- GroupDocs.Parser for .NETライブラリ（ダウンロードはこちら）[ここ](https://releases.groupdocs.com/parser/net/）)
- 作業に使用するサンプルドキュメントファイル

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間を含めます。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ステップ1: テンプレートフィールドを定義する
まず、正規表現とリンクされた位置を使用してテンプレート フィールドを定義します。
```csharp
//正規表現でフィールドを定義する
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
//特定の位置設定でリンクフィールドを定義する
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## ステップ2: テンプレートを作成する
次に、定義したフィールドを含むテンプレートを作成します。
```csharp
//定義されたフィールドでテンプレートを作成する
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## ステップ3: テンプレートを使用してドキュメントを解析する
さて、初期化しましょう`Parser`クラスを作成し、テンプレートを使用してドキュメントを解析します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //テンプレートに従ってドキュメントを解析する
    DocumentData data = parser.ParseByTemplate(template);
    //抽出されたデータを反復処理し、結果を印刷する
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## 結論
GroupDocs.Parser for .NET は、テンプレートを使用してドキュメントから構造化データを抽出するプロセスを簡素化します。フィールドを定義してテンプレートを適用することで、関連情報を効率的に抽出し、ドキュメント処理タスクの自動化と生産性を向上させることができます。

## よくある質問
### GroupDocs.Parser は暗号化された PDF ファイルからデータを抽出できますか?
はい、GroupDocs.Parser は、解析中にパスワードを提供することで、暗号化された PDF ファイルの解析をサポートします。
### テンプレートベースの抽出ではどのファイル形式がサポートされていますか?
GroupDocs.Parser は、PDF、DOCX、XLSX、PPTX、TXT など、幅広いファイル形式をサポートしています。
### GroupDocs.Parser の試用版はありますか?
はい、無料試用版は以下からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### ドキュメントのバッチ処理に GroupDocs.Parser を使用できますか?
はい、GroupDocs.Parser ではバッチ処理により複数のドキュメントを同時に解析できます。
### GroupDocs.Parser のテクニカル サポートはどこで受けられますか?
技術サポートを求めたり、コミュニティに参加したりすることができます。[GroupDocs フォーラム](https://forum.groupdocs.com/c/parser/17).