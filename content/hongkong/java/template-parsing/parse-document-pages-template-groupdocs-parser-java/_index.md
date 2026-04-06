---
date: '2026-02-11'
description: 學習如何透過範本解析 PDF 頁面、從 PDF 中提取條碼，以及使用 GroupDocs.Parser for Java 在 Java 中提取
  QR 碼。
keywords:
- GroupDocs.Parser for Java
- parse document pages by template
- extract barcode data from PDF
title: 如何使用 GroupDocs.Parser for Java 透過模板解析 PDF 文件頁面
type: docs
url: /zh-hant/java/template-parsing/parse-document-pages-template-groupdocs-parser-java/
weight: 1
---

" Not relevant.

Now produce final content.# 如何使用 GroupDocs.Parser for Java 依模板解析 PDF 文件頁面

在當今的數位環境中，**如何解析 PDF** 檔案是開發人員常見的挑戰。無論您需要擷取 QR code、讀取條碼，或是從表單中讀取結構化欄位，可靠的解析解決方案都能節省大量時間。本指南將示範如何使用 **GroupDocs.Parser for Java** 依模板解析 **PDF** 頁面，重點在於從 PDF 文件中提取條碼資料。

## 快速回答
- **哪個函式庫可協助您依模板解析 PDF？** GroupDocs.Parser for Java.  
- **示範的條碼類型為何？** QR code（可更換為其他類型）。  
- **我需要授權嗎？** 免費試用可用於測試；正式環境需購買永久授權。  
- **可以使用 Maven 執行嗎？** 可以，只需將儲存庫與相依性加入您的 `pom.xml`。  
- **需要哪個 Java 版本？** JDK 8 或更高版本。

## 先決條件
在開始之前，請確保您已具備以下條件：

- **Java Development Kit (JDK)** 8+ 已安裝。  
- **Maven** 用於相依性管理（非必須，但建議使用）。  
- 具備基本的 Java 程式概念。

### 所需函式庫與相依性
若要在專案中使用 GroupDocs.Parser，請加入以下 Maven 設定：

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

或者，您也可以直接從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新版本。

