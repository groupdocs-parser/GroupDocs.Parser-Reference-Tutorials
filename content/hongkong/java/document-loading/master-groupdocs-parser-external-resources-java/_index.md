---
date: '2025-12-29'
description: 了解如何使用 GroupDocs.Parser for Java 從文件中提取圖像以及如何過濾資源。本指南涵蓋配置、自訂處理程式和實用範例。
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: 使用 GroupDocs.Parser Java 從文件中提取圖片 – 指南
type: docs
url: /zh-hant/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# 從文件中提取圖像並使用 GroupDocs.Parser Java 篩選資源

從文件中提取圖像是建構文件處理管線時的常見需求。在本教學中，您將學會 **如何使用 GroupDocs.Parser for Java 提取圖像**，同時了解 **如何篩選資源**，只載入所需的檔案。我們將逐步說明如何設定函式庫、建立自訂的 `ExternalResourceHandler`，以及套用篩選邏輯，以保持應用程式的效能與安全性。

## 快速解答
- **GroupDocs.Parser 的功能是什麼？** 它能解析多種文件格式，並讓您存取文字、圖像及其他嵌入資源。  
- **我可以跳過不需要的圖像嗎？** 可以——透過實作自訂的 `ExternalResourceHandler`，您可以決定載入哪些資源。  
- **需要哪個 Maven 版本？** 使用 GroupDocs.Parser Java 25.5 或更新版本。  
- **我需要授權嗎？** 免費試用可用於評估；正式環境需購買永久授權。  
- **此方法是執行緒安全的嗎？** 解析物件不會在執行緒間共享；每個執行緒請建立新的 `Parser` 實例。

## 什麼是「從文件中提取圖像」？
當文件內含嵌入的圖片、圖表或其他媒體時，「從文件中提取圖像」指的是以程式方式取得這些二進位檔案，讓您能將它們儲存、顯示或在原始文件之外進一步處理。

## 為什麼在提取圖像時要篩選資源？
篩選資源可協助您：
- 透過忽略大型或不相關的檔案來減少記憶體使用量。  
- 防止載入可能不安全的內容，以提升安全性。  
- 加快處理速度，特別是對於包含大量嵌入物件的巨型文件。

## 前置條件

- **Java Development Kit (JDK)** – 8 版或以上。  
- **Maven** – 用於相依管理。  
- 具備 Java I/O 與例外處理的基本知識。

## 設定 GroupDocs.Parser for Java

將 GroupDocs 儲存庫與 parser 相依項目加入您的 `pom.xml`：

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

或者，從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新版本。

### 取得授權
- **免費試用** – 無償探索核心功能。  
- **臨時授權** – 評估期間解鎖全部功能。  
- **購買授權** – 商業部署必須使用。

## 如何在提取圖像時篩選資源

### 步驟 1：建立自訂處理器
定義一個繼承自 `ExternalResourceHandler` 的類別。在 `onLoading` 方法內決定保留哪些資源。

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### 步驟 2：使用處理器設定 `ParserSettings`
將您的 `Handler` 實例傳入 `ParserSettings`，並在開啟文件時使用它。

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### 步驟 3：微調篩選邏輯
如果需要更複雜的規則——例如依圖像大小、格式或 URI 模式篩選——請相應地擴充 `onLoading` 方法：

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## 實務應用

1. **文件管理系統** – 從掃描的合約中僅提取必要的圖像以產生縮圖。  
2. **資料抽取服務** – 跳過裝飾性圖形，專注於包含有價值資料的圖表。  
3. **網頁爬蟲工具** – 在從 HTML 文件中取得有意義的媒體時，過濾掉追蹤像素。

## 效能考量
- **提前篩選**：在遍歷資源之前套用自訂處理器，以避免將不需要的資料載入記憶體。  
- **及時釋放**：使用 try‑with‑resources (`try (Parser parser = …)`) 釋放原生資源。  
- **非同步處理**：對於大量批次，使用平行串流處理文件，同時確保每個 `Parser` 實例僅在單一執行緒中使用。

## 常見問題與解決方案
| 問題 | 發生原因 | 解決方式 |
|------|----------|----------|
| 未返回圖像 | 處理器不小心跳過了所有資源 | 檢查 `if` 條件，確保 `args.setSkipped(true)` 只在不需要的 URI 上被呼叫。 |
| 大型檔案發生 `IOException` | 堆積記憶體不足 | 增加 JVM 堆積大小（例如 `-Xmx2g`）或將頁面分成較小的區塊處理。 |
| 授權未被識別 | 在正式程式碼中使用試用版 DLL | 透過 `License.setLicense("path/to/license")` 設定正確的授權檔案路徑。 |

## 常見問答

**Q: 使用自訂 `ExternalResourceHandler` 的主要目的為何？**  
A: 它讓您能控制載入哪些外部資源，透過篩除不必要的檔案提升安全性與效能。

**Q: 我可以在沒有授權的情況下使用 GroupDocs.Parser for Java 嗎？**  
A: 可以，免費試用可供使用，但某些進階功能在取得臨時或正式授權前可能受限。

**Q: 如何在使用 GroupDocs.Parser 解析時處理例外情況？**  
A: 將解析呼叫包在 try‑catch 區塊中，捕捉 `IOException` 及其他特定例外，以優雅地處理錯誤。

**Q: 篩選資源時常見的陷阱是什麼？**  
A: URI 判斷錯誤可能會跳過必要的檔案；建議使用日誌或斷點驗證條件是否正確。

**Q: 是否可以使用 GroupDocs.Parser for Java 解析非 HTML 文件？**  
A: 當然可以——GroupDocs.Parser 支援 PDF、Word、Excel、PowerPoint 等多種格式。

## 後續步驟
深入探索函式庫，可參考 [API Reference](https://reference.groupdocs.com/parser/java) 或嘗試額外設定，例如 `ParserSettings.setDetectTables(true)` 以進行表格抽取。

---

**最後更新：** 2025-12-29  
**測試環境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs  

**資源**  
- **文件說明：** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API 參考：** [API Details](https://reference.groupdocs.com/parser/java)  
- **下載：** [Latest Versions](https://releases.groupdocs.com/parser/java/)