---
date: '2026-08-26'
description: Aspose.OCR と GroupDocs.Parser を使用して Java で画像からテキストを抽出する方法。Java アプリケーションで高速
  OCR と構造化パースを実現します。
keywords:
- how to extract text from image java
- read text from photo using java
- Aspose OCR Java
- GroupDocs Parser for Java
lastmod: '2026-08-26'
og_description: Aspose.OCR と GroupDocs.Parser を使用して Java で画像からテキストを抽出する方法。このガイドでは、ステップバイステップのセットアップ、ストリーム処理、Java
  開発者向けのベストプラクティスを紹介します。
og_image_alt: Guide to extract text from image in Java using Aspose OCR and GroupDocs
  Parser
og_title: Aspose.OCR と GroupDocs.Parser を使用した Java での画像からテキスト抽出方法
schemas:
- author: GroupDocs
  dateModified: '2026-08-26'
  description: Learn how to extract text from image java with Aspose.OCR and GroupDocs.Parser,
    enabling fast OCR and structured parsing in Java applications.
  headline: How to extract text from image java using Aspose.OCR & GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract text from image java with Aspose.OCR and GroupDocs.Parser,
    enabling fast OCR and structured parsing in Java applications.
  name: How to extract text from image java using Aspose.OCR & GroupDocs.Parser
  steps:
  - name: '**Set the license for Aspose OCR:**'
    text: '**Set the license for Aspose OCR:**'
  - name: '**Initialize GroupDocs.Parser:**'
    text: '**Initialize GroupDocs.Parser:**'
  - name: '**Create the AsposeOCR instance:**'
    text: '**Create the AsposeOCR instance:**'
  - name: '**Read the image stream into a BufferedImage:**'
    text: '**Read the image stream into a BufferedImage:**'
  - name: '**Configure recognition settings (optional area selection):**'
    text: '**Configure recognition settings (optional area selection):**'
  - name: '**Run the recognition and handle warnings:**'
    text: '**Run the recognition and handle warnings:**'
  - name: '**Enable area detection:**'
    text: '**Enable area detection:**'
  - name: '**(Optional) Define specific regions** – reuse the rectangle logic from
      the previous section if you only care about certain parts of the image.'
    text: '**(Optional) Define specific regions** – reuse the rectangle logic from
      the previous section if you only care about certain parts of the image.'
  - name: '**Execute OCR and collect area information:**'
    text: '**Execute OCR and collect area information:**'
  type: HowTo
- questions:
  - answer: Add the Aspose OCR dependency from the Aspose Maven repository to your
      `pom.xml` and run `mvn clean install`. The JAR will be resolved automatically.
    question: How do I install Aspose OCR in my Maven project?
  - answer: Yes. Convert each PDF page to an image (for example, with Aspose.PDF),
      then feed each image stream to the OCR method described above.
    question: Can I extract text from multi‑page PDFs?
  - answer: Aspose OCR is optimized for printed characters. For handwriting, consider
      a dedicated handwriting‑recognition service such as Azure Computer Vision or
      Google Cloud Vision.
    question: Does this approach work with handwritten text?
  - answer: A trial license is sufficient for evaluation, but a full license removes
      watermarks, lifts usage limits, and provides priority support for commercial
      deployments.
    question: Is a license required for production use?
  - answer: Set the language on the `RecognitionSettings` object (e.g., `settings.setLanguage(Language.Spanish);`).
      This narrows the character set and dictionary, raising confidence scores.
    question: How can I improve accuracy for a specific language?
  type: FAQPage
tags:
- OCR Java
- Aspose OCR
- GroupDocs Parser
- image text extraction
title: Aspose.OCR と GroupDocs.Parser を使用した Java での画像からテキスト抽出方法
type: docs
url: /ja/java/ocr-integration/java-ocr-text-recognition-aspose-groupdocs-parser-guide/
weight: 1
---

# 画像からテキストを抽出する方法（Java） - Aspose.OCR と GroupDocs.Parser を使用して

モダンな Java アプリケーションでは、文書の画像を検索可能で編集可能なテキストに変換することが、オートメーション、コンプライアンス、分析のための重要な要件です。**How to extract text from image java** がこのガイドで回答する正確な質問です。Aspose.OCR の高精度光学文字認識と GroupDocs.Parser の強力なレイアウト認識を組み合わせ、ストリームを扱うことで、Web サービス、バッチジョブ、デスクトップツールのいずれにも適したソリューションを構築する方法を学びます。

## クイック回答
- **OCR を処理するライブラリは何ですか？** Aspose.OCR は印刷テキストに対して業界トップクラスの精度を提供します。  
- **OCR 出力を解析するコンポーネントはどれですか？** GroupDocs.Parser は生の文字列を構造化されたテーブル、フォーム、段落に変換します。  
- **最低限必要な Java バージョンは？** JDK 8 以上。  
- **本番環境でライセンスは必要ですか？** 評価用のトライアルで動作しますが、フルライセンスを取得すると透かしが除去され、すべての機能が利用可能になります。  
- **画像ストリームを直接処理できますか？** はい — 両 API は `InputStream` を受け取れるため、HTTP アップロードに最適です。

## 「画像からテキストを抽出する」とは？
画像からテキストを抽出するとは、スキャンしたページやレシートの写真などの視覚的文字を、コードで検索・インデックス・変換できるプレーンな Unicode 文字列に変換することです。OCR エンジンはピクセルパターンを解析し、文字形状を認識してテキスト表現を出力します。

## なぜ Aspose.OCR と GroupDocs.Parser を組み合わせるのか？
Aspose.OCR と GroupDocs.Parser を組み合わせることで、高品質な文字認識と強力なレイアウト解析の両方が得られます。Aspose.OCR が画像から生テキストを抽出し、GroupDocs.Parser がそのテキストを解析してテーブル、フォーム、マルチカラム構造を特定し、構造化データとして返します。

- **精度:** Aspose.OCR は業界トップクラスの認識率を実現します。  
- **柔軟性:** GroupDocs.Parser はテーブル、フォームフィールド、マルチカラムレイアウトを検出し、JSON または Java オブジェクトでデータを返します。  
- **ストリームフレンドリー:** 両ライブラリとも `InputStream` から直接読み取り、一時ファイルを不要にし、クラウドネイティブ展開を簡素化します。

## 前提条件
- **Java Development Kit:** JDK 8 以上がインストールされていること。  
- **Maven:** 推奨ビルドツール（手動で JAR を管理することも可）。  
- **Aspose OCR ライブラリ:** プロジェクトのクラスパスに JAR を追加。  
- **GroupDocs.Parser for Java:** Maven で追加（下記参照）または JAR をダウンロード。  
- **基本的な Java 知識:** ストリーム、例外処理、コレクションに慣れていること。

## GroupDocs.Parser for Java の設定

