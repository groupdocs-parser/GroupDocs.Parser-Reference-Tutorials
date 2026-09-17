---
date: '2026-09-17'
description: 了解如何在 Java 中使用 GroupDocs.Parser OCR 從 Java 圖像提取文字。本指南涵蓋環境設定、OCR 整合、程式碼範例，以及高效文件處理的實際案例。
keywords:
- java image to text
- how to ocr java
- use ocr java
- extract text areas java
lastmod: '2026-09-17'
og_description: 使用 GroupDocs.Parser OCR 從 Java 圖像提取文字。了解逐步設定、程式碼整合及在 Java 中實現高精度文字提取的效能技巧。
og_image_alt: Developer guide showing java image to text extraction with GroupDocs.Parser
  OCR
og_title: 使用 GroupDocs.Parser OCR 提取 Java 圖像文字
schemas:
- author: GroupDocs
  dateModified: '2026-09-17'
  description: Learn how to extract java image to text with GroupDocs.Parser OCR in
    Java. This guide covers setup, OCR integration, code snippets, and real‑world
    use cases for efficient document processing.
  headline: How to extract java image to text using GroupDocs.Parser OCR
  type: TechArticle
- questions:
  - answer: Add it as a Maven dependency (see the XML snippet above) or download the
      JAR from the official releases page.
    question: How do I install GroupDocs.Parser for Java?
  - answer: Aspose OCR is a high‑accuracy text recognition engine. Paired with GroupDocs.Parser,
      it extends the parser’s capabilities to handle image‑only files and provide
      precise text positions.
    question: What is Aspose OCR, and why use it with GroupDocs.Parser?
  - answer: Yes. GroupDocs.Parser supports JPEG, PNG, BMP, TIFF, and more—just ensure
      the OCR connector can read the format.
    question: Can I process multiple image formats?
  - answer: Check the file path, confirm the OCR connector is licensed, and verify
      that the document type is supported by Aspose OCR.
    question: What should I do if no text areas are extracted?
  - answer: Visit [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Parser?
  type: FAQPage
tags:
- java image to text
- GroupDocs.Parser
- OCR Java
- document processing
- text extraction
title: 如何使用 GroupDocs.Parser OCR 從 Java 圖像提取文字
type: docs
url: /zh-hant/java/ocr-integration/ocr-text-extraction-groupdocs-parser-java/
weight: 1
---

# 如何使用 GroupDocs.Parser OCR 提取 java 圖像文字

在本教學中，您將了解如何透過將 OCR 與 GroupDocs.Parser 函式庫結合，**提取 java 圖像文字**。您將看到如何設定 Aspose OCR 連接器、取得精確的文字座標，並將結果應用於實務情境，例如發票處理、可搜尋的檔案庫以及 UI 疊加。

## 快速解答
- **「java image to text」是什麼意思？** 它是將圖像檔案轉換為可搜尋、可編輯的文字，使用 Java 應用程式中的 OCR。  
- **哪個函式庫提供 Java 的 OCR？** GroupDocs.Parser 結合 Aspose OCR 連接器。  
- **我需要授權嗎？** 免費試用可用於評估；正式環境需購買永久授權。  
- **我可以取得文字座標嗎？** 可以——API 會回傳每個辨識字詞的邊界矩形（左、上、寬、高）。  
- **需要哪個 Java 版本？** 建議使用 Java 8 或更新版本，以確保完整相容性。

## 什麼是 OCR 文字擷取？
OCR（光學字符辨識）將掃描圖像、PDF 或相片中出現的視覺文字轉換為機器可讀的字元。當您 **提取 java 圖像文字** 時，您的應用程式即可對先前僅為靜態圖像的文件進行索引、編輯與分析。此功能可實現全文搜尋、資料探勘與自動化工作流程，將僅有圖片的檔案轉化為可供下游系統使用的可操作資訊。

## 為什麼選擇 GroupDocs.Parser 進行 OCR？
GroupDocs.Parser 提供單一且統一的 API，簡化多種文件類型的處理，同時提供高精度的 OCR 結果。透過整合 Aspose OCR 引擎，它支援數十種語言與複雜字型，回傳精確的位置資料，且能有效擴展以應付批次處理。這些特性使其成為企業級文件數位化專案的理想選擇。

- **統一 API** – 單一程式碼基礎即可處理 PDF、圖像及超過 30 種其他格式。  
- **精確辨識** – Aspose OCR 支援 60 多種語言與複雜字型。  
- **位置資料** – 回傳每個文字區塊的精確座標，支援版面感知的處理。  
- **可擴充效能** – 每次作業可處理最多 500 頁，同時使用低於 200 MB 的記憶體。

## 前置條件

- **GroupDocs.Parser for Java** – 版本 25.5 或更新（支援 30 多種輸入與輸出格式）。  
- **Maven** 或手動下載方式以安裝函式庫。  
- **Aspose OCR connector** – 必須用於啟用僅圖像文字辨識。  
- 使用 **Java 8+** 的 IDE，例如 IntelliJ IDEA 或 Eclipse。  
- 具備基本的 Java 程式設計知識與相依管理經驗。

## 設定 GroupDocs.Parser for Java

### 使用 Maven
在您的 `pom.xml` 檔案中加入以下相依性：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-parser</artifactId>
    <version>25.5</version>
</dependency>
```

> **定義：** `pom.xml` 是 Maven 專案描述檔，列出所有必需的函式庫及其版本。

### 直接下載
或者，從官方發行頁面下載最新的 JAR：

[GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)

> **定義：** 發行頁面提供預建的二進位檔與文件，以便立即整合。

#### 取得授權步驟
- **免費試用** – 無償評估函式庫。  
- **臨時授權** – 取得時間限制的金鑰以延長測試。  
- **購買** – 獲得完整授權，以無限制使用於正式環境。

### 基本初始化與設定
`ParserSettings` 設定 GroupDocs.Parser 讀取文件的方式，包括 OCR 選項與效能設定。  
`AsposeOcrOnPremise` 提供本地部署的 OCR 引擎與 Aspose OCR 的授權處理。

以下為建立帶有 Aspose OCR 連接器的 `ParserSettings` 實例的核心 Java 程式碼：

```java
ParserSettings settings = new ParserSettings();
settings.setOcrConnector(new AsposeOcrOnPremise("your-license-path"));
```

> **定義：** `ParserSettings` 設定 GroupDocs.Parser 讀取與處理文件的方式，而 `AsposeOcrOnPremise` 提供 OCR 引擎與授權。

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

基礎設定完成後，讓我們深入探討 OCR 文字區域的擷取。

## java 圖像文字擷取的運作原理
`Parser` 是核心類別，用於開啟文件並提供對其頁面與內容的存取。`PageTextAreaOptions` 指定擷取選項，例如啟用 OCR 與要求位置資料。使用 `Parser` 載入圖像，透過 `PageTextAreaOptions` 啟用 OCR，然後遍歷回傳的 `PageTextArea` 物件。此兩步驟模式在一次執行中同時回傳辨識字串及其邊界矩形，讓您能捕捉每個字詞的精確位置。

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.ParserSettings;
import com.groupdocs.parser.ocr.AsposeOcrOnPremise;

ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

## 如何使用 OCR 擷取文字區域（逐步說明）

本節將逐步說明設定 OCR、開啟文件、以及取得帶座標的文字區域的完整流程。依循這些步驟即可同時取得擷取的文字與版面資訊，供進階處理（如疊加渲染或資料抽取）使用。

### 1. 使用 OCR 連接器初始化 `ParserSettings`
OCR 連接器可啟用僅圖像文件的文字辨識。

```java
// Initialize ParserSettings with OCR Connector
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

### 2. 開啟文件並設定擷取選項
`PageTextAreaOptions` 告訴解析器回傳每個辨識字詞的位置資料。

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
    // Configure PageTextAreaOptions for OCR processing
    PageTextAreaOptions options = new PageTextAreaOptions(true);
    
    // Extract text areas from the document
    java.lang.Iterable<PageTextArea> areas = parser.getTextAreas(options);

    if (areas == null) {
        return; // Exit if text areas extraction is not supported
    }
    
    for (PageTextArea a : areas) {
        String text = a.getText();
        int leftPosition = a.getRectangle().getLeft();
        int topPosition = a.getRectangle().getTop();
        int width = a.getRectangle().getSize().getWidth();
        int height = a.getRectangle().getSize().getHeight();

        // Process the extracted data as needed
    }
} catch (java.lang.Exception ex) {
    // Handle any exceptions that occur during processing
}
```

#### 程式碼說明
- **建立** 指向您文件資料夾的 `Parser` 實例。  
- **啟用** 透過 `PageTextAreaOptions(true)` 的 OCR。  
- **遍歷** 每個 `PageTextArea`，為您提供辨識文字 **以及** 其精確的矩形（位置與大小）。  
- **允許** 您儲存或操作這些資料，例如寫入資料庫或在 UI 上疊加顯示。

`PageTextArea` 代表一個已辨識的文字區塊及其邊界矩形，讓您輕鬆將文字映射回原始圖像。

### 3. 處理結果
現在您可以將擷取的文字與座標用於各種情境：

- **文件數位化** – 將掃描的合約轉換為可搜尋的 PDF。  
- **資料錄入自動化** – 從收據圖像直接抽取發票號碼等欄位。  
- **內容管理** – 為進階搜尋高亮建立文字位置索引。

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|------|----------|----------|
| 未返回文字區域 | OCR 連接器未設定或圖像路徑不正確 | 確認 `AsposeOcrOnPremise` 實例已正確授權，且檔案路徑可存取。 |
| 文字亂碼 | 解析度低的圖像或不支援的語言 | 使用較高解析度的掃描，並設定 OCR 語言套件。 |
| 大型 PDF 記憶體不足錯誤 | 一次處理大量高解析度頁面 | 分批處理頁面，或啟用串流模式（`ParserSettings.setEnableStreaming(true)`）。 |

## 常見問答

**Q: 如何安裝 GroupDocs.Parser for Java？**  
A: 將其加入 Maven 相依性（請參考上方的 XML 片段），或從官方發行頁面下載 JAR。

**Q: 什麼是 Aspose OCR，為什麼要與 GroupDocs.Parser 搭配使用？**  
A: Aspose OCR 是高精度的文字辨識引擎。與 GroupDocs.Parser 結合後，可擴充解析器的功能，以處理僅圖像檔案並提供精確的文字位置。

**Q: 我可以處理多種圖像格式嗎？**  
A: 可以。GroupDocs.Parser 支援 JPEG、PNG、BMP、TIFF 等多種格式——只要確保 OCR 連接器能讀取該格式。

**Q: 若未擷取到文字區域該怎麼辦？**  
A: 檢查檔案路徑，確認 OCR 連接器已取得授權，並驗證文件類型是否受 Aspose OCR 支援。

**Q: 我可以在哪裡找到更多關於 GroupDocs.Parser 的資源？**  
A: 前往 [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) 瀏覽詳細指南與 API 參考。

## 其他技巧與最佳實踐

- **批次處理**：將擷取迴圈包在 `try‑with‑resources` 區塊中，以自動釋放檔案句柄。  
- **效能調校**：啟用 `ParserSettings.setEnableParallelProcessing(true)`，以在大型批次中利用多核心 CPU。  
- **語言設定**：呼叫 `AsposeOcrOnPremise.setLanguage("eng+spa")`，同時辨識英文與西班牙文。  
- **結果儲存**：將 `PageTextArea` 物件序列化為 JSON，方便下游使用。

## 資源

- [GroupDocs.Parser for Java 版本發佈](https://releases.groupdocs.com/parser/java/)  
- [下載最新版本](https://releases.groupdocs.com/parser/java/)  
- [文件](https://docs.groupdocs.com/parser/java/)  
- [API 參考](https://reference.groupdocs.com/parser/java)  
- [GitHub 儲存庫](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- [免費支援論壇](https://forum.groupdocs.com/c/parser)  
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)  

## 結論
您現在已掌握使用 GroupDocs.Parser 與 Aspose OCR 連接器進行 **java 圖像文字** 擷取的完整、可投入生產的方案。可將這些技術應用於數位化舊有文件、自動化資料錄入，或以最小的工作量建立可搜尋的檔案庫。

---

**最後更新：** 2026-09-17  
**測試環境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs

## 相關教學

- [Ocr 文字擷取 Java Groupdocs Parser](/parser/java/ocr-integration/ocr-text-extraction-java-groupdocs-parser/)
- [處理掃描文件：在 Java 中使用 Aspose OCR 文字擷取與 GroupDocs.Parser](/parser/java/ocr-integration/aspose-ocr-text-extraction-groupdocs-parser-java/)
- [Java OCR 文字辨識 Aspose Groupdocs Parser 指南](/parser/java/ocr-integration/java-ocr-text-recognition-aspose-groupdocs-parser-guide/)