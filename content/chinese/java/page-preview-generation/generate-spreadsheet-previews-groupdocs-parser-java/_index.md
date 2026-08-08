---
date: '2026-07-16'
description: 了解如何使用 GroupDocs.Parser 在 Java 中创建电子表格缩略图，预览 Excel 而无需 Office，并将 Excel
  工作表渲染为图像。本指南涵盖设置、实现以及实际用例。
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: 使用 GroupDocs.Parser 在 Java 中创建电子表格缩略图——无需 Office 即可预览 Excel 并将 Excel
  工作表渲染为图像。遵循本分步指南，高效生成 PNG 预览。
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: 使用 GroupDocs.Parser 在 Java 中创建电子表格缩略图
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
title: 使用 GroupDocs.Parser 在 Java 中创建电子表格缩略图
type: docs
url: /zh/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# 使用 GroupDocs.Parser 创建电子表格缩略图 Java

如果您正在寻找 **创建电子表格缩略图 Java** 程序，您来对地方了。在本指南中，我们将演示如何使用 GroupDocs.Parser for Java 从 `.xlsx` 工作簿生成高质量的 PNG 预览——非常适合快速缩略图、共享快照或在您的应用程序中构建文档预览功能。该解决方案无需 Microsoft Office 安装，并且能够在处理大型工作簿时保持低内存使用。

## 快速答案
- **“preview Excel” 是什么意思？** 生成图像文件（例如 PNG），以表示每个工作表页面。  
- **推荐使用哪种格式？** PNG 提供无损质量，且非常适合网页缩略图。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要商业许可证。  
- **我可以更改图像分辨率吗？** 可以——在 `PreviewOptions` 中调整 DPI。  
- **是否可以预览其他格式？** GroupDocs.Parser 还支持 PDF、Word 和多种图像类型。

## 使用 GroupDocs.Parser “预览 Excel” 是什么？

加载您的 Excel 工作簿并将每个工作表渲染为 PNG 图像，无需 Microsoft Office。GroupDocs.Parser 逐页流式处理，生成无损缩略图，可保存到磁盘或通过 HTTP 返回，非常适合基于 Web 的预览服务。

GroupDocs.Parser 读取 Excel 工作簿，将每个工作表渲染为可视页面，并允许您将这些页面流式输出为图像文件。这消除了对 Office 互操作或第三方转换器的需求。

## 为什么使用 GroupDocs.Parser 进行 Excel 预览？

您应该使用 GroupDocs.Parser，因为它可在任何 Java 服务器上运行，无需 Office 安装，能够以低内存处理大型工作簿，并生成可配置 DPI 的无损 PNG 图像。SDK 支持 **100+ 输入和输出格式**，可在 3 秒内处理 200 页的工作簿，并将每个工作表的内存使用保持在 50 MB 以下。

- **无需 Office 安装** – 可在任何服务器端 Java 环境中运行。  
- **支持大文件** – 逐页流式处理，保持低内存使用。  
- **高质量输出** – 可控制 DPI、格式和渲染选项。  
- **跨格式灵活性** – 同一 API 可用于 PDF、Word 文档等。

## 先决条件
- **Java Development Kit**（8 及以上）。  
- **IDE**（如 IntelliJ IDEA 或 Eclipse）。  
- **GroupDocs.Parser for Java SDK** – 从 [此处](https://releases.groupdocs.com/parser/java/) 下载。  
- **文档** – 请参阅官方的 [文档](https://docs.groupdocs.com/parser/java/)。  
- **示例 Excel 文件**（`.xlsx`），您想要预览的文件。  
- **Maven 或 Gradle**（可选），用于依赖管理。

## 导入包
这些导入为您提供对解析器、预览选项和流处理实用程序的访问。

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

## 逐步指南：生成电子表格页面预览

### 步骤 1：初始化 Parser 实例
`Parser` 是 GroupDocs.Parser 的核心类，提供对电子表格文件的读取访问并支持逐页渲染。  
创建一个指向您的 Excel 工作簿的 `Parser` 对象。*try‑with‑resources* 块可确保自动关闭 parser。

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **技巧提示：** 使用绝对路径或配置资源文件夹，以避免 `FileNotFoundException`。

### 步骤 2：准备预览选项
`PreviewOptions` 配置渲染参数，如输出格式和 DPI。  
`ICreatePageStream` 是一个回调接口，为每个生成的页面提供输出流。定义每页的保存方式。`ICreatePageStream` 实现为每个工作表页面返回一个新的 `FileOutputStream`。

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

> 这一步是 **convert xlsx to png** 的过程——流将 PNG 数据写入磁盘。

### 步骤 3：附加委托以捕获渲染信息
如果您需要每个渲染工作表的详细信息（例如尺寸、工作表名称），请注册回调。

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### 步骤 4：指定输出格式和 DPI
选择 PNG 作为图像格式，并设置在质量和文件大小之间取得平衡的 DPI。

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> 如果需要更小的缩略图（例如 96）或高分辨率打印（例如 300），请调整 DPI。

### 步骤 5：生成预览
在完成所有配置后，调用 `generatePreview`。SDK 将遍历每个工作表并调用您提供的流。

```java
parser.generatePreview(previewOptions);
```

### 步骤 6：定义 `getOutputPath()` 辅助方法
`getOutputPath()` 根据页面（工作表）编号构建文件名，并返回输出图像的完整路径。您可以随意自定义文件夹结构。

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **常见陷阱：** 事先未创建 `output` 目录会导致 `IOException`。请以编程方式创建或确保其已存在。

## 完整工作示例（简化版）

下面是一个将所有部分结合在一起的简洁版本。它演示了 **create spreadsheet thumbnail Java** 工作流的完整过程。

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

运行此代码片段后，您将在 `output` 文件夹中找到一系列 `preview_page_1.png`、`preview_page_2.png` 等文件——每个文件对应原始 Excel 工作簿中的一个工作表。

## 常见问题与解决方案

| 问题 | 原因 | 解决方案 |
|-------|-------|-----|
| **未生成图像** | `getOutputPath` 返回无效目录 | 确保目标文件夹存在，或使用 `new File("output").mkdirs();` 创建 |
| **大文件导致内存不足错误** | 一次性加载整个工作簿 | 使用流式方式（如示例所示），一次处理一页 |
| **DPI 不正确** | `setDpi` 未调用或设置为默认值（96） | 在 `generatePreview` 之前调用 `previewOptions.setDpi(yourDesiredValue);` |
| **不支持的格式** | 尝试预览损坏的 `.xlsx` 文件 | 使用 Excel 验证文件或在处理前调用 `Parser.isSupported` |

## 常见问题

**Q: 我可以使用 GroupDocs.Parser 为 PDF 和图像生成预览吗？**  
**A:** 是的，同一 API 可用于 PDF、Word 文档和多种图像格式。

**Q: 我如何更改输出图像格式？**  
**A:** 调用 `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`（或 `Gif`、`Bmp` 等）。

**Q: 对于非常大的工作簿，性能是否是个问题？**  
**A:** SDK 采用流式处理页面，保持低内存使用。对于超大文件，考虑并行批处理。

**Q: 我如何处理预览生成过程中的错误？**  
**A:** 将代码放在 try‑catch 块中（如示例所示），并记录异常细节。如果不使用 try‑with‑resources，请在 `finally` 块中关闭流。

**Q: 该库是否需要安装 Microsoft Office？**  
**A:** 不需要。GroupDocs.Parser 是纯 Java 解决方案，可在任何支持 Java 8+ 的平台上运行。

**最后更新：** 2026-07-16  
**测试版本：** GroupDocs.Parser 23.11（撰写时最新）  
**作者：** GroupDocs

## 相关教程

- [如何生成预览 – GroupDocs.Parser Java 文档页面预览生成教程](/parser/java/page-preview-generation/)
- [使用 GroupDocs.Parser 解析 Excel Java：完整指南](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [使用 GroupDocs.Parser for Java 从 Excel 表格提取原始文本：逐步指南](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)