---
date: '2026-02-06'
description: GroupDocs.Parser for Java を使用して Excel ファイルをプレビューし、xlsx を PNG に変換する方法を学びます。このチュートリアルでは、セットアップ、実装、実用的な応用について説明します。
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: JavaでGroupDocs.Parserを使用してExcelファイルをプレビューする方法
type: docs
url: /ja/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser を使用した Java での Excel ファイルのプレビュー方法

プログラムで **Excel をプレビューする方法** を探しているなら、ここが適切な場所です。このガイドでは、GroupDocs.Parser for Java を使用して `.xlsx` ワークブックから画像プレビュー（PNG）を作成する手順を解説します。サムネイルの迅速な生成、スナップショットの共有、またはアプリケーション内でのドキュメントプレビュー機能の構築に最適です。

## クイック回答
- **“preview Excel” とは何ですか？** 各ワークシートページを表す画像ファイル（例: PNG）を生成することです。  
- **推奨フォーマットはどれですか？** PNG はロスレス品質を提供し、ウェブサムネイルに適しています。  
- **ライセンスは必要ですか？** 開発には無料トライアルで動作しますが、本番環境では商用ライセンスが必要です。  
- **画像解像度を変更できますか？** はい、`PreviewOptions` の DPI を調整します。  
- **他のフォーマットのプレビューは可能ですか？** GroupDocs.Parser は PDF、Word、その他多数の画像タイプもサポートしています。

## GroupDocs.Parser での “Excel のプレビュー方法” とは？

GroupDocs.Parser は Excel ワークブックを読み取り、各シートをビジュアルページとしてレンダリングし、これらのページを画像ファイルへストリーム出力できます。これにより、Office の相互運用やサードパーティのコンバータが不要になります。

## Excel プレビューに GroupDocs.Parser を使用する理由
- **Office のインストール不要** – 任意のサーバーサイド Java 環境で実行可能です。  
- **大容量ファイルに対応** – ページを1つずつストリーム処理し、メモリ使用量を抑えます。  
- **高品質な出力** – DPI、フォーマット、レンダリングオプションを制御できます。  
- **クロスフォーマットの柔軟性** – 同じ API が PDF、Word 文書などでも利用可能です。

## 前提条件
- **Java Development Kit**（8 以上）。  
- **IDE**（例: IntelliJ IDEA または Eclipse）。  
- **GroupDocs.Parser for Java SDK** – [here](https://releases.groupdocs.com/parser/java/) からダウンロード。  
- プレビューしたい **サンプル Excel ファイル**（`.xlsx`）。  
- 依存関係管理用の **Maven または Gradle**（オプション）。

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

### 手順 1: Parser インスタンスの初期化
`Parser` オブジェクトを作成し、対象の Excel ワークブックを指すようにします。*try‑with‑resources* ブロックにより、Parser は自動的にクローズされます。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **プロのコツ:** `FileNotFoundException` を回避するため、絶対パスを使用するかリソースフォルダーを設定してください。

### 手順 2: プレビューオプションの準備
各ページの保存方法を定義します。`ICreatePageStream` の実装は、各ワークシートページごとに新しい `FileOutputStream` を返します。

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

> このステップが **xlsx を png に変換** する箇所です。ストリームは PNG データをディスクに書き込みます。

### 手順 3: レンダリング情報取得用デリゲートのアタッチ
各レンダリングシートの詳細（例: サイズ、シート名）が必要な場合は、コールバックを登録します。

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### 手順 4: 出力フォーマットと DPI の指定
画像フォーマットに PNG を選択し、品質とファイルサイズのバランスを取る DPI を設定します。

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> サムネイルを小さくしたい場合（例: 96）や高解像度印刷が必要な場合（例: 300）には DPI を調整してください。

### 手順 5: プレビューの生成
すべて設定したら `generatePreview` を呼び出します。SDK は各ワークシートを順に処理し、提供したストリームを呼び出します。

```java
parser.generatePreview(previewOptions);
```

### 手順 6: `getOutputPath()` ヘルパーの定義
このメソッドはページ（シート）番号に基づいてファイル名を作成します。フォルダー構成は自由にカスタマイズしてください。

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **一般的な落とし穴:** 事前に `output` ディレクトリを作成していないと `IOException` が発生します。プログラムで作成するか、事前に存在することを確認してください。

## 完全動作サンプル（簡易版）

以下は、すべての要素を結合したコンパクトなバージョンです。**Excel ページプレビューの作成** ワークフローを最初から最後まで示しています。

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

このスニペットを実行すると、`output` フォルダーに `preview_page_1.png`、`preview_page_2.png` … といったファイルが生成されます。各ファイルは元の Excel ワークブックのシートを表しています。

## よくある問題と解決策

| Issue | Cause | Fix |
|-------|-------|-----|
| **画像が生成されない** | `getOutputPath` が無効なディレクトリを返す | 対象フォルダーが存在することを確認するか、`new File("output").mkdirs();` で作成してください。 |
| **巨大ファイルでのメモリ不足エラー** | ワークブック全体を一度にロードしている | ストリーミング方式（上記参照）を使用し、ページを1つずつ処理してください。 |
| **DPI が正しくない** | `setDpi` が呼び出されていない、またはデフォルト（96）のまま | `generatePreview` の前に `previewOptions.setDpi(yourDesiredValue);` を呼び出してください。 |
| **サポートされていないフォーマット** | 破損した `.xlsx` をプレビューしようとしている | Excel でファイルを検証するか、処理前に `Parser.isSupported` を使用してください。 |

## よくある質問

**Q: GroupDocs.Parser を使用して PDF や画像のプレビューを生成できますか？**  
A: はい、同じ API が PDF、Word 文書、その他多数の画像フォーマットでも利用可能です。

**Q: 出力画像フォーマットを変更するには？**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`（または `Gif`, `Bmp` など）を呼び出してください。

**Q: 非常に大きなワークブックでパフォーマンスは問題になりますか？**  
A: SDK はページをストリーム処理するため、メモリ使用量が低く抑えられます。極めて大きなファイルの場合は、並列バッチ処理を検討してください。

**Q: プレビュー生成中のエラーはどう処理すればよいですか？**  
A: コードを try‑catch ブロックで囲み（上記参照）、例外詳細をログに記録してください。try‑with‑resources を使用しない場合は、`finally` ブロックでストリームを閉じることを忘れないでください。

**Q: ライブラリは Microsoft Office のインストールが必要ですか？**  
A: いいえ。GroupDocs.Parser は純粋な Java ソリューションで、Java 8 以上をサポートする任意のプラットフォームで動作します。

## 結論
これで、GroupDocs.Parser を使用した **Excel のプレビュー方法** と **xlsx を png に変換** の完全な本番対応手法が手に入りました。プロジェクトの要件に合わせて DPI、出力フォルダー、画像フォーマットを調整し、このスニペットをより大規模なドキュメント管理ワークフローに組み込んでください。

次のステップへ進みますか？公式の [documentation](https://docs.groupdocs.com/parser/java/) で高度なレンダリングオプション、パスワード保護ファイル、バッチ処理手法を確認してください。

---

**最終更新日:** 2026-02-06  
**テスト環境:** GroupDocs.Parser 23.11 (latest at time of writing)  
**作者:** GroupDocs