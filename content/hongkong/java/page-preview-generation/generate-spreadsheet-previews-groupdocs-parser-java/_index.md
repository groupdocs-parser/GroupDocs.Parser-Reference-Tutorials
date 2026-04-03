---
date: '2026-02-06'
description: 學習如何使用 GroupDocs.Parser for Java 預覽 Excel 檔案並將 xlsx 轉換為 png。本教學涵蓋設定、實作及實用應用。
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: 如何在 Java 中使用 GroupDocs.Parser 預覽 Excel 檔案
type: docs
url: /zh-hant/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Parser 預覽 Excel 檔案

如果您正在尋找 **如何程式化預覽 Excel** 試算表，您已經來對地方了。在本指南中，我們將說明如何使用 GroupDocs.Parser for Java 從 `.xlsx` 工作簿建立影像預覽（PNG）——非常適合快速產生縮圖、分享快照，或在您的應用程式中建構文件預覽功能。

## 快速解答
- **「預覽 Excel」是什麼意思？** 產生代表每個工作表頁面的影像檔（例如 PNG）。  
- **建議使用哪種格式？** PNG 提供無損品質，且非常適合網頁縮圖。  
- **需要授權嗎？** 免費試用可用於開發；正式上線需購買商業授權。  
- **可以調整影像解析度嗎？** 可以——在 `PreviewOptions` 中調整 DPI。  
- **能否預覽其他格式？** GroupDocs.Parser 也支援 PDF、Word 以及多種影像類型。

## 使用 GroupDocs.Parser 「預覽 Excel」是什麼？
GroupDocs.Parser 讀取 Excel 工作簿，將每個工作表渲染為視覺頁面，並允許您將這些頁面串流為影像檔。這樣就不需要 Office 互操作或第三方轉換器。

## 為什麼使用 GroupDocs.Parser 來預覽 Excel？
- **不需要安裝 Office** – 可在任何伺服器端 Java 環境執行。  
- **支援大型檔案** – 逐頁串流，降低記憶體使用量。  
- **高品質輸出** – 可控制 DPI、格式與渲染選項。  
- **跨格式彈性** – 同一套 API 可用於 PDF、Word 文件等。

## 前置條件
- **Java Development Kit**（8 以上）。  
- **IDE**（如 IntelliJ IDEA 或 Eclipse）。  
- **GroupDocs.Parser for Java SDK** – 從 [here](https://releases.groupdocs.com/parser/java/) 下載。  
- **要預覽的範例 Excel 檔案**（`.xlsx`）。  
- **Maven 或 Gradle**（可選）用於相依管理。

## 匯入套件
以下匯入讓您可以使用 parser、預覽選項以及串流處理工具。

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

## 步驟說明：產生試算表頁面預覽

### 步驟 1：初始化 Parser 實例
建立指向您的 Excel 工作簿的 `Parser` 物件。*try‑with‑resources* 區塊會自動關閉 parser。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **專業提示：** 使用絕對路徑或設定資源資料夾，以避免 `FileNotFoundException`。

### 步驟 2：準備預覽選項
定義每頁的儲存方式。`ICreatePageStream` 實作會為每個工作表頁面返回一個新的 `FileOutputStream`。

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

> 這一步即是 **將 xlsx 轉換為 png**——串流會將 PNG 資料寫入磁碟。

### 步驟 3：附加委派以捕獲渲染資訊
如果您需要每個已渲染工作表的詳細資訊（例如尺寸、工作表名稱），請註冊回呼函式。

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### 步驟 4：指定輸出格式與 DPI
選擇 PNG 作為影像格式，並設定一個在品質與檔案大小之間取得平衡的 DPI。

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> 若需要較小的縮圖（例如 96）或高解析度列印（例如 300），請調整 DPI。

### 步驟 5：產生預覽
完成所有設定後，呼叫 `generatePreview`。SDK 會遍歷每個工作表並呼叫您提供的串流。

```java
parser.generatePreview(previewOptions);
```

### 步驟 6：定義 `getOutputPath()` 輔助方法
此方法會根據頁面（工作表）編號建立檔名。您可以自由自訂資料夾結構。

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **常見陷阱：** 若事先未建立 `output` 目錄，會拋出 `IOException`。請以程式方式建立或確保其已存在。

## 完整範例（簡化版）

以下是一個將所有部件結合的精簡版範例。它示範了 **建立 Excel 頁面預覽** 的完整工作流程。

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

執行此程式碼後，您會在 `output` 資料夾中看到一系列 `preview_page_1.png`、`preview_page_2.png`… 檔案——每個檔案對應原始 Excel 工作簿中的一個工作表。

## 常見問題與解決方案
| 問題 | 原因 | 解決方案 |
|------|------|----------|
| **未產生影像** | `getOutputPath` 回傳無效目錄 | 確保目標資料夾存在，或使用 `new File("output").mkdirs();` 建立它。 |
| **大型檔案記憶體不足錯誤** | 一次載入整個工作簿 | 使用串流方式（如示範）逐頁處理。 |
| **DPI 設定不正確** | `setDpi` 未呼叫或使用預設值 (96) | 在 `generatePreview` 前呼叫 `previewOptions.setDpi(yourDesiredValue);`。 |
| **不支援的格式** | 嘗試預覽受損的 `.xlsx` 檔案 | 使用 Excel 檢查檔案，或在處理前使用 `Parser.isSupported`。 |

## 常見問答

**問：我可以使用 GroupDocs.Parser 產生 PDF 與影像的預覽嗎？**  
答：可以，相同的 API 可用於 PDF、Word 文件以及多種影像格式。

**問：如何變更輸出影像格式？**  
答：呼叫 `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`（或 `Gif`、`Bmp` 等）。

**問：處理非常大型的工作簿時效能會是問題嗎？**  
答：SDK 會串流頁面，保持低記憶體使用。對於巨量檔案，可考慮平行批次處理。

**問：如何處理預覽產生過程中的錯誤？**  
答：將程式碼包在 try‑catch 區塊（如示範），並記錄例外細節。若未使用 try‑with‑resources，請在 `finally` 區塊關閉串流。

**問：此函式庫是否需要安裝 Microsoft Office？**  
答：不需要。GroupDocs.Parser 為純 Java 解決方案，適用於任何支援 Java 8+ 的平台。

## 結論
現在您已擁有使用 GroupDocs.Parser 進行 **Excel 預覽** 以及 **將 xlsx 轉換為 png** 的完整、可投入生產的方法。依需求調整 DPI、輸出資料夾或影像格式，並將此程式碼片段整合到更大的文件管理工作流程中。

準備好下一步了嗎？請參考官方 [documentation](https://docs.groupdocs.com/parser/java/) 以了解進階渲染選項、受密碼保護的檔案以及批次處理技巧。

---

**最後更新：** 2026-02-06  
**測試版本：** GroupDocs.Parser 23.11（撰寫時的最新版本）  
**作者：** GroupDocs