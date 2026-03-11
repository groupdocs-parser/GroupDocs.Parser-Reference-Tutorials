---
date: '2026-02-09'
description: 學習如何在 Java 中使用 GroupDocs.Parser 的 OCR 從圖像和文件中提取文字。本指南涵蓋設定、Java 圖像轉文字的轉換，以及高效文件處理的實用案例。
keywords:
- OCR Text Extraction
- GroupDocs.Parser Java
- Java OCR Integration
title: 如何使用 GroupDocs.Parser Java 進行 OCR：從圖像和文件中提取文字
type: docs
url: /zh-hant/java/ocr-integration/ocr-text-extraction-groupdocs-parser-java/
weight: 1
---

# 如何在 GroupDocs.Parser Java 中使用 OCR

您是否希望有效地從圖像或掃描文件中提取文字？使用 GroupDocs.Parser Java 函式庫的 **如何使用 OCR** 提供了強大的解決方案，讓您能在應用程式中無縫整合光學字符辨識（OCR）。本完整指南將帶您了解如何使用 Aspose OCR 連接器與 GroupDocs.Parser 在 Java 中從圖像檔案提取文字區域，提升文件處理能力。

**您將學到的內容**
- 設定與使用 GroupDocs.Parser for Java。
- 使用 OCR 連接器初始化 `ParserSettings`。
- 使用 Aspose OCR 技術從圖像提取文字區域的技巧。
- 此功能在實際情境中的應用，例如 **java image to text** 轉換以及在 Java 中提取文字位置。

## 快速解答
- **「how to use OCR」是什麼意思？** 它指的是整合 OCR 引擎以讀取基於圖像的檔案中的文字。  
- **哪個函式庫提供 Java 的 OCR？** GroupDocs.Parser 結合 Aspose OCR 連接器。  
- **我需要授權嗎？** 提供免費試用；正式環境需購買永久授權。  
- **我可以取得文字座標嗎？** 可以，API 會回傳文字區域的位置（左、上、寬、高）。  
- **需要哪個 Java 版本？** 建議使用 Java 8 或更新版本。

## 什麼是 OCR 文字提取？
光學字符辨識（OCR）將視覺文字（如掃描圖像、PDF 或相片中的文字）轉換為機器可讀的字元。當您在 Java 中 **如何使用 OCR** 時，便能讓應用程式搜尋、編輯與分析先前靜態的文件。

## 為什麼選擇 GroupDocs.Parser 進行 OCR？
- **統一的 API** – 以單一程式碼基礎處理 PDF、圖像及其他多種格式。  
- **精確的辨識** – 由 Aspose OCR 提供支援，支援多種語言與字型。  
- **位置資料** – 取得每個文字區塊的精確座標，適合版面感知的處理。  
- **可擴充** – 可處理小型圖像或大型批次工作，且可在本地或雲端執行。

## 前置條件

在開始之前，請確保您已具備以下條件：

### 必要的函式庫與相依性
- **GroupDocs.Parser for Java**：版本 25.5 或更新。  
- **Maven** 或直接下載方式以安裝函式庫。  
- **Aspose OCR Connector**：需要存取 Aspose 的 OCR 技術。

### 環境設定需求
- 相容的 IDE（IntelliJ IDEA、Eclipse 等），執行於 Java 8+ 環境。  
- 若偏好使用 Maven 套件庫，請先安裝 Maven。

### 知識前提
- 基本的 Java 程式設計技能。  
- 熟悉專案相依性管理。

## 設定 GroupDocs.Parser for Java

您可以透過 Maven 加入函式庫，或直接下載。

### 使用 Maven
在您的 `pom.xml` 檔案中加入以下設定：

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
或者，從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新版本。

#### 取得授權步驟
- **免費試用** – 無償評估此函式庫。  
- **暫時授權** – 使用限時金鑰以延長測試。  
- **購買** – 取得正式授權以供生產環境部署。

### 基本初始化與設定

函式庫可用後，您即可初始化解析器。以下是建立帶有 Aspose OCR 連接器的 `ParserSettings` 實例的核心 Java 程式碼：

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.ParserSettings;
import com.groupdocs.parser.ocr.AsposeOcrOnPremise;

ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

基礎設定完成後，讓我們深入探討 OCR 文字區域的提取。

## 如何使用 OCR 提取文字區域（逐步說明）

### 1. 使用 OCR 連接器初始化 `ParserSettings`
OCR 連接器可辨識僅含圖像的文件中的文字。

```java
// Initialize ParserSettings with OCR Connector
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

### 2. 開啟文件並設定提取選項
我們使用 `PageTextAreaOptions` 讓解析器回傳每個辨識字詞的位置資料。

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
- **啟用** 透過 `PageTextAreaOptions(true)` 的 OCR 功能。  
- **遍歷** 每個 `PageTextArea`，取得辨識文字 **以及** 其精確矩形（位置與尺寸）。  
- **允許** 您儲存或操作這些資料，例如寫入資料庫或在 UI 上疊加顯示。

### 3. 處理結果
您現在可以將提取的文字與座標應用於各種情境：

- **文件數位化** – 將掃描合約轉換為可搜尋的 PDF。  
- **資料輸入自動化** – 從收據圖像直接提取發票號碼等欄位。  
- **內容管理** – 為進階搜尋高亮建立文字位置索引。

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| 未返回文字區域 | OCR 連接器未配置或圖像路徑不正確 | 確認 `AsposeOcrOnPremise` 實例已正確授權，且檔案路徑可存取。 |
| 文字亂碼 | 圖像品質低或語言不受支援 | 使用更高解析度的掃描，並設定 OCR 語言套件。 |
| 大型 PDF 記憶體不足錯誤 | 一次處理大量高解析度頁面 | 將頁面分批處理或啟用串流模式（`ParserSettings.setEnableStreaming(true)`）。 |

## 常見問答

**Q: 如何安裝 GroupDocs.Parser for Java？**  
A: 以 Maven 依賴方式加入（請參考上方的 XML 片段），或直接從官方發布頁面下載。

**Q: 什麼是 Aspose OCR，為何要與 GroupDocs.Parser 一起使用？**  
A: Aspose OCR 是高精度的文字辨識引擎。與 GroupDocs.Parser 結合後，可擴充解析器的功能，以處理僅含圖像的檔案並提供精確的文字位置。

**Q: 我可以處理多種圖像格式嗎？**  
A: 可以。GroupDocs.Parser 支援 JPEG、PNG、BMP、TIFF 等格式——只要確保 OCR 連接器能讀取該格式即可。

**Q: 若未提取到文字區域該怎麼辦？**  
A: 檢查檔案路徑，確認 OCR 連接器已取得授權，並驗證文件類型是否受 Aspose OCR 支援。

**Q: 我在哪裡可以找到更多關於 GroupDocs.Parser 的資源？**  
A: 前往 [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) 瀏覽詳細指南與 API 參考。

## 資源
- [文件說明](https://docs.groupdocs.com/parser/java/)
- [API 參考](https://reference.groupdocs.com/parser/java)
- [下載最新版本](https://releases.groupdocs.com/parser/java/)
- [GitHub 倉庫](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/parser)
- [暫時授權](https://purchase.groupdocs.com/temporary-license/) 

探索這些資源，以加深對 GroupDocs.Parser 的了解，並在您的專案中擴展其功能。

---

**最後更新：** 2026-02-09  
**測試環境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs