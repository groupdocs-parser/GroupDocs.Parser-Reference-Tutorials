---
date: '2026-07-16'
description: GroupDocs.Parser を使用して Java で spreadsheet thumbnail を作成し、preview Excel
  without Office、render Excel sheets as images の方法を学びます。このガイドでは、setup、implementation、practical
  use cases をカバーしています。
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: GroupDocs.Parser を使用した Java での spreadsheet thumbnail — preview Excel
  without Office と render Excel sheets as images。この step‑by‑step ガイドに従って、PNG previews
  を効率的に生成しましょう。
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: GroupDocs.Parser を使用した Java での spreadsheet thumbnail 作成
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: GroupDocs.Parser を使用した Java での spreadsheet thumbnail 作成
type: docs
url: /ja/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser を使用した Java のスプレッドシートサムネイル作成

Java で **スプレッドシートサムネイル作成** プログラムを探しているなら、ここが適切な場所です。このガイドでは、GroupDocs.Parser for Java を使用して `.xlsx` ワークブックから高品質な PNG プレビューを生成する方法を説明します。クイックサムネイル、スナップショットの共有、またはアプリケーション内でのドキュメントプレビュー機能の構築に最適です。このソリューションは Microsoft Office のインストールなしで動作し、大規模なワークブックにもスケールし、メモリ使用量を低く抑えます。

## クイック回答
- **“preview Excel” とは何ですか？** 各ワークシートページを表す画像ファイル（例: PNG）を生成します。  
- **推奨されるフォーマットはどれですか？** PNG はロスレス品質を提供し、ウェブサムネイルに適しています。  
- **ライセンスは必要ですか？** 開発には無料トライアルが利用でき、商用には商用ライセンスが必要です。  
- **画像解像度を変更できますか？** はい—`PreviewOptions` で DPI を調整します。  
- **他のフォーマットのプレビューは可能ですか？** GroupDocs.Parser は PDF、Word、その他多数の画像形式もサポートしています。

## GroupDocs.Parser を使用した “Excel のプレビュー方法” とは何ですか？

Excel ワークブックを読み込み、Microsoft Office を必要とせずに各シートを PNG 画像としてレンダリングします。GroupDocs.Parser はページを1つずつストリーミングし、ディスクに保存したり HTTP 経由で返したりできるロスレスサムネイルを生成するため、Web ベースのプレビューサービスに最適です。

GroupDocs.Parser は Excel ワークブックを読み取り、各シートをビジュアルページとしてレンダリングし、これらのページを画像ファイルにストリームできます。これにより、Office の相互運用やサードパーティのコンバータが不要になります。

## Excel プレビューに GroupDocs.Parser を使用する理由は？

GroupDocs.Parser を使用すべき理由は、任意の Java サーバーで動作し、Office のインストールが不要で、大規模なワークブックを低メモリで処理でき、設定可能な DPI でロスレス PNG 画像を生成できるからです。SDK は **100 以上の入力および出力フォーマット** をサポートし、200 ページのワークブックを 3 秒未満で処理でき、シートあたりのメモリ使用量を 50 MB 未満に抑えます。

- **Office のインストールは不要** – 任意のサーバーサイド Java 環境で実行できます。  
- **大きなファイルをサポート** – ページを1つずつストリーミングし、メモリ使用量を低く抑えます。  
- **高品質な出力** – DPI、フォーマット、レンダリングオプションを制御できます。  
- **クロスフォーマットの柔軟性** – 同じ API が PDF、Word 文書などでも機能します。

