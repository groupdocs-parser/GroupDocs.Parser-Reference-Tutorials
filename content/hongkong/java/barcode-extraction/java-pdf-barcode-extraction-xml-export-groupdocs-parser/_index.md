---
date: '2026-10-12'
description: 了解如何在 Java 中使用 GroupDocs.Parser 從 PDF 中提取 QR，並將條碼資料匯出為 XML 以供下游處理。
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: 了解如何在 Java 中使用 GroupDocs.Parser 從 PDF 中提取 QR，並將條碼資料匯出為 XML 以供下游處理。
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: 如何在 Java 中使用 GroupDocs.Parser 從 PDF 中提取 QR 並匯出條碼資料為 XML 以供後續處理
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
title: 如何在 Java 中使用 GroupDocs.Parser 從 PDF 中提取 QR 並匯出條碼資料為 XML 以供後續處理
type: docs
url: /zh-hant/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Parser 從 PDF 提取 QR

在現代商業工作流程中，**extracting QR from PDF** 檔案可以將手動資料輸入的瓶頸轉變為全自動化的管線。無論您在處理出貨清單、零售收據或產品目錄，快速且可靠地取得 QR 資訊對下游系統至關重要。本教學將帶您使用 **GroupDocs.Parser for Java** 讀取 PDF 中的 QR 碼（以及其他條碼），並將結果匯出為乾淨的 XML 檔案，供您的 ERP、庫存或分析平台使用。

## 快速解答
- **GroupDocs.Parser for Java 的功能是什麼？** 它會讀取 PDF 檔案並提取結構化資料，例如條碼、表格和文字。  
- **如何提取 QR 碼？** 設定 `BarcodeOptions` 為 QR 類型，然後呼叫 `parser.getBarcodes()`。  
- **我可以在 Java 中讀取 QR 碼嗎？** 可以——在選項中將條碼類型設為 `"QR"`。  
- **需要授權嗎？** 試用版可用於測試；正式環境需要商業授權。  
- **需要哪個 Java 版本？** 建議使用 Java 8 或以上。

## 在 PDF 處理的情境下，「從 PDF 提取 QR」是什麼？
從 PDF 提取 QR 意指掃描每一頁的 QR 編碼圖形，解碼內嵌資料，並以程式友善的格式返回。GroupDocs.Parser 抽象化了低階影像分析，讓您專注於業務邏輯，而非像素操作。

## 為什麼使用 GroupDocs.Parser 進行 QR 提取？
GroupDocs.Parser 支援 **超過 30 種輸入格式**，且可在不將整個檔案載入記憶體的情況下處理高達 **500 MB** 的 PDF，於低解析度掃描下仍能提供高精度結果。您可以選擇 `QualityMode.Low` 以提升速度，或 `QualityMode.High` 以獲得最高精度，同一套 API 同時支援 PDF、影像與 Office 文件，免除使用多個函式庫的需求。

## 前置條件
- **GroupDocs.Parser for Java**（版本 25.5 或更新）。  
- Maven 或手動下載 JAR。  
- Java 8+ 開發環境（IntelliJ IDEA、Eclipse 或任何編輯器）。

## 設定 GroupDocs.Parser for Java
### 使用 Maven
將 GroupDocs 儲存庫和相依性加入您的 `pom.xml`：

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

### 直接下載
或者，從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新的 JAR。

#### 取得授權步驟
- **免費試用：** 30 天完整功能試用。  
- **臨時授權：** 申請臨時金鑰以延長評估。  
- **購買：** 取得商業授權以供正式部署。

### 基本初始化與設定
建立指向您要分析之 PDF 的 `Parser` 實例：

`Parser` 是 GroupDocs.Parser 的核心類別，代表文件並提供提取文字、表格與條碼等內容的方法。

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

## 如何在 Java PDF 中使用 GroupDocs.Parser 讀取 QR 碼
閱讀 Java PDF 中的 QR 碼需要建立 parser 實例、設定條碼選項以鎖定 QR 類型、呼叫條碼提取方法，然後處理返回的條碼物件。此流程簡單直接，適用於任何 PDF 頁面，並返回解碼值與位置中繼資料以供後續處理。

### 步驟 1：驗證條碼支援
在嘗試提取之前，先確認文件格式支援條碼掃描：

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*說明：* 此檢查可防止在不支援的檔案類型上發生執行時錯誤。

### 步驟 2：設定條碼選項（讀取 QR 碼 Java）
`BarcodeOptions` 是一個設定物件，可讓您指定要偵測的條碼符號、設定掃描品質模式，並微調偵測門檻等參數，以確保對目標 QR 碼的最佳效能。

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*說明：* `QualityMode.Low` 可加速處理；若需要更高精度可切換至 `High`。`"QR"` 參數指示引擎僅搜尋 QR 類型條碼。

### 步驟 3：提取 QR 資料
`parser.getBarcodes(options)` 會使用提供的 `BarcodeOptions` 掃描文件，並回傳 `PageBarcodeArea` 物件集合，每個物件封裝了解碼的 QR 值、頁碼以及條碼在頁面上的精確座標，方便精確的下游處理。

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*說明：* `parser.getBarcodes` 會回傳 `PageBarcodeArea` 物件的可疊代集合，每個物件包含已解碼的 QR 值及其在頁面上的位置。

## 匯出提取資料為 XML
### 步驟 4：初始化 XML 匯出器
`XmlExporter` 是一個工具類別，可將條碼物件集合轉換為結構良好的 XML 文件，會自動為每個條碼產生元素，並加入頁索引、位置與解碼值等屬性，之後即可儲存或串流至其他系統。

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*說明：* `XmlExporter` 處理條碼物件序列化為標準 XML，方便與 ERP 或庫存系統整合。

### 步驟 5：寫入 XML 檔案
將提取的 QR 資訊儲存至磁碟：

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*說明：* 產生的 `data.xml` 為每個 QR 碼包含一個 `<Barcode>` 元素，屬性包括頁碼、座標與解碼值。

## 實務應用
1. **庫存管理：** 透過讀取進貨 PDF 上的 QR 標籤，自動填入庫存資料庫。  
2. **供應鏈可視化：** 透過提取物流文件中嵌入的 QR 識別碼，即時追蹤包裹。  
3. **零售收據：** 從數位收據上印刷的 QR 碼提取促銷或保固資訊。

## 效能考量
- **記憶體管理：** 對於非常大的 PDF，請以串流方式處理頁面，而非一次載入整個檔案。  
- **QualityMode 選擇：** 大量處理時使用 `Low`，處理低解析度掃描時切換至 `High`。  
- **函式庫更新：** 保持 GroupDocs.Parser 為最新版本，以獲得最新的效能提升與錯誤修正。

## 常見問題與故障排除
| 症狀 | 可能原因 | 解決方案 |
|------|----------|----------|
| 未返回條碼 | 條碼類型指定錯誤 | 將 `"QR"` 改為適當的類型（例如 `"CODE_128"`）。 |
| 大型 PDF 發生記憶體不足錯誤 | 一次載入整個文件 | 逐頁處理或增加 JVM 堆積大小（`-Xmx2g`）。 |
| XML 檔案為空 | `exportBarcodes` 在提取之前被呼叫 | 確保在匯出前 `parser.getBarcodes(options)` 已返回資料。 |

## 常見問答
**Q: 我可以使用 GroupDocs.Parser 從影像檔案提取條碼嗎？**  
A: 可以，函式庫支援從常見影像格式（PNG、JPEG、TIFF）提取條碼。

**Q: 支援哪些條碼格式？**  
A: QR、Code 39、Code 128、DataMatrix、PDF417 等等。完整清單請參考 API 文件。

**Q: 如何處理受密碼保護的 PDF？**  
A: 在 `Parser` 建構子中傳入密碼，例如 `new Parser(filePath, "password")`。

**Q: 試用版足以進行正式測試嗎？**  
A: 試用版提供完整功能，但會在提取的資料上加上浮水印。正式環境建議取得商業授權。

**Q: 若 PDF 同時包含 QR 與線性條碼該怎麼辦？**  
A: 建立多個 `BarcodeOptions` 實例，或傳入類型陣列，以一次掃描所有需要的格式。

---

**最後更新：** 2026-10-12  
**測試環境：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

## 資源
- [GroupDocs.Parser Java 文件說明](https://docs.groupdocs.com/parser/java/)
- [API 參考](httpshttps://reference.groupdocs.com/parser/java)
- [下載 GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub 程式庫](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/parser)
- [臨時授權申請](https://purchase.groupdocs.com/temporary-license/)

## 相關教學
- [提取條碼 PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [如何使用 GroupDocs.Parser for Java 從 URL 載入 PDF](/parser/java/document-loading/)
- [使用 GroupDocs.Parser in Java 提取 PDF 表單資料](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)