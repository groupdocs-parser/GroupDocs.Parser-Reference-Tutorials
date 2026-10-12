---
date: '2026-10-12'
description: JavaでGroupDocs.Parserを使用してPDFからQRコードを抽出し、バーコードデータをXMLにエクスポートして下流処理に活用する方法を学びましょう。
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: JavaでGroupDocs.Parserを使用してPDFからQRコードを抽出し、バーコードデータをXMLにエクスポートして下流処理に活用する方法を学びましょう。
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: JavaでPDFからQRコードを抽出し、GroupDocs.Parserを使用してバーコードデータをXMLにエクスポートする方法
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: JavaでPDFからQRコードを抽出し、GroupDocs.Parserを使用してバーコードデータをXMLにエクスポートする方法
type: docs
url: /ja/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# JavaでGroupDocs.Parserを使用してPDFからQRを抽出する方法

現代のビジネスワークフローでは、**PDFからQRを抽出**することで、手動のデータ入力のボトルネックを完全に自動化されたパイプラインに変えることができます。出荷明細書、小売レシート、製品カタログなどを扱う場合でも、QR情報を迅速かつ確実に取得することは、下流システムにとって不可欠です。このチュートリアルでは、**GroupDocs.Parser for Java** を使用して PDF から QR コード（および他のバーコード）を読み取り、結果をクリーンな XML ファイルにエクスポートし、ERP、在庫、または分析プラットフォームで利用できるようにする手順を説明します。

## クイック回答
- **GroupDocs.Parser for Java は何をしますか？** PDF ファイルを読み取り、バーコード、テーブル、テキストなどの構造化データを抽出します。  
- **QR コードを抽出するには？** `BarcodeOptions` を QR タイプに設定し、`parser.getBarcodes()` を呼び出します。  
- **Java で QR コードを読み取れますか？** はい—オプションでバーコードタイプを `"QR"` に設定します。  
- **ライセンスは必要ですか？** テストにはトライアルで動作しますが、本番環境では商用ライセンスが必要です。  
- **必要な Java バージョンは？** Java 8 以上が推奨されます。

## PDF 処理の文脈で「PDF から QR を抽出する」とは何か
PDF から QR を抽出するとは、各ページをスキャンして QR でエンコードされた画像を検出し、埋め込まれたデータをデコードして、プログラムが扱いやすい形式で返すことを意味します。GroupDocs.Parser は低レベルの画像解析を抽象化するため、ピクセル操作ではなくビジネスロジックに集中できます。

## QR 抽出に GroupDocs.Parser を使用する理由
GroupDocs.Parser は **30 以上の入力フォーマット** をサポートし、**500 MB** までの PDF をメモリに全体を読み込まずに処理でき、低解像度のスキャンでも高精度な結果を提供します。速度重視なら `QualityMode.Low`、最高精度が必要なら `QualityMode.High` を選択でき、同じ API が PDF、画像、Office 文書で動作するため、複数のライブラリを使用する必要がなくなります。

## 前提条件
- **GroupDocs.Parser for Java**（バージョン 25.5 以降）。  
- Maven または手動で JAR をダウンロード。  
- Java 8 以上の開発環境（IntelliJ IDEA、Eclipse、または任意のエディタ）。

## GroupDocs.Parser for Java の設定
### Maven の使用
`pom.xml` に GroupDocs リポジトリと依存関係を追加します：

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### 直接ダウンロード
または、最新の JAR を [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) からダウンロードします。

#### ライセンス取得手順
- **無料トライアル:** フル機能セットの 30 日間トライアル。  
- **一時ライセンス:** 拡張評価用に一時キーをリクエスト。  
- **購入:** 本番展開用の商用ライセンスを取得。

### 基本的な初期化と設定
解析したい PDF を指す `Parser` インスタンスを作成します：

`Parser` は GroupDocs.Parser のコアクラスで、ドキュメントを表し、テキスト、テーブル、バーコードなどのコンテンツ抽出メソッドを提供します。

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## GroupDocs.Parser を使用して Java の PDF で QR コードを読み取る方法
GroupDocs.Parser を使用して Java の PDF で QR コードを読み取るには、パーサーインスタンスを作成し、QR タイプを対象とするバーコードオプションを設定し、バーコード抽出メソッドを呼び出し、返されたバーコードオブジェクトを処理します。このプロセスはシンプルで、任意の PDF ページで動作し、デコードされた値と位置メタデータを返して、さらに処理できるようにします。

### 手順 1: バーコードサポートの確認
抽出を試みる前に、ドキュメント形式がバーコードスキャンをサポートしているか確認してください：

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*説明:* このガードはサポートされていないファイルタイプでの実行時エラーを防止します。

### 手順 2: バーコードオプションの設定（Java で QR コードを読む）
`BarcodeOptions` は、検出するバーコードシンボルを指定し、スキャン品質モードを設定し、検出閾値などのパラメータを微調整できる構成オブジェクトで、対象の QR コードに対して最適なパフォーマンスを保証します。

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*説明:* `QualityMode.Low` は処理速度を上げます。より高い精度が必要な場合は `High` に切り替えてください。`"QR"` 引数はエンジンに QR タイプのバーコードのみを探すよう指示します。

### 手順 3: QR データの抽出
`parser.getBarcodes(options)` は提供された `BarcodeOptions` を使用してドキュメントをスキャンし、`PageBarcodeArea` オブジェクトのコレクションを返します。各オブジェクトはデコードされた QR 値、ページ番号、ページ内のバーコードの正確な座標を含み、正確な下流処理を可能にします。

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*説明:* `parser.getBarcodes` は `PageBarcodeArea` オブジェクトのイテラブルコレクションを返し、各オブジェクトはデコードされた QR 値とページ上の位置を含みます。

## 抽出データを XML にエクスポート
### 手順 4: XML エクスポーターの初期化
`XmlExporter` はバーコードオブジェクトのコレクションを整然とした XML ドキュメントに変換するユーティリティクラスで、各バーコードにページインデックス、位置、デコードされた値の属性を持つ要素を自動生成し、他システムへ保存またはストリームできます。

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*説明:* `XmlExporter` はバーコードオブジェクトを標準 XML にシリアライズし、ERP や在庫システムとの統合にすぐ使える形にします。

### 手順 5: XML ファイルの書き込み
抽出した QR 情報をディスクに保存します：

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*説明:* 生成された `data.xml` には QR コードごとに 1 つの `<Barcode>` 要素が含まれ、ページ番号、座標、デコードされた値の属性があります。

## 実用的な応用例
1. **在庫管理:** 入荷 PDF の QR タグを読み取り、在庫データベースを自動的に更新。  
2. **サプライチェーンの可視化:** ロジスティクス文書に埋め込まれた QR 識別子を抽出して、パッケージをリアルタイムで追跡。  
3. **小売レシート:** デジタルレシートに印刷された QR コードからプロモーションや保証情報を取得。

## パフォーマンス上の考慮点
- **メモリ管理:** 非常に大きな PDF は、ファイル全体をメモリに読み込むのではなく、ストリーミング方式でページを処理します。  
- **QualityMode の選択:** バルク処理には `Low` を使用し、低解像度スキャンの場合は `High` に切り替えます。  
- **ライブラリの更新:** 最新のパフォーマンス向上とバグ修正を利用できるよう、GroupDocs.Parser を常に最新に保ちます。

## よくある問題とトラブルシューティング
| 症状 | 考えられる原因 | 対策 |
|---------|--------------|-----|
| バーコードが返されない | バーコードタイプの指定が間違っている | `"QR"` を適切なタイプ（例: `"CODE_128"`）に変更します。 |
| 大きな PDF でメモリ不足エラー | ドキュメント全体を一度に読み込んでいる | ページごとに処理するか、JVM ヒープサイズを増やす（`-Xmx2g`）。 |
| 空の XML ファイル | 抽出前に `exportBarcodes` を呼び出した | エクスポート前に `parser.getBarcodes(options)` がデータを返すことを確認します。 |

## よくある質問
**Q: GroupDocs.Parser で画像ファイルからバーコードを抽出できますか？**  
A: はい、ライブラリは一般的な画像フォーマット（PNG、JPEG、TIFF）からのバーコード抽出をサポートしています。

**Q: 認識できるバーコード形式は何ですか？**  
A: QR、Code 39、Code 128、DataMatrix、PDF417 など多数。完全な一覧は API ドキュメントをご参照ください。

**Q: パスワード保護された PDF はどう扱いますか？**  
A: パスワードを `Parser` コンストラクタに渡します：`new Parser(filePath, "password")`。

**Q: トライアル版は本番テストに十分ですか？**  
A: トライアルはフル機能を提供しますが、抽出データに透かしが付加されます。本番環境では商用ライセンスを取得してください。

**Q: PDF に QR と一次元バーコードの両方が含まれる場合は？**  
A: 複数の `BarcodeOptions` インスタンスを作成するか、タイプの配列を渡して一度のスキャンで必要なすべてのフォーマットを検出します。

---

**最終更新日:** 2026-10-12  
**テスト環境:** GroupDocs.Parser 25.5  
**作者:** GroupDocs  

## リソース
- [GroupDocs.Parser Java ドキュメント](https://docs.groupdocs.com/parser/java/)
- [API リファレンス](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser のダウンロード](https://releases.groupdocs.com/parser/java/)
- [GitHub リポジトリ](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [無料サポートフォーラム](https://forum.groupdocs.com/c/parser)
- [一時ライセンス申請](https://purchase.groupdocs.com/temporary-license/)

## 関連チュートリアル
- [Java 用 GroupDocs.Parser で PDF バーコード抽出](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [GroupDocs.Parser for Java で URL から PDF をロードする方法](/parser/java/document-loading/)
- [Java で GroupDocs.Parser を使用して PDF フォームデータを抽出する](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)