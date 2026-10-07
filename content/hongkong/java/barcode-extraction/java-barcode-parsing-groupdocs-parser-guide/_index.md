---
date: '2026-10-07'
description: 了解如何使用 GroupDocs.Parser 讀取 Java QR 代碼，這是一個強大的 Java 條碼識別函式庫，可從影像與文件中提取
  QR 代碼。
keywords:
- read qr code java
- java barcode recognition library
- java read qr code from image
lastmod: '2026-10-07'
og_description: 了解如何使用 GroupDocs.Parser 讀取 Java QR 代碼，這是一個強大的 Java 條碼識別函式庫，可從影像與文件中提取
  QR 代碼。快速設定、詳細指南與故障排除技巧。
og_image_alt: Guide to reading QR code in Java with GroupDocs.Parser
og_title: 如何使用 GroupDocs.Parser 高效讀取 Java QR 代碼
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to read QR code java using GroupDocs.Parser, a powerful java
    barcode recognition library that extracts QR codes from images and documents.
  headline: How to read QR code java efficiently with GroupDocs.Parser
  type: TechArticle
- description: Learn how to read QR code java using GroupDocs.Parser, a powerful java
    barcode recognition library that extracts QR codes from images and documents.
  name: How to read QR code java efficiently with GroupDocs.Parser
  steps:
  - name: define a barcode field
    text: The `BarcodeField` class describes the barcode’s location, size, and type.
      **Definition anchor:** `BarcodeField` is the object that tells the parser where
      to look for a barcode and which format to expect.
  - name: create a template
    text: A `Template` groups one or more `BarcodeField` objects so the parser knows
      exactly what to extract. **Definition anchor:** `Template` represents a collection
      of field definitions that the parser applies to a document.
  - name: parse the document using the parser
    text: 'Instantiate a `Parser` object that loads a document, applies templates,
      and returns extracted data. **Definition anchor:** `Parser` is the core class
      that loads a document, applies templates, and returns extracted data. The parser
      scans each page, matches the QR‑code region, and returns the decoded '
  - name: instantiate the parser
    text: Create a reusable `Parser` object that points to the folder containing your
      source files. Reusing the same instance across many files reduces object‑creation
      overhead by up to 40 %. Now you can loop through a directory, parse each document,
      and collect barcode values without re‑initialising the libr
  type: HowTo
