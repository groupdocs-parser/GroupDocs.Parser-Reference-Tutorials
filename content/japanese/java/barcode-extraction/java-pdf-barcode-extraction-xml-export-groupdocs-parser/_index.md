---
date: '2026-02-19'
description: GroupDocs.Parser を使用して Java の PDF で QR コードを読み取り、バーコードデータを XML にエクスポートする方法を学びましょう。
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: GroupDocs.Parser を使用した Java PDF で QR コードを読み取る方法
type: docs
url: /ja/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Java PDF で QR コードを読み取る方法（GroupDocs.Parser 使用）

現代のビジネスワークフローでは、PDF ドキュメントから **QR コードを読み取る方法** が、手作業によるデータ入力のボトルネックと完全自動化パイプラインの差を生むことがあります。出荷明細書、小売レシート、製品カタログなどを扱う場合でも、QR 情報を迅速かつ確実に抽出できることが重要です。本チュートリアルでは、**GroupDocs.Parser for Java** を使用して PDF から QR コード（およびその他のバーコード）を読み取り、下流システムが利用できるクリーンな XML ファイルへエクスポートする手順を解説します。

## Quick Answers
- **GroupDocs.Parser for Java の役割は？** PDF ファイルを読み取り、バーコードなどの構造化データを抽出します。  
- **QR コードを抽出する方法は？** `BarcodeOptions` に QR タイプを設定し、`parser.getBarcodes()` を呼び出します。  
- **Java で QR コードを読み取れますか？** はい、オプションでバーコードタイプを `"QR"` に設定すれば可能です。  
- **ライセンスは必要ですか？** テスト用のトライアルは利用可能ですが、本番環境では商用ライセンスが必要です。  
- **必要な Java バージョンは？** Java 8 以上が推奨されます。

## PDF 処理における「QR コードを読み取る」とは何か？
PDF から QR コードを読み取るとは、各ページを走査して QR でエンコードされた画像を検出し、埋め込まれたデータをデコードしてプログラムが扱いやすい形式で返すことです。GroupDocs.Parser は低レベルの画像解析を抽象化するため、ピクセル単位の操作に時間を取られることなくビジネスロジックに集中できます。

## なぜ GroupDocs.Parser を QR 抽出に使うのか？
- **高精度:** 組み込みの画像処理アルゴリズムが低解像度スキャンでも正確に検出します。  
- **パフォーマンスオプション:** `QualityMode.Low` を選べば高速処理、`QualityMode.High` で最高精度を実現。  
- **クロスフォーマット対応:** PDF だけでなく画像や Office 文書でも利用でき、ファイル種別が変わっても同一コードベースで処理可能です。

## 前提条件
- **GroupDocs.Parser for Java**（バージョン 25.5 以降）。  
- Maven または手動での JAR ダウンロード。  
- Java 8 以上の開発環境（IntelliJ IDEA、Eclipse、または任意のエディタ）。

## GroupDocs.Parser for Java のセットアップ
### Maven を使用する場合
`pom.xml` に GroupDocs リポジトリと依存関係を追加します。

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

### 直接ダウンロードする場合
または、[GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) から最新 JAR を取得してください。

#### ライセンス取得手順
- **無料トライアル:** フル機能が利用できる 30 日間トライアル。  
- **一時ライセンス:** 延長評価用に一時キーをリクエスト。  
- **購入:** 本番環境向けに商用ライセンスを取得。

### 基本的な初期化とセットアップ
解析対象の PDF を指す `Parser` インスタンスを作成します。

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

## Java PDF で QR コードを読み取る手順（GroupDocs.Parser 使用）
### 手順 1: バーコードサポートの確認
抽出を試みる前に、対象ドキュメント形式がバーコードスキャンに対応しているか確認します。

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*解説:* このガードにより、未対応のファイルタイプで実行時エラーが発生するのを防ぎます。

### 手順 2: バーコードオプションの設定（Java で QR コードを読む）
スキャン品質を設定し、対象が QR コードであることを指定します。

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*解説:* `QualityMode.Low` は処理速度を向上させ、精度が必要な場合は `High` に切り替えてください。`"QR"` 引数はエンジンに QR タイプのバーコードのみを検索させます。

### 手順 3: QR データの抽出
PDF の各ページからバーコード情報を取得します。

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*解説:* `parser.getBarcodes` は `PageBarcodeArea` オブジェクトのイテラブルコレクションを返し、各オブジェクトにデコードされた QR 値とページ上の位置情報が含まれます。

## 抽出データを XML にエクスポート
### 手順 4: XML エクスポーターの初期化
バーコードコレクションを整然とした XML ファイルに変換するエクスポーターを作成します。

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*解説:* `XmlExporter` はバーコードオブジェクトを標準 XML 形式にシリアライズし、ERP や在庫管理システムとの連携に適した形にします。

### 手順 5: XML ファイルの書き出し
抽出した QR 情報をディスクに保存します。

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*解説:* 生成された `data.xml` には QR コードごとに `<Barcode>` 要素が作成され、ページ番号、座標、デコード値が属性として格納されます。

## 実務での活用例
1. **在庫管理:** 入荷 PDF に含まれる QR タグを読み取り、在庫データベースを自動更新。  
2. **サプライチェーン可視化:** ロジスティクス文書に埋め込まれた QR 識別子を抽出し、リアルタイムで荷物を追跡。  
3. **小売レシート:** デジタルレシートに印刷された QR コードからプロモーション情報や保証情報を取得。

## パフォーマンス上の考慮点
- **メモリ管理:** 非常に大きな PDF は、全体をメモリに読み込むのではなくページ単位でストリーミング処理してください。  
- **QualityMode の選択:** 大量処理は `Low`、低解像度スキャンは `High` を推奨。  
- **ライブラリの更新:** 最新のパフォーマンス改善やバグ修正を享受するため、GroupDocs.Parser を常に最新バージョンに保ちましょう。

## よくある問題とトラブルシューティング
| 症状 | 想定原因 | 対策 |
|------|----------|------|
| バーコードが返ってこない | バーコードタイプが誤って指定されている | `"QR"` を適切なタイプ（例: `"CODE_128"`）に変更 |
| 大容量 PDF で Out‑of‑memory エラー | ドキュメント全体を一度に読み込んでいる | ページごとに処理するか、JVM ヒープサイズを増やす（`-Xmx2g`） |
| XML が空になる | `exportBarcodes` を抽出前に呼び出している | `parser.getBarcodes(options)` がデータを返すことを確認してからエクスポート |

## FAQ（よくある質問）
**Q: 画像ファイルからもバーコードを抽出できますか？**  
A: はい、PNG、JPEG、TIFF などの一般的な画像形式からの抽出をサポートしています。

**Q: 認識可能なバーコード形式は？**  
A: QR、Code 39、Code 128、DataMatrix、PDF417 など多数。詳細は API ドキュメントをご参照ください。

**Q: パスワード保護された PDF はどう扱いますか？**  
A: `Parser` コンストラクタにパスワードを渡します：`new Parser(filePath, "password")`。

**Q: トライアル版は本番テストに十分ですか？**  
A: トライアルはフル機能を提供しますが、抽出データに透かしが付加されます。本番環境では商用ライセンスの取得が必要です。

**Q: PDF に QR と一次元バーコードが混在している場合は？**  
A: 複数の `BarcodeOptions` インスタンスを作成するか、タイプ配列を渡して一括スキャンしてください。

---

**最終更新日:** 2026-02-19  
**テスト環境:** GroupDocs.Parser 25.5  
**作者:** GroupDocs  

## リソース
- [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/parser)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)