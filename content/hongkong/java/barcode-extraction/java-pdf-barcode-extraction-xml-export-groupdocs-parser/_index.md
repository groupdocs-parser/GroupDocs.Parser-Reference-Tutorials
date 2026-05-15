---
date: '2026-02-19'
description: 學習如何在 Java PDF 中使用 GroupDocs.Parser 讀取 QR 碼，並將條碼資料匯出為 XML。
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: 如何使用 GroupDocs.Parser 在 Java PDF 中讀取 QR 碼
type: docs
url: /zh-hant/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# 如何在 Java PDF 中使用 GroupDocs.Parser 讀取 QR 碼

在現代商業工作流程中，從 PDF 文件 **讀取 QR** 碼的方式可能決定是手動資料輸入的瓶頸，還是全自動化的流程。無論您在處理出貨清單、零售收據或產品目錄，快速且可靠地擷取 QR 資訊都是必須的。本教學將逐步說明如何使用 **GroupDocs.Parser for Java** 從 PDF 中讀取 QR 碼（以及其他條碼），並將結果匯出為乾淨的 XML 檔案，供下游系統使用。

## Quick Answers
- **GroupDocs.Parser for Java 的功能是什麼？** 它會讀取 PDF 檔案並擷取結構化資料，例如條碼。  
- **如何擷取 QR 碼？** 只要在 `BarcodeOptions` 中設定 QR 類型，並呼叫 `parser.getBarcodes()` 即可。  
- **我可以在 Java 中讀取 QR 碼嗎？** 可以——在選項中將條碼類型設為 `"QR"`。  
- **需要授權嗎？** 試用版可用於測試；正式上線則需商業授權。  
- **需要哪個 Java 版本？** 建議使用 Java 8 或以上。

## 在 PDF 處理的情境下，「讀取 QR」是什麼意思？
從 PDF 中讀取 QR 碼意味著掃描每一頁的 QR 圖形，解碼其中的資料，並以程式友善的格式回傳。GroupDocs.Parser 抽象化了低階的影像分析，讓您可以專注於業務邏輯，而不必處理像素層面的操作。

## 為什麼使用 GroupDocs.Parser 進行 QR 擷取？
- **高精度：** 內建的影像處理演算法能處理低解析度掃描。  
- **效能選項：** 可選擇 `QualityMode.Low` 以提升速度，或 `QualityMode.High` 以獲得最高精度。  
- **跨格式支援：** 支援 PDF、影像乃至 Office 文件，讓您可在不同檔案類型間重複使用相同程式碼基礎。

## 前置條件
- **GroupDocs.Parser for Java**（版本 25.5 或更新）。  
- Maven 或手動下載 JAR。  
- Java 8+ 開發環境（IntelliJ IDEA、Eclipse 或任何編輯器）。  

## 設定 GroupDocs.Parser for Java
### 使用 Maven
在 `pom.xml` 中加入 GroupDocs 的儲存庫與相依性：

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
- **臨時授權：** 申請臨時金鑰以延長評估時間。  
- **購買：** 取得商業授權以供正式部署使用。

### 基本初始化與設定
建立指向欲分析 PDF 的 `Parser` 實例：

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
### 步驟 1：驗證條碼支援
在嘗試擷取之前，先確認文件格式支援條碼掃描：

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*說明：* 此檢查可防止在不支援的檔案類型上產生執行時錯誤。

### 步驟 2：設定條碼選項（在 Java 中讀取 QR 碼）
設定掃描品質，並指定只關注 QR 碼：

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*說明：* `QualityMode.Low` 可加快處理速度；若需要更高精度則切換至 `High`。`"QR"` 參數告訴引擎僅搜尋 QR 類型的條碼。

### 步驟 3：擷取 QR 資料
從 PDF 的每一頁取得條碼資訊：

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*說明：* `parser.getBarcodes` 會回傳 `PageBarcodeArea` 物件的可疊代集合，每個物件包含已解碼的 QR 值以及其在頁面上的位置。

## 匯出擷取的資料為 XML
### 步驟 4：初始化 XML 匯出器
建立匯出器，將條碼集合轉換為結構良好的 XML 檔案：

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*說明：* `XmlExporter` 負責將條碼物件序列化為標準 XML，方便與 ERP 或庫存系統整合。

### 步驟 5：寫入 XML 檔案
將擷取的 QR 資訊儲存至磁碟：

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*說明：* 產生的 `data.xml` 為每個 QR 碼包含一個 `<Barcode>` 元素，並帶有頁碼、座標與解碼值等屬性。

## 實務應用
1. **庫存管理：** 透過讀取進貨 PDF 上的 QR 標籤，自動填入庫存資料庫。  
2. **供應鏈可視化：** 從物流文件中擷取 QR 識別碼，即時追蹤貨件。  
3. **零售收據：** 從數位收據上印刷的 QR 碼取得促銷或保固資訊。

## 效能考量
- **記憶體管理：** 對於非常大的 PDF，請以串流方式逐頁處理，而非一次載入整個檔案。  
- **QualityMode 選擇：** 大量處理時使用 `Low`，低解析度掃描時則切換至 `High`。  
- **函式庫更新：** 保持 GroupDocs.Parser 為最新版本，以獲得最新的效能提升與錯誤修正。

## 常見問題與除錯
| 症狀 | 可能原因 | 解決方案 |
|---------|--------------|-----|
| 未返回條碼 | 條碼類型設定錯誤 | 將 `"QR"` 改為適當的類型（例如 `"CODE_128"`）。 |
| 大型 PDF 發生記憶體不足錯誤 | 一次載入整個文件 | 改為逐頁處理或增加 JVM 堆積大小（`-Xmx2g`）。 |
| XML 檔案為空 | `exportBarcodes` 在擷取之前被呼叫 | 確保在匯出前 `parser.getBarcodes(options)` 已取得資料。 |

## 常見問答
**Q: 我可以使用 GroupDocs.Parser 從影像檔案擷取條碼嗎？**  
A: 可以，函式庫支援從常見影像格式（PNG、JPEG、TIFF）擷取條碼。

**Q: 支援哪些條碼格式？**  
A: QR、Code 39、Code 128、DataMatrix、PDF417 等等。完整清單請參考 API 文件。

**Q: 如何處理受密碼保護的 PDF？**  
A: 在 `Parser` 建構子中傳入密碼，例如 `new Parser(filePath, "password")`。

**Q: 試用版足以進行生產測試嗎？**  
A: 試用版提供完整功能，但會在擷取的資料上加上浮水印。正式環境請取得商業授權。

**Q: 若 PDF 同時包含 QR 與線性條碼該怎麼辦？**  
A: 建立多個 `BarcodeOptions` 實例，或傳入類型陣列，以一次掃描所有需要的格式。

---

**最後更新：** 2026-02-19  
**測試版本：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

## 資源
- [GroupDocs.Parser Java 文件](https://docs.groupdocs.com/parser/java/)
- [API 參考](https://reference.groupdocs.com/parser/java)
- [下載 GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub 程式庫](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/parser)
- [臨時授權申請](https://purchase.groupdocs.com/temporary-license/)