## 前提条件
- **Java Development Kit** (8 +)。  
- **IDE**（IntelliJ IDEA や Eclipse など）。  
- **GroupDocs.Parser for Java SDK** – [here](https://releases.groupdocs.com/parser/java/) からダウンロードしてください。  
- **Documentation** – 公式の [documentation](https://docs.groupdocs.com/parser/java/) を参照してください。  
- **Sample Excel file**（プレビューしたい `.xlsx`）。  
- **Maven または Gradle**（オプション）で依存関係を管理します。

## パッケージのインポート
これらのインポートにより、パーサー、プレビューオプション、ストリーム処理ユーティリティにアクセスできます。

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## スプレッドシートページプレビュー生成のステップバイステップガイド

### ステップ 1: パーサーインスタンスの初期化
`Parser` は GroupDocs.Parser のコアクラスで、スプレッドシートファイルへの読み取りアクセスを提供し、ページ単位のレンダリングを可能にします。  
Excel ワークブックを指す `Parser` オブジェクトを作成します。*try‑with‑resources* ブロックにより、パーサーは自動的にクローズされます。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro tip:** 絶対パスを使用するか、リソースフォルダーを設定して `FileNotFoundException` を回避してください。

### ステップ 2: プレビューオプションの準備
`PreviewOptions` は出力フォーマットや DPI などのレンダリングパラメータを設定します。  
`ICreatePageStream` は生成された各ページに対して出力ストリームを提供するコールバックインターフェイスです。各ページの保存方法を定義します。`ICreatePageStream` の実装は各ワークシートページごとに新しい `FileOutputStream` を返します。

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> このステップは **xlsx を png に変換** する箇所です—ストリームが PNG データをディスクに書き込みます。

### ステップ 3: レンダー情報を取得するデリゲートをアタッチ
各レンダリングされたシートの詳細（例: サイズ、シート名）が必要な場合は、コールバックを登録します。

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### ステップ 4: 出力フォーマットと DPI を指定
画像フォーマットとして PNG を選択し、品質とファイルサイズのバランスを取る DPI を設定します。

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> サムネイルを小さくしたい場合（例: 96）や高解像度印刷が必要な場合（例: 300）には DPI を調整してください。

### ステップ 5: プレビューを生成
すべて設定したら、`generatePreview` を呼び出します。SDK は各ワークシートを反復し、提供したストリームを呼び出します。

```java
parser.generatePreview(previewOptions);
```

### ステップ 6: `getOutputPath()` ヘルパーを定義
`getOutputPath()` はページ（シート）番号に基づいてファイル名を作成し、出力画像のフルパスを返します。フォルダー構造は自由にカスタマイズしてください。

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **一般的な落とし穴:** 事前に `output` ディレクトリを作成し忘れると `IOException` が発生します。プログラムで作成するか、存在することを確認してください。

## 完全な動作例（簡易版）

以下は、すべての要素を結びつけたコンパクトなバージョンです。**Java のスプレッドシートサムネイル作成** ワークフローを最初から最後まで示しています。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

このスニペットを実行すると、`output` フォルダーに `preview_page_1.png`、`preview_page_2.png`、… といったファイルが生成されます—それぞれが元の Excel ワークブックのシートを表しています。

## 一般的な問題と解決策

| Issue | Cause | Fix |
|-------|-------|-----|
| **画像が生成されない** | `getOutputPath` が無効なディレクトリを返す | 対象フォルダーが存在することを確認するか、`new File("output").mkdirs();` で作成してください。 |
| **大きなファイルでのメモリ不足エラー** | ワークブック全体を一度にロードする | ストリーミング方式（上記参照）を使用し、ページを1つずつ処理してください。 |
| **DPI が正しくない** | `setDpi` が呼び出されていない、またはデフォルト（96）に設定されている | `generatePreview` の前に `previewOptions.setDpi(希望の値);` を呼び出してください。 |
| **サポートされていない形式** | 破損した `.xlsx` をプレビューしようとする | Excel でファイルを検証するか、処理前に `Parser.isSupported` を使用してください。 |

## よくある質問

**Q: GroupDocs.Parser を使用して PDF や画像のプレビューを生成できますか？**  
A: はい、同じ API が PDF、Word 文書、その他多数の画像形式でも機能します。

**Q: 出力画像フォーマットを変更するには？**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`（または `Gif`, `Bmp` など）を呼び出してください。

**Q: 非常に大きなワークブックでパフォーマンスは問題ですか？**  
A: SDK はページをストリーミングするため、メモリ使用量が低く抑えられます。巨大なファイルの場合は、並列バッチ処理を検討してください。

**Q: プレビュー生成中のエラーはどのように処理すればよいですか？**  
A: コードを try‑catch ブロックで囲み（上記参照）、例外の詳細をログに記録してください。try‑with‑resources を使用しない場合は、`finally` ブロックでストリームを閉じることを確認してください。

**Q: ライブラリは Microsoft Office のインストールが必要ですか？**  
A: いいえ。GroupDocs.Parser は純粋な Java ソリューションで、Java 8+ をサポートする任意のプラットフォームで動作します。

---

**最終更新日:** 2026-07-16  
**テスト環境:** GroupDocs.Parser 23.11 (latest at time of writing)  
**作者:** GroupDocs

## 関連チュートリアル

- [プレビュー生成方法 – GroupDocs.Parser Java 用ドキュメントページプレビュー生成チュートリアル](/parser/java/page-preview-generation/)
- [GroupDocs.Parser を使用した Excel Java の解析: 完全ガイド](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [GroupDocs.Parser for Java を使用して Excel シートから生テキストを抽出する方法: ステップバイステップガイド](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)