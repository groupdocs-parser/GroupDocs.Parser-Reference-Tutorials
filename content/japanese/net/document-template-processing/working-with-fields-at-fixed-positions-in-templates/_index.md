---
title: テンプレート内の固定位置のフィールドの操作
linktitle: テンプレート内の固定位置のフィールドの操作
second_title: GroupDocs.Parser .NET API
description: GroupDocs.Parser for .NET を使用してドキュメントからデータを抽出する方法を学習します。コード例を含む包括的なチュートリアル。
weight: 11
url: /ja/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## 導入
このチュートリアルでは、GroupDocs.Parser for .NET を使用して、テンプレート内の固定位置にあるフィールドを操作する方法について説明します。GroupDocs.Parser は、開発者が PDF、Word、Excel などのさまざまなドキュメント形式からデータを抽出できるようにする強力なドキュメント解析ライブラリです。具体的には、テンプレート フィールドの定義と使用に焦点を当て、固定位置に基づいて対象となる情報を抽出する方法について説明します。
## 前提条件
始める前に、以下のものを用意してください。
- C# および .NET 開発に関する基本的な理解。
- Visual Studio がシステムにインストールされています。
- GroupDocs.Parser for .NETライブラリがインストールされています。ダウンロードはこちらから[ここ](https://releases.groupdocs.com/parser/net/).
- テスト用のサンプル ドキュメント ファイル。

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
まず、テンプレート内で固定位置のフィールドを定義します。このフィールドは、データが抽出される領域を表します。
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
ここ：
- `Rectangle`フィールドの位置とサイズを指定します。
- `Point(35, 135)`左上隅の座標を表します。
- `Size(100, 10)`フィールドの幅と高さを定義します。
- `"FromCompany"`このフィールドに割り当てられた名前です。
## ステップ2: テンプレートを作成する
定義されたフィールドを使用してテンプレートを構築します。
```csharp
Template template = new Template(new TemplateItem[] { field });
```
の`Template`オブジェクトは定義されたフィールドを保持します。
## ステップ3: テンプレートを使用してドキュメントを解析する
インスタンス化する`Parser`クラスをターゲット ドキュメント パスに関連付け、作成されたテンプレートを使用してドキュメントを解析します。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    //抽出されたデータを反復処理する
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
ここ：
- `Parser`サンプルドキュメントのファイルパスで初期化されます。
- `ParseByTemplate`メソッドは、提供されたテンプレートに基づいてデータを抽出するために使用されます。
- 抽出されたデータにアクセスするには`DocumentData`各項目は定義されたフィールドに対応します。

## 結論
このチュートリアルでは、GroupDocs.Parser for .NET を使用してテンプレート内の固定位置にあるフィールドを操作するプロセスについて説明しました。特定のフィールド位置を持つテンプレートを定義することで、開発者はさまざまなドキュメント形式から対象データを正確に抽出できます。

## よくある質問
### GroupDocs.Parser はすべてのドキュメント形式と互換性がありますか?
 GroupDocs.Parserは、PDF、Microsoft Word、Excel、PowerPointなど、幅広いファイル形式をサポートしています。[ドキュメンテーション](https://tutorials.groupdocs.com/parser/net/)詳細なリストについては、こちらをご覧ください。
### GroupDocs.Parser の一時ライセンスを取得するにはどうすればよいですか?
テスト目的の臨時ライセンスは以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Parser のサポートはどこで見つかりますか?
技術的なサポートやディスカッションについては、[GroupDocs.Parser フォーラム](https://forum.groupdocs.com/c/parser/17).
### 購入前に GroupDocs.Parser を試すことはできますか?
はい、無料トライアルでライブラリを探索できます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Parser のライセンスを購入するにはどうすればよいですか?
ライセンスを購入するには、[購入ページ](https://purchase.groupdocs.com/buy).