### Maven の設定
`pom.xml` にリポジトリと依存関係を追加します:

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
Maven を使用したくない場合は、最新の JAR を [GroupDocs Releases](https://releases.groupdocs.com/parser/java/) から取得してください。

### ライセンス取得
有効なライセンスを取得すると、Aspose OCR と GroupDocs.Parser の両方のフル機能がアンロックされます。無料トライアルで開始するか、ベンダーサイトから永続ライセンスを購入してください。

#### 基本的な初期化と設定
1. **Aspose OCR のライセンスを設定:**  
   `License` クラスはクラスパスから `license.lic` ファイルを読み込み、すべての OCR 機能を有効化します。

```java
   import com.aspose.ocr.License;
   
   // Initialize and set the Aspose OCR license
   License license = new License();
   license.setLicense("YOUR_LICENSE_PATH/AsposeOcrLicensePath");
   ```

2. **GroupDocs.Parser を初期化:**  
   基本的な解析には追加コードは不要です。認識された文字列を渡すと、ライブラリが OCR 出力形式を自動検出します。

## 画像からテキストを抽出する方法（Java）?
画像ストリームを読み込み、Aspose.OCR の `recognizePage` メソッドを実行し、得られたテキストを GroupDocs.Parser に渡すだけで、数行の Java コードで完了します。この直接的なアプローチにより中間ファイルが不要となり、データベースへの挿入や検索エンジンへのインデックス作成にすぐ使える構造化結果が得られます。  
`recognizePage` は提供された画像を処理し、認識されたテキストを文字列として返します。

## 機能: 画像ストリームからテキストを認識する

### 概要
このプロセスは受信した `InputStream` を `BufferedImage` に変換し、必要に応じて OCR を特定領域に限定し、Aspose OCR の `recognizePage` メソッドを呼び出します。返された文字列はその後 GroupDocs.Parser に渡され、レイアウト解析が行われます。

#### 手順の説明
1. **AsposeOCR インスタンスを作成:**  
   `OcrEngine` クラスはすべての認識タスクのエントリーポイントです。言語モデル、前処理フィルタ、出力設定をカプセル化します。

```java
   import com.aspose.ocr.AsposeOCR;
   
   AsposeOCR api = new AsposeOCR();
   ```

2. **画像ストリームを BufferedImage に読み込む:**  
   `BufferedImage` はピクセルデータにアクセス可能なメモリ上の画像を保持する Java クラスです。`ImageIO.read` はバイトストリームをラスタ画像にデコードし、OCR エンジンが解析できる形にします。`BufferedImage` を使用すると、認識前に画像を切り抜いたり回転したりできます。

```java
   import java.awt.image.BufferedImage;
   import javax.imageio.ImageIO;
   
   BufferedImage image = ImageIO.read(imageStream);
   ```

3. **認識設定を構成（オプションの領域選択）:**  
   関心領域が分かっている場合（例: パスポートの MRZ）には、矩形 (`Rectangle` オブジェクト) を指定して OCR を限定し、処理速度を向上させ誤認識を減らすことができます。

```java
   import com.aspose.ocr.RecognitionSettings;
   
   RecognitionSettings settings = new RecognitionSettings();
   
   // Example: limit OCR to a specific rectangle
   if (options != null && options.getRectangle() != null) {
       ArrayList<Rectangle> areas = new ArrayList<>();
       areas.add(new Rectangle(
           (int) options.getRectangle().getLeft(),
           (int) options.getRectangle().getTop(),
           (int) options.getRectangle().getSize().getWidth(),
           (int) options.getRectangle().getSize().getHeight()));
       settings.setRecognitionAreas(areas);
   }
   ```

4. **認識を実行し警告を処理:**  
   `recognizePage` の呼び出しは `RecognitionResult` を返し、抽出されたテキストと診断警告（例: 信頼度の低いセグメント）を含みます。`result.getWarnings()` をチェックして品質問題をログに記録してください。

```java
   import com.aspose.ocr.RecognitionResult;
   
   RecognitionResult result = api.RecognizePage(image, settings);
   
   if (options != null && options.getHandler() != null) {
       options.getHandler().onWarnings(pageIndex, result.warnings);
   }
   
   return result.recognitionText;
   ```

## 機能: 画像ストリームからテキスト領域を認識する

### 概要
フォーム上の個別フィールドなど、テキストブロックを個別に取得したい場合は領域検出を有効にします。OCR エンジンはテキストスニペットごとに矩形座標とテキストを返し、GroupDocs.Parser がそれらを構造化モデルにマッピングできます。

#### 手順の説明
1. **領域検出を有効化:**  
   `recognitionSettings.setDetectAreas(true)` を設定すると、エンジンは検出された各テキストスニペットの矩形座標を返します。

```java
   RecognitionSettings settings = new RecognitionSettings();
   settings.setDetectAreas(true);
   ```

2. **（オプション）特定領域を定義** – 前節の矩形ロジックを再利用し、画像の特定部分だけに関心がある場合に使用します。

3. **OCR を実行し領域情報を収集:**  
   結果は `TextArea` オブジェクトのコレクションを含み、各オブジェクトは `getRectangle()` と `getText()` を提供します。このコレクションを反復処理して DTO や JSON ペイロードに格納できます。

```java
   import java.awt.Rectangle;
   import java.util.ArrayList;
   
   ArrayList<PageTextArea> areas = new ArrayList<>();
   for (int i = 0; i < result.recognitionAreasRectangles.size(); i++) {
       Rectangle rect = result.recognitionAreasRectangles.get(i);
       String text = result.recognitionText;
   
       areas.add(new PageTextArea(
           text,
           new Page(pageIndex, pageSize),
           new Rectangle(
               new Point(rect.getX(), rect.getY()),
               new Size(rect.getWidth(), rect.getHeight()))));
   }
   
   return areas;
   ```

## 実用的な活用例
- **文書管理システム:** スキャンした PDF をインデックス化し、ユーザーが元のスキャンを開かずに全文検索できるようにします。  
- **自動データ入力:** 写真撮影したレシート、請求書、出荷ラベルから明細情報を抽出します。  
- **コンテンツデジタル化:** 印刷マニュアルを検索可能な電子書籍に変換し、テーブルや見出しを保持します。  
- **コンプライアンス監視:** 規制フォームをスキャンし、欠落または不正なフィールドを自動的に検出します。

## パフォーマンス上の考慮点
- **バッチ処理:** 1 JVM スレッドあたり最大 20 枚の画像をまとめて処理し、OCR モデルのロードオーバーヘッドを分散させます。  
- **画像品質:** 300 dpi 以上のスキャンは、150 dpi の画像に比べて認識精度を最大 15 % 向上させます。  
- **メモリ管理:** 各 OCR パス後に `bufferedImage.flush()` を呼び出し、同じ `OcrEngine` インスタンスを再利用してネイティブモデルをメモリに保持します。

## よくある問題とトラブルシューティング
| 症状 | 考えられる原因 | 対処法 |
|---------|--------------|-----|
| 文字化け | 低解像度画像 | 300 dpi 以上のスキャンを使用し、OCR 前に画像のシャープ化を適用 |
| テキストが返らない | 非対応のカラースペース（CMYK） | `BufferedImage.TYPE_INT_RGB` で RGB に変換 |
| メモリ不足エラー | 非常に大きな画像（例: >10 MP） | 画像をタイルに分割して処理するか、JVM ヒープを増やす（`-Xmx4g`） |

## よくある質問

**Q: Aspose OCR を Maven プロジェクトにインストールする方法は？**  
A: Aspose Maven リポジトリから Aspose OCR の依存関係を `pom.xml` に追加し、`mvn clean install` を実行してください。JAR は自動的に解決されます。

**Q: マルチページ PDF からテキストを抽出できますか？**  
A: はい。各 PDF ページを画像に変換（例: Aspose.PDF を使用）し、上記の OCR メソッドに画像ストリームを順次渡します。

**Q: 手書き文字にも対応していますか？**  
A: Aspose OCR は印刷文字に最適化されています。手書き文字の場合は、Azure Computer Vision や Google Cloud Vision などの専用手書き認識サービスの利用を検討してください。

**Q: 本番環境でライセンスは必須ですか？**  
A: 評価用のトライアルライセンスでも動作しますが、フルライセンスを取得すると透かしが除去され、使用制限が解除され、商用展開向けの優先サポートが受けられます。

**Q: 特定言語の精度を向上させるには？**  
A: `RecognitionSettings` オブジェクトで言語を設定します（例: `settings.setLanguage(Language.Spanish);`）。これにより文字セットと辞書が絞り込まれ、信頼度スコアが向上します。

**最終更新日:** 2026-08-26  
**テスト環境:** Aspose.OCR 23.12, GroupDocs.Parser 25.5  
**作者:** Aspose  

## 関連チュートリアル

- [GroupDocs.Parser OCR チュートリアル – Java 統合ガイド](/parser/java/ocr-integration/)
- [Java で GroupDocs.Parser を使用して docx からテキストを抽出する方法 – 包括的ガイド](/parser/java/text-extraction/extract-text-word-docs-groupdocs-parser-java/)