---
date: '2026-07-16'
description: 了解如何使用 GroupDocs.Parser 以 Java 建立試算表縮圖、在未安裝 Office 的情況下預覽 Excel，並將 Excel
  工作表渲染為圖像。本指南涵蓋設定、實作以及實務案例。
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: 使用 GroupDocs.Parser 建立 Java 試算表縮圖——在未安裝 Office 的情況下預覽 Excel，並將 Excel
  工作表渲染為圖像。請依照此一步一步的指南高效產生 PNG 預覽。
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: 使用 GroupDocs.Parser 建立 Java 試算表縮圖
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: 使用 GroupDocs.Parser 建立 Java 試算表縮圖
type: docs
url: /zh-hant/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# 使用 GroupDocs.Parser 建立 Java 試算表縮圖

如果您正在尋找 **create spreadsheet thumbnail Java** 程式，您已來對地方。在本指南中，我們將說明如何使用 GroupDocs.Parser for Java 從 `.xlsx` 工作簿產生高品質 PNG 預覽——非常適合快速縮圖、分享快照，或在您的應用程式中建立文件預覽功能。此解決方案不需要安裝 Microsoft Office，且可擴展至大型工作簿，同時保持低記憶體使用量。

## 快速解答
- **什麼是「preview Excel」？** 產生代表每個工作表頁面的影像檔案（例如 PNG）。  
- **建議使用哪種格式？** PNG 提供無損品質，且非常適合網頁縮圖。  
- **需要授權嗎？** 免費試用可用於開發；正式環境需購買商業授權。  
- **可以更改影像解析度嗎？** 可以——在 `PreviewOptions` 中調整 DPI。  
- **可以預覽其他格式嗎？** GroupDocs.Parser 亦支援 PDF、Word 以及多種影像類型。

## 「如何使用 GroupDocs.Parser 預覽 Excel」是什麼？
載入您的 Excel 工作簿，將每個工作表渲染為 PNG 影像，無需 Microsoft Office。GroupDocs.Parser 會一次串流一頁，產生無損縮圖，可儲存至磁碟或透過 HTTP 回傳，非常適合基於 Web 的預覽服務。

GroupDocs.Parser 讀取 Excel 工作簿，將每個工作表渲染為視覺頁面，並允許您將這些頁面串流為影像檔案。這消除了對 Office 互操作或第三方轉換器的需求。

## 為什麼使用 GroupDocs.Parser 進行 Excel 預覽？
您應該使用 GroupDocs.Parser，因為它可在任何 Java 伺服器上運行，無需 Office 安裝，能以低記憶體處理大型工作簿，並產生可設定 DPI 的無損 PNG 影像。SDK 支援 **100+ 輸入與輸出格式**，可在 3 秒內處理 200 頁的工作簿，且每張工作表的記憶體使用量低於 50 MB。

- **不需要 Office 安裝** – 可在任何伺服器端 Java 環境執行。  
- **支援大型檔案** – 逐頁串流，保持低記憶體使用。  
- **高品質輸出** – 可控制 DPI、格式與渲染選項。  
- **跨格式彈性** – 相同 API 可用於 PDF、Word 文件等。