### 取得授權
您可以從官方網站下載 GroupDocs.Parser 的免費試用版。若需長期使用，請考慮取得臨時授權或透過 [此連結](https://purchase.groupdocs.com/temporary-license/) 購買正式授權。

## 設定 GroupDocs.Parser for Java
若要使用 Maven 將 GroupDocs.Parser 整合至您的專案：

1. **新增儲存庫與相依性** – 將上述 XML 片段複製到您的 `pom.xml`。  
2. **匯入所需類別** – 如 `Parser`、`Template`、`DocumentPageData` 等類別位於 `com.groupdocs.parser` 套件中。  
3. **初始化 Parser** – 建立 `Parser` 實例，並指向您要處理的 PDF。

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.DocumentPageData;
import com.groupdocs.parser.templates.Template;
import com.groupdocs.parser.templates.TemplateBarcode;
import com.groupdocs.parser.templates.Rectangle;
import com.groupdocs.parser.templates.Point;
import com.groupdocs.parser.templates.Size;

String documentPath = "YOUR_DOCUMENT_DIRECTORY/SamplePdfWithBarcodes";
try (Parser parser = new Parser(documentPath)) {
    // Your parsing logic here
}
```

## 如何使用 GroupDocs.Parser 依模板解析 PDF
### 功能 1：定義條碼欄位（java 提取 QR code）
首先，我們描述每頁條碼的位置與大小。此步驟是 **依模板解析 PDF** 的核心，因為它告訴解析器精確的搜尋位置。

```java
TemplateBarcode barcode = new TemplateBarcode(
        new Rectangle(new Point(405, 55), new Size(100, 50)),
        "QR");
```

此處我們建立一個 `TemplateBarcode`，目標為位於座標 (405, 55) 且尺寸為 100 × 50 像素的 QR code。

### 功能 2：建立模板（java 讀取條碼 PDF）
接著，我們將條碼定義包裝於 `Template` 物件中。此模板可於文件的每一頁重複使用。

```java
Template template = new Template(Arrays.asList(new com.groupdocs.parser.templates.TemplateItem[]{barcode}));
```

### 功能 3：依模板解析文件頁面（從 PDF 提取條碼）
現在我們遍歷每一頁，套用模板，並收集條碼值。

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
        }
    }
}
```

迴圈會檢查識別出的區域是否為 `PageBarcodeArea`。若是，我們便取得條碼的字串值。

### 功能 4：列印提取的條碼資料（java 提取 QR code）
為了快速驗證，您可以將每個條碼值印至主控台：

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
            System.out.println(result);
        }
    }
}
```

執行此程式碼片段將輸出每個提取的條碼（或 QR code）值，讓您確認 **如何解析 PDF** 如預期般運作。

## 為何使用 GroupDocs.Parser for Java 依模板解析 PDF？
- **精確度** – 模板允許您鎖定精確座標，消除誤判。  
- **效能** – 解析以逐頁方式進行，即使是大型 PDF 亦能保持低記憶體使用。  
- **彈性** – 支援多種條碼類型（QR、Code128、DataMatrix 等），亦可擴充至其他欄位類型。  
- **跨平台** – 可於任何執行 Java 8+ 的平台上運作，適合伺服器端處理。

## 常見問題與解決方案
| 症狀 | 可能原因 | 解決方法 |
|------|----------|----------|
| 未返回條碼值 | 模板座標與實際條碼位置不符 | 使用 PDF 檢視器的測量工具驗證 X/Y 座標與尺寸。 |
| `Parser` 拋出 `FileNotFoundException` | `documentPath` 不正確或缺少讀取權限 | 確保路徑為絕對或相對於專案根目錄，且檔案可讀取。 |
| 掃描 PDF 的偵測精度低 | 影像解析度對條碼掃描器而言過低 | 使用較高解析度的掃描（300 dpi 以上）或以銳化濾鏡預處理 PDF。 |
| 大型 PDF 發生記憶體不足錯誤 | Parser 在記憶體中保留過多頁面 | 將 PDF 分批處理或增大 JVM 堆大小（`-Xmx2g`）。 |

## 實務應用
1. **庫存管理** – 自動從供應商 PDF 讀取條碼，以更新庫存資料庫。  
2. **法律文件驗證** – 提取內嵌數位簽章的 QR code，以作審計追蹤。  
3. **資料遷移** – 在舊系統之間搬移記錄時，以條碼作為唯一識別碼。  

## 效能考量
- **及時關閉 Parser** – `try‑with‑resources` 區塊確保檔案句柄被釋放。  
- **監控記憶體** – 大型 PDF 可能佔用大量堆積，建議使用串流或分塊處理。  

## 結論
現在您已擁有一套完整、可投入生產環境的 **如何解析 PDF** 依模板的操作指南，使用 GroupDocs.Parser for Java。透過定義條碼模板、遍歷頁面並提取值，您可以自動化幾乎所有條碼驅動的工作流程。

### 下一步
- 嘗試其他條碼類型（例如 Code128、DataMatrix），只需變更 `TemplateBarcode` 的第二個參數。  
- 結合多個 `TemplateBarcode` 物件，以處理單頁上混合的條碼版面。  
- 透過探索 [GroupDocs.Parser 文件](https://docs.groupdocs.com/parser/java/) 進一步了解文字提取、影像提取與自訂模板的建立。  

## 常見問答
**Q: 我可以從掃描文件中解析條碼嗎？**  
A: 可以，只要它們是 PDF 格式。請確保解析度足夠高，以準確偵測條碼。

**Q: 如何在單一頁面處理多種條碼類型？**  
A: 定義額外的 `TemplateBarcode` 實例，並設定各自的座標與尺寸。

**Q: 如果我的文件是影像而非 PDF 該怎麼辦？**  
A: GroupDocs.Parser 主要支援文字型文件。建議先將影像轉換為可搜尋的 PDF。

**Q: 能否從加密的 PDF 中提取資料？**  
A: 可能需要先使用其他函式庫解密 PDF，然後再進行解析。

---

**最後更新：** 2026-02-11  
**測試環境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs