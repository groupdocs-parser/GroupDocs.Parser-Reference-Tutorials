---
date: '2026-08-05'
description: 了解如何使用 GroupDocs.Parser for Java 從 Word 文件中提取圖像，並高效地將 Word 圖像保存為 PNG。
keywords:
- extract images from word
- how to extract images
- extract images from docx
- extract pictures from word
- convert word images png
lastmod: '2026-08-05'
og_description: 使用 GroupDocs.Parser for Java 從 Word 文件中提取圖像。一步一步了解如何提取圖片，並高效地將 Word
  圖像保存為 PNG。
og_image_alt: Code example showing image extraction from a Word document using GroupDocs.Parser
  for Java
og_title: 使用 GroupDocs.Parser for Java 從 Word 提取圖像
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  headline: Extract images from word using GroupDocs.Parser for Java
  type: TechArticle
- description: Learn how to extract images from word documents using GroupDocs.Parser
    for Java and save word images png efficiently.
  name: Extract images from word using GroupDocs.Parser for Java
  steps:
  - name: initialize the parser
    text: The `Parser` class is the entry point for reading a document. It loads the
      file into memory and prepares all content streams for extraction.
  - name: extract images
    text: '`PageImageArea` objects represent each picture found in the document, regardless
      of whether the image is inline, floating, or part of a shape.'
  - name: configure image options
    text: '`ImageOptions` lets you specify the output format, resolution, and other
      rendering settings before saving each picture.'
  - name: save each image
    text: '`ImageFormat` enum defines the output image format such as PNG, JPEG, or
      BMP. The `save` method writes the binary image data to a file on disk. By passing
      `ImageFormat.Png`, you satisfy the **save word images png** requirement.'
  - name: define helper methods for paths
    text: Utility methods simplify path handling and keep the main extraction logic
      clean and maintainable. Replace `YOUR_DOCUMENT_DIRECTORY` and `YOUR_OUTPUT_DIRECTORY`
      with the actual file system locations you intend to use.
  type: HowTo
- questions:
  - answer: It handles DOC, DOCX, PDF, PPT, PPTX, and many other formats, exposing
      images via the same `getImages()` method.
    question: What file formats does GroupDocs.Parser support for image extraction?
  - answer: Yes—pass the password to the `Parser` constructor, and the library will
      decrypt the document before extraction.
    question: Can I extract images from password‑protected Word files?
  - answer: After retrieving `PageImageArea` objects, inspect `image.getFormat()`
      and filter accordingly before saving.
    question: Is there a way to extract only specific image types (e.g., JPEG only)?
  - answer: While the core API is synchronous, you can wrap the extraction logic in
      a separate thread or use Java’s `CompletableFuture` for parallel processing.
    question: Does the library support asynchronous processing?
  - answer: A free trial is fine for evaluation, but a paid license is required for
      commercial deployments.
    question: Do I need a commercial license for production use?
  type: FAQPage
tags:
- extract images
- GroupDocs.Parser
- Java document processing
title: 使用 GroupDocs.Parser for Java 從 Word 提取圖像
type: docs
url: /zh-hant/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# 從 Word 中提取圖像，使用 GroupDocs.Parser for Java

手動從 Word 檔案中提取圖像既耗時又容易出錯。在本教學中，您將了解如何使用 GroupDocs.Parser for Java 自動 **how to extract images from word** 文件，並將 **save word images png** 以供後續處理。您將清楚了解此函式庫為何快速、如何設定，以及最佳實踐技巧，讓您能將圖像提取嵌入任何 Java 應用程式中。

## 快速答案
- **What does the library do?** 它會解析 Word、PDF 以及許多其他格式，並提供文字、表格與圖像。  
- **How many lines of code?** 大約 30 行 Java 程式碼，加上一些設定行。  
- **Do I need a license?** 免費試用可用於開發；正式環境需購買完整授權。  
- **Can I extract embedded images?** 是的 – `getImages()` 方法會回傳所有嵌入的圖像。  
- **Supported output format?** 預設為 PNG，但可透過 `ImageFormat` 使用其他格式。

## 何謂「extract images from word」？
Extract images from word 指以程式方式取得 Microsoft Word 文件中所有嵌入的圖片檔案。GroupDocs.Parser 會讀取 DOCX 或 DOC 檔的二進位結構，並將每張圖像以 `PageImageArea` 物件呈現，讓您無需在 Microsoft Word 中開啟文件即可提取所有圖片。此方法可消除手動複製貼上，降低人為錯誤，且能在批次作業中擴展至數千個檔案。

## 為何使用 GroupDocs.Parser for Java？
您可以以 **速度**、**可靠性** 與 **跨平台彈性** 從 Word 文件中提取圖像。GroupDocs.Parser 能在標準 2 核心伺服器上於 2 秒內處理 200 頁的 DOCX，且可在 Windows、Linux 與 macOS 上運行，無需 Microsoft Office。此函式庫亦能容忍損壞的檔案，回傳仍可取得的圖像，因而非常適合大規模遷移專案。

## 前置條件
- **GroupDocs.Parser for Java**（版本 25.5 或更新）  
- **JDK 8+** 已安裝於您的開發機器上  
- 使用 IntelliJ IDEA、Eclipse 或 NetBeans 等 IDE 進行程式編輯與執行  

## 設定 GroupDocs.Parser for Java
將函式庫加入您的 Maven 專案：

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

或者，直接從 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下載最新版本。