## 前置條件
- **Java Development Kit** (8 +)。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse。  
- **GroupDocs.Parser for Java SDK** – 從 [here](https://releases.groupdocs.com/parser/java/) 下載。  
- **Documentation** – 請參閱官方 [documentation](https://docs.groupdocs.com/parser/java/)。  
- **Sample Excel file** (`.xlsx`) 您想要預覽的範例檔案。  
- **Maven 或 Gradle**（可選）用於相依管理。

## 匯入套件
以下匯入讓您可以使用 parser、preview options 與串流處理工具。

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

## 逐步指南：產生試算表頁面預覽

### 步驟 1：初始化 Parser 實例
`Parser` 是 GroupDocs.Parser 的核心類別，提供對試算表檔案的讀取存取並支援逐頁渲染。  
建立指向您的 Excel 工作簿的 `Parser` 物件。*try‑with‑resources* 區塊會自動關閉 parser。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **小技巧：** 使用絕對路徑或設定資源資料夾，以避免 `FileNotFoundException`。

### 步驟 2：準備預覽選項
`PreviewOptions` 設定渲染參數，例如輸出格式與 DPI。  
`ICreatePageStream` 是回呼介面，為每個產生的頁面提供輸出串流。定義每頁的儲存方式。`ICreatePageStream` 的實作會為每個工作表頁面返回新的 `FileOutputStream`。

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

> 此步驟即是 **convert xlsx to png**——串流將 PNG 資料寫入磁碟。

### 步驟 3：附加委派以捕獲渲染資訊
如果您需要每個渲染工作表的詳細資訊（例如尺寸、工作表名稱），請註冊回呼。

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
選擇 PNG 作為影像格式，並設定兼顧品質與檔案大小的 DPI。

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> 若需要較小的縮圖（例如 96）或高解析度列印（例如 300），請調整 DPI。

### 步驟 5：產生預覽
完成所有設定後，呼叫 `generatePreview`。SDK 會遍歷每個工作表，並呼叫您提供的串流。

```java
parser.generatePreview(previewOptions);
```

### 步驟 6：定義 `getOutputPath()` 輔助方法
`getOutputPath()` 會根據頁面（工作表）編號建立檔名，並返回輸出影像的完整路徑。您可以自行客製化資料夾結構。

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **常見陷阱：** 若事先未建立 `output` 目錄，會導致 `IOException`。請以程式方式建立或確保其已存在。

## 完整工作範例（簡化版）

以下是一個將所有部分結合的精簡版本。它示範了 **create spreadsheet thumbnail Java** 工作流程的全程。

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

執行此程式碼片段後，您會在 `output` 資料夾中看到一系列 `preview_page_1.png`、`preview_page_2.png` … 檔案——每個檔案皆代表原始 Excel 工作簿中的一個工作表。

## 常見問題與解決方案
| 問題 | 原因 | 解決方案 |
|-------|-------|-----|
| **未產生影像** | `getOutputPath` 回傳無效目錄 | 確保目標資料夾存在，或使用 `new File("output").mkdirs();` 建立。 |
| **大型檔案記憶體不足錯誤** | 一次載入整個工作簿 | 使用串流方式（如示範）逐頁處理。 |
| **DPI 設定錯誤** | 未呼叫 `setDpi` 或使用預設值 (96) | 在 `generatePreview` 前呼叫 `previewOptions.setDpi(yourDesiredValue);` |
| **不支援的格式** | 嘗試預覽損壞的 `.xlsx` | 使用 Excel 檢查檔案或在處理前使用 `Parser.isSupported` 進行驗證 |

## 常見問答

**Q: 我可以使用 GroupDocs.Parser 為 PDF 和影像產生預覽嗎？**  
A: 可以，相同的 API 可用於 PDF、Word 文件以及多種影像格式。

**Q: 如何變更輸出影像格式？**  
A: 呼叫 `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`（或 `Gif`、`Bmp` 等）。

**Q: 處理非常大型的工作簿時效能會是問題嗎？**  
A: SDK 會串流頁面，保持低記憶體使用。對於超大型檔案，可考慮以平行批次方式處理。

**Q: 如何處理預覽產生過程中的錯誤？**  
A: 如範例所示，將程式碼包在 try‑catch 區塊中並記錄例外細節。若未使用 try‑with‑resources，請在 `finally` 區塊中關閉串流。

**Q: 此函式庫需要安裝 Microsoft Office 嗎？**  
A: 不需要。GroupDocs.Parser 是純 Java 解決方案，可在任何支援 Java 8+ 的平台上運行。

**最後更新：** 2026-07-16  
**測試版本：** GroupDocs.Parser 23.11（撰寫時的最新版本）  
**作者：** GroupDocs

## 相關教學

- [如何產生預覽 – GroupDocs.Parser Java 文件頁面預覽生成教學](/parser/java/page-preview-generation/)
- [使用 GroupDocs.Parser 解析 Excel Java：完整指南](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [如何使用 GroupDocs.Parser for Java 從 Excel 工作表提取原始文字：逐步指南](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)