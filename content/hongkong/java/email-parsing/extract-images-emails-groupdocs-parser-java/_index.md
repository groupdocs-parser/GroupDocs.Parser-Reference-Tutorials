---
date: '2025-12-29'
description: 學習如何使用 GroupDocs.Parser for Java 從電子郵件和 .msg 檔案中提取圖像。包括設定、程式碼與實務技巧。
keywords:
- extract images from emails
- GroupDocs.Parser for Java
- image extraction email
title: 使用 GroupDocs.Parser for Java 從電郵中提取圖像
type: docs
url: /zh-hant/java/email-parsing/extract-images-emails-groupdocs-parser-java/
weight: 1
---

# 從電子郵件中提取圖像（使用 GroupDocs.Parser for Java）

從電子郵件訊息中提取圖像是開發人員常見的需求，無論是想自動化資料處理、改善客戶支援流程，或是建立內容豐富的檔案庫。本教學將教您如何使用功能強大的 GroupDocs.Parser Java 函式庫，**從電子郵件**檔案（尤其是 `.msg` 檔）中提取圖像。

## 快速回答
- **GroupDocs.Parser 的功能是什麼？** 它能解析多種文件格式，包括 Outlook 的 `.msg` 和 `.eml`，並提供對嵌入資源（如圖像）的簡易存取。  
- **提取時使用哪種圖像格式？** PNG，因為它能保留品質且廣受支援。  
- **我需要授權嗎？** 免費試用可用於測試；正式環境需購買完整授權。  
- **可以一次處理多封電子郵件嗎？** 可以——透過迴圈檔案即可實作批次處理。  
- **需要哪個 Java 版本？** Java 8 或更新版本。

## 什麼是「從電子郵件中提取圖像」？
當電子郵件內含嵌入的圖片——如螢幕截圖、產品照片或標誌——這些視覺資產會儲存在訊息檔案中。**從電子郵件中提取圖像** 意指以程式方式將 `.msg` 或 `.eml` 容器中的二進位物件抽取出來，以便儲存、分析或在其他地方顯示。

## 為何使用 GroupDocs.Parser 完成此任務？
- **廣泛的格式支援** – 可直接處理 `.msg` 與 `.eml`，無需額外外掛。  
- **簡易 API** – 只需呼叫一個方法 (`getImages()`) 即可取得所有圖像區域。  
- **效能最佳化** – 為大型檔案與高吞吐量情境而設計。  
- **跨平台** – 只要能執行 Java 的作業系統皆可使用。

## 前置條件
- **GroupDocs.Parser for Java** ≥ 25.5（建議使用最新版本）。  
- Java Development Kit (JDK) 8 或更新版本。  
- 任一 IDE，例如 IntelliJ IDEA 或 Eclipse。  
- 具備基本的 Java 語法與 Maven/Gradle 建置經驗。

## 設定 GroupDocs.Parser for Java

### Maven 依賴（建議）
將以下儲存庫與依賴項加入 `pom.xml`：

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

### 直接下載（若您偏好手動設定）
您也可以從官方發行頁面下載函式庫：[GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)。

### 取得授權
- **免費試用** – 無償評估 API。  
- **臨時授權** – 如有需要，可延長試用期限。  
- **完整授權** – 購買後可在正式環境無限制使用。

### 基本初始化與設定
以下是一個最小化的 Java 程式範例，示範如何開啟電子郵件檔案並為圖像提取做準備：

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;