### 取得授權步驟
- **Free trial:** 先使用免費試用以探索功能。  
- **Temporary license:** 如有需要，可取得臨時授權以延長測試。  
- **Purchase:** 取得完整授權以供正式環境部署。

## 實作指南
以下為完整、可直接執行的 Java 程式碼，**extracts images from word** 文件並將其儲存為 PNG 檔案。

### 步驟 1：初始化解析器
`Parser` 類別是讀取文件的入口點。它會將檔案載入記憶體，並準備所有內容串流以供提取。

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### 步驟 2：提取圖像
`PageImageArea` 物件代表文件中找到的每張圖片，無論圖像是內嵌、浮動或屬於形狀的一部份。

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### 步驟 3：設定圖像選項
`ImageOptions` 讓您在儲存每張圖片前指定輸出格式、解析度以及其他渲染設定。

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### 步驟 4：儲存每張圖像
`ImageFormat` 列舉定義輸出圖像格式，如 PNG、JPEG 或 BMP。  
`save` 方法會將二進位圖像資料寫入磁碟檔案。傳入 `ImageFormat.Png` 即可滿足 **save word images png** 的需求。

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### 步驟 5：定義路徑輔助方法
輔助方法簡化路徑處理，讓主要的提取邏輯保持簡潔且易於維護。

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

將 `YOUR_DOCUMENT_DIRECTORY` 與 `YOUR_OUTPUT_DIRECTORY` 替換為您實際要使用的檔案系統路徑。

## 如何從 docx 中提取嵌入的圖像？
`getImages()` 方法會回傳 `PageImageArea` 物件集合，代表每個嵌入的圖像。  
使用 `new Parser("input.docx")` 載入 DOCX，然後呼叫 `parser.getImages()` – 此方法會自動回傳所有嵌入的圖像，包括內嵌圖片、浮動形狀與 VML 繪圖。無需額外的 API 呼叫，您即可直接遍歷回傳的集合並處理每個 `PageImageArea`。

## 如何從 docx 提取圖像並儲存為 PNG？
建立 `ImageOptions` 實例，設定 `options.setImageFormat(ImageFormat.Png)`，並將其傳入 `image.save(outputPath, options)`。此設定可確保每張提取的圖片以 PNG 檔寫入，滿足 **save word images png** 目標，同時保留原始解析度與色彩深度。

## 實務應用
1. **Content management:** 從舊有 Word 檔案中提取圖像，建立數位資產庫。  
2. **Data migration:** 將嵌入的圖形遷移至新 CMS，免除手動複製貼上。  
3. **Document archiving:** 將圖像分別儲存，以減少封存大小並提升可搜尋性。  
4. **Automated publishing:** 將提取的 PNG 直接供給網頁產生器或電子郵件範本使用。  

## 效能考量
- **Memory usage:** 處理大型文件時至少配置 `-Xmx2g`；解析器會串流資料以降低堆積使用量。  
- **Batch processing:** 在迴圈中對每個文件重複使用單一 `Parser` 實例，以減少物件建立開銷。  
- **File handles:** 使用 try‑with‑resources 區塊可確保解析器即時關閉，防止檔案描述符泄漏。  

## 常見問題與解決方案
| 問題 | 解決方案 |
|-------|----------|
| **OutOfMemoryError** 在巨大的 DOCX 檔案上發生 | 增加 JVM 堆積大小或將文件分成較小的批次處理。 |
| **未返回圖像** | 確認文件確實包含嵌入的圖像；某些「圖片」是 VML 繪圖，未以圖像形式暴露。 |
| **圖像方向不正確** | 部分 DOCX 圖像會儲存 EXIF 旋轉資訊；如有需要，可使用圖像函式庫進行後處理。 |

## 常見問答

**Q: GroupDocs.Parser 支援哪些檔案格式的圖像提取？**  
A: 它支援 DOC、DOCX、PDF、PPT、PPTX 以及許多其他格式，並透過相同的 `getImages()` 方法公開圖像。

**Q: 能否從受密碼保護的 Word 檔案中提取圖像？**  
A: 可以——在 `Parser` 建構子中傳入密碼，函式庫會在提取前解密文件。

**Q: 有沒有辦法只提取特定類型的圖像（例如僅 JPEG）？**  
A: 取得 `PageImageArea` 物件後，可檢查 `image.getFormat()`，再依需求過濾後再儲存。

**Q: 函式庫支援非同步處理嗎？**  
A: 雖然核心 API 為同步，但您可將提取邏輯包裝於獨立執行緒，或使用 Java 的 `CompletableFuture` 進行平行處理。

**Q: 生產環境使用是否需要商業授權？**  
A: 免費試用適合評估，但商業部署需購買授權。

---

**最後更新：** 2026-08-05  
**測試版本：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

**資源**  
- **文件說明：** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)  
- **API 參考：** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)  
- **下載：** [Latest Release](https://releases.groupdocs.com/parser/java/)  
- **GitHub：** [Source code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **免費支援：** [GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **臨時授權：** [Obtain a temporary license](https://purchase.groupdocs.com/temporary-license/)

## 相關教學

- [如何使用 GroupDocs.Parser for Java 保存圖像](/parser/java/image-extraction/extract-images-groupdocs-parser-java/)
- [如何使用 GroupDocs.Parser 在 Java 中從 PDF 提取圖像：逐步指南](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)
- [如何使用 GroupDocs.Parser 在 Java 中從 Word 文件提取文字](/parser/java/text-extraction/extract-text-word-docs-groupdocs-parser-java/)