- questions:
  - answer: Upgrade to the latest GroupDocs.Parser version, which lists all supported
      formats. If a format is still missing, convert the file to PDF or a supported
      image type before parsing.
    question: How do I handle unsupported document formats?
  - answer: Yes. GroupDocs.Parser extracts QR codes from PNG, JPEG, BMP, and TIFF
      files using the same `BarcodeField` definition you would use for PDFs.
    question: Can I parse barcodes from images as well?
  - answer: Mis‑aligned rectangles, selecting the wrong barcode type (e.g., “QR” vs.
      “CODE_128”), and forgetting to add the barcode field to the template’s item
      list.
    question: What are common pitfalls when defining a template?
  - answer: The library can handle dozens of barcodes per document; performance scales
      linearly with the number of pages and barcode density.
    question: Is there a limit to the number of barcodes I can parse at once?
  - answer: Post questions on the [GroupDocs Support Forum](https://forum.groupdocs.com/c/parser)
      or consult the official documentation for troubleshooting guides.
    question: Where can I get help if I run into issues?
  type: FAQPage
tags:
- read qr code
- java barcode parsing
- groupdocs parser
- java barcode recognition
- qr code extraction
title: 如何使用 GroupDocs.Parser 高效讀取 Java QR 代碼
type: docs
url: /zh-hant/java/barcode-extraction/java-barcode-parsing-groupdocs-parser-guide/
weight: 1
---

# 如何高效使用 GroupDocs.Parser 讀取 QR code java

在現代企業應用中，**read QR code java** 是自發票、運送清單與庫存表格中自動擷取資料的常見需求。透過 GroupDocs.Parser，您可以直接從 PDF、Word、試算表或純影像格式中提取 QR‑code 資料，無需自行撰寫底層影像處理程式碼。本教學將帶您完成安裝、範本建立、解析以及最佳實踐技巧，讓您能自信地將條碼擷取整合至任何 Java 專案。

## 快速解答
- **什麼函式庫可以讓我讀取 QR code java？** GroupDocs.Parser for Java。  
- **我需要授權嗎？** 免費試用可用於評估；正式環境需要完整授權。  
- **支援哪些文件類型？** PDF、DOCX、XLSX、PNG、JPEG、TIFF 等。  
- **我可以一次提取多個條碼嗎？** 可以——解析器能在每個文件中偵測並返回多個條碼。  
- **需要哪個 Java 版本？** Java 8 或以上。

## 什麼是 read qr code java？

Reading QR code java 指的是使用 GroupDocs.Parser Java 函式庫來定位並解碼嵌入於 PDF、影像或 Office 文件中的 QR 條碼。此函式庫抽象化底層影像處理，讓您只需呼叫少數方法即可取得編碼文字。此方式可免除手動掃描，降低自動化工作流程中的資料輸入錯誤。

## 為什麼使用 GroupDocs.Parser 進行條碼資料擷取？

GroupDocs.Parser 提供 **超過 30 種條碼格式的高精度辨識**，包括 QR、Data Matrix 與 Code‑128，並支援 **30+ 輸入與輸出文件類型**。其基於範本的引擎讓您精確定位條碼位置，將誤報率降低最高可達 95 %。API 完全執行緒安全，能在標準伺服器硬體上 **每小時處理數千檔案**，非常適合大規模 **parse QR code PDF** 的情境。

## 前置條件
- **Java Development Kit** 8 或更新版本，已安裝於工作站或建置伺服器。  
- **Maven** 用於相依管理（若偏好亦可使用 Gradle）。  
- **GroupDocs.Parser for Java** 版本 25.5 或更新（可於 Maven Central 取得）。  
- 具備 Java 專案結構與 IDE 設定的基本認識。

## 如何設定 GroupDocs.Parser for Java

要安裝 GroupDocs.Parser，只需將其 Maven 坐標加入專案的 `pom.xml`。儲存檔案後，Maven 會自動下載函式庫及其相依項目。請將 `{{VERSION}}` 替換為目前的發佈版本號，然後在 IDE 或命令列執行 Maven 重新整理以驗證設定。

將函式庫加入 Maven `pom.xml` 並重新整理專案。  
（將 `{{VERSION}}` 替換為最新版本號。）

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-parser</artifactId>
    <version>{{VERSION}}</version>
</dependency>
```

如果偏好手動下載，可從官方發佈頁面取得 JAR。

### 直接下載
您也可以從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新的 JAR。

#### 授權取得
- **免費試用** – 先使用試用版探索全部功能。  
- **臨時授權** – 申請短期金鑰以延長測試時間。  
- **完整授權** – 購買訂閱以獲得無限制的正式環境使用權。

## 如何定義與解析條碼範本

建立條碼範本的第一步是描述您想要提取的每個條碼。範本告訴解析器確切的區域、預期格式與任何縮放規則，從而在不同文件版面上都能可靠偵測。定義完成後，解析器即可在不需手動影像分析的情況下定位並解碼每個條碼。

### 步驟 1：定義條碼欄位

`BarcodeField` 類別描述條碼的位置、大小與類型。  
**定義說明：** `BarcodeField` 是告訴解析器要在哪裡尋找條碼以及預期格式的物件。

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

### 步驟 2：建立範本

`Template` 將一個或多個 `BarcodeField` 物件聚合，使解析器明確知道要提取什麼。  
**定義說明：** `Template` 代表一組欄位定義，解析器會將其套用於文件。

```java
// Define a barcode field with its position and type
TemplateBarcode barcode = new TemplateBarcode(
        new Rectangle(new Point(405, 55), new Size(100, 50)),
        "QR");
```

### 步驟 3：使用解析器解析文件

實例化 `Parser` 物件以載入文件、套用範本，並返回提取的資料。  
**定義說明：** `Parser` 是核心類別，負責載入文件、套用範本並回傳提取資料。

```java
// Create a template containing the barcode field
template = new Template(Arrays.asList(new TemplateItem[]{barcode}));
```

解析器會掃描每一頁，匹配 QR‑code 區域，並在一次呼叫中返回解碼後的字串。

## 如何建立與使用文件解析器實例

為了高效處理多個文件，請建立單一的 `Parser` 物件指向來源檔案目錄。此共享實例會維持內部資源，減少重複載入函式庫的成本。於批次作業中重複使用，可提升吞吐量並降低垃圾回收壓力。

`Parser` 類別是載入文件、套用範本並回傳條碼資料的核心元件。

### 步驟 1：實例化解析器

建立可重複使用的 `Parser` 物件，指向存放來源檔案的資料夾。於多檔案間重複使用同一實例，可將物件建立開銷降低至約 40 %。

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    DocumentData data = parser.parseByTemplate(template);

    // Iterate through extracted data and print barcode values
    for (int i = 0; i < data.getCount(); i++) {
        PageArea pageArea = data.get(i).getPageArea();
        if (pageArea instanceof PageBarcodeArea) {
            PageBarcodeArea area = (PageBarcodeArea) pageArea;
            System.out.println(data.get(i).getName() + ": " + area.getValue());
        } else {
            System.out.println(data.get(i).getName() + ": Not a template barcode field");
        }
    }
}
```

現在您可以遍歷目錄、解析每份文件，並收集條碼值，而無需每次重新初始化函式庫。

## 實務應用

1. **庫存管理** – 從運送 PDF 中提取產品編號，自動更新庫存。  
2. **零售會員計畫** – 讀取收據上的 QR code，將購買行為與顧客帳號連結。  
3. **供應鏈追蹤** – 提取海關文件條碼，即時監控貨物流向。

## 效能考量

- **重複使用解析器實例** 於批次作業以減少 GC 壓力。  
- **將範本矩形設定得更緊湊**；較小的搜尋區域可提升偵測速度 20‑30 %。  
- **使用 VisualVM 或 YourKit 進行記憶體分析**，處理多百頁 PDF 時避免記憶體洩漏。

## 常見問題與解決方案

| 問題 | 原因 | 解決方案 |
|------|------|----------|
| 未返回條碼值 | 矩形座標與實際條碼位置不符 | 使用 PDF 檢視器的測量工具驗證座標，並相應調整 `x`、`y`、`width`、`height` 值。 |
| `IOException` 檔案開啟時 | 檔案路徑不正確或無法存取 | 使用絕對路徑或確保應用程式對目錄具有讀取權限。 |
| 大型 PDF 處理緩慢 | 每頁建立新的 `Parser` | 在多頁間重複使用同一個 `Parser` 實例，或使用 Java 的 `ExecutorService` 並行處理檔案。 |
| 不支援的文件格式錯誤 | 使用較舊的函式庫版本 | 升級至最新的 GroupDocs.Parser 版本，該版本已支援更多格式。 |
| 輸出中出現意外字元 | QR code 使用 UTF‑8 編碼卻被當作 ASCII 讀取 | 在解讀返回字串時指定正確的字符集。 |

## 常見問答

**Q：如何處理不支援的文件格式？**  
A：升級至最新的 GroupDocs.Parser 版本，該版本列出所有支援的格式。若仍缺少某種格式，可先將檔案轉為 PDF 或支援的影像類型再進行解析。

**Q：我也可以從影像解析條碼嗎？**  
A：可以。GroupDocs.Parser 可從 PNG、JPEG、BMP 與 TIFF 檔案中提取 QR code，使用與 PDF 相同的 `BarcodeField` 定義即可。

**Q：定義範本時常見的陷阱是什麼？**  
A：矩形對齊不正確、選錯條碼類型（例如「QR」與「CODE_128」混淆），以及忘記將條碼欄位加入範本的項目清單。

**Q：一次可以解析的條碼數量有上限嗎？**  
A：函式庫可處理每份文件數十個條碼；效能會隨頁數與條碼密度線性伸縮。

**Q：如果遇到問題，我可以在哪裡取得協助？**  
A：可在 [GroupDocs Support Forum](https://forum.groupdocs.com/c/parser) 發問，或參考官方文件中的故障排除指南。

## 後續步驟

深入探索 **動態範本產生**、**多執行緒批次處理** 與 **自訂條碼類型擴充** 等進階功能，請參閱完整 API 參考。嘗試不同的矩形形狀（橢圓、 多邊形）以提升非標準版面上的偵測率，並將解析器整合至現有的文件處理管線，實現端到端自動化。

## 資源
- **文件**：完整指南請見 [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/)  
- **文件連結**：詳情請參閱 [documentation](https://docs.groupdocs.com/parser/java/)  
- **API 參考**：詳細規格請見 [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)  
- **下載**：從 [GroupDocs Downloads](https://releases.groupdocs.com/parser/java/) 取得最新發佈版。  
- **GitHub 倉庫**：在 [GroupDocs on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java) 瀏覽原始碼並貢獻。  
- **免費支援**：於 [GroupDocs Forum](https://forum.groupdocs.com/c/parser) 與社群互動。  
- **臨時授權**：在 [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license/) 取得試用金鑰。

---

**最後更新：** 2026-10-07  
**測試版本：** GroupDocs.Parser 25.5 (Java)  
**作者：** GroupDocs  

---

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
    System.out.println("Document parser created and ready to use.");
}
```

## 相關教學

- [檢查 Java 條碼支援 - GroupDocs.Parser 完整指南](/parser/java/barcode-extraction/java-barcode-support-check-groupdocs-parser/)
- [如何在 Java PDF 中讀取 QR Code - GroupDocs.Parser](/parser/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/)
- [Extract Barcode Pdf Groupdocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)