public class EmailImageExtractor {
    public static void main(String[] args) {
        String inputFilePath = "path/to/your/sample.msg";
        
        try (Parser parser = new Parser(inputFilePath)) {
            Iterable<PageImageArea> images = parser.getImages();
            // Further processing will follow...
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## 實作指南

### 如何使用 GroupDocs.Parser 從電子郵件中提取圖像？

#### 步驟 1：設定圖像提取選項
在開始儲存檔案前，先設定欲輸出的格式（PNG）：

```java
import com.groupdocs.parser.options.ImageOptions;
import com.groupdocs.parser.options.ImageFormat;

ImageOptions options = new ImageOptions(ImageFormat.Png);
```

#### 步驟 2：遍歷圖像並儲存
以下迴圈會將每個發現的圖像儲存至目標資料夾，並以連續編號命名：

```java
int imageNumber = 0;

for (PageImageArea image : parser.getImages()) {
    String outputFilePath = "YOUR_OUTPUT_DIRECTORY/" + imageNumber + ".png";
    
    // Save each image using the configured options
    image.save(outputFilePath, options);
    imageNumber++;
}
```

#### 步驟 3：驗證輸出
程式執行完畢後，檢查 `YOUR_OUTPUT_DIRECTORY`。您應該會看到一系列 PNG 檔案（`0.png`、`1.png`、…），每個檔案對應原始電子郵件中嵌入的圖像。

### 如何從 msg 檔案中提取圖像？
相同程式碼亦適用於 `.msg` 檔，因為 GroupDocs.Parser 會自動偵測格式。只需將 `inputFilePath` 指向 `.msg` 檔，即可執行相同的提取迴圈。

### 如何在 Java 中解析 msg 檔案？
若您需要同時讀取訊息的其他部分（主旨、內容、附件），可使用額外的 `Parser` 方法，如 `getDocumentInfo()`、`getAttachments()` 與 `getText()`。此處示範的圖像提取是更廣泛 **parse msg files java** 工作流程的核心之一。

## 疑難排解技巧
- **檔案路徑錯誤：** 請再次確認輸入的 `.msg` 檔與輸出目錄皆已存在且可存取。  
- **版本不匹配：** 確認 Maven 依賴的版本與您下載的函式庫版本相同。  
- **權限問題：** 在 IDE 或命令列執行時，確保具有足夠的讀寫權限，特別是在 Windows 上資料夾權限可能受限。

## 實務應用
1. **客戶支援自動化** – 從收到的支援郵件中抽取螢幕截圖，以便快速分析。  
2. **行銷分析** – 從行銷活動郵件中收集視覺資產，以衡量品牌一致性。  
3. **文件管理系統** – 透過將提取的圖像附加至相關記錄，豐富中繼資料。

## 效能考量
- **記憶體管理：** 將大型郵箱分批處理，以避免過度使用堆積記憶體。  
- **非同步處理：** 使用 Java 的 `CompletableFuture` 或執行緒池，於大量檔案時平行化提取。  
- **保持更新：** 定期升級至最新的 GroupDocs.Parser 版本，以獲得效能提升與錯誤修正。

## 結論
現在您已掌握使用 GroupDocs.Parser for Java 來 **從電子郵件檔案中提取圖像** 的完整且可投入生產環境的方案。透過設定 `ImageOptions`、遍歷 `PageImageArea` 物件，並將每張圖像儲存為 PNG，您即可自動化各種工作流程——從支援工單處理到行銷資產管理。歡迎依需求擴充此範例，例如加入文字提取、附件處理或批次處理，以符合您的專案需求。

## 常見問題

**問：如何處理含有加密附件的電子郵件？**  
**答：** GroupDocs.Parser 不會解密加密內容；您必須先自行解密附件或取得相應的憑證。

**問：GroupDocs.Parser 能從所有電子郵件格式提取圖像嗎？**  
**答：** 它支援最常見的格式，包括 `.msg` 與 `.eml`。完整相容性清單請參考官方文件。

**問：執行 GroupDocs.Parser 的系統需求是什麼？**  
**答：** 需要 Java 8更新版本，且具備足夠記憶體以載入郵件檔（一般訊息約 256 MB）。

**問：如何提升數千封電子郵件的提取速度？**  
**答：** 採用批次處理，將同時執行的執行緒數量限制為與 CPU 核心數相符，並盡可能重複使用單一 `Parser` 實例。

**問：在哪裡可以找到更多程式碼範例？**  
**答：** 前往 [GroupDocs GitHub repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java) 取得更多範例與社群貢獻。

---
**最後更新：** 2025-12-29  
**測試版本：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs  

## 資源

- **文件說明：** [GroupDocs Parser Java Docs](https://docs.groupdocs.com/parser/java/)  
- **API 參考：** [GroupDocs API Documentation](https://reference.groupdocs.com/parser/java)  
- **下載：** [Get the Latest Version](https://releases.groupdocs.com/parser/java/)  
- **GitHub：** [Explore on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **免費支援：** [Join GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **臨時授權：** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)