---
date: '2026-08-05'
description: 了解如何使用 GroupDocs.Parser for Java 从 Word 文档中提取图像，并高效地将 Word 图像保存为 PNG
  格式。
keywords:
- extract images from word
- how to extract images
- extract images from docx
- extract pictures from word
- convert word images png
lastmod: '2026-08-05'
og_description: 使用 GroupDocs.Parser for Java 提取 Word 文档中的图像。逐步了解如何提取图片并高效地将 Word 图像保存为
  PNG。
og_image_alt: Code example showing image extraction from a Word document using GroupDocs.Parser
  for Java
og_title: 使用 GroupDocs.Parser for Java 从 Word 中提取图像
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
title: 使用 GroupDocs.Parser for Java 从 Word 中提取图像
type: docs
url: /zh/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

# 使用 GroupDocs.Parser for Java 从 Word 中提取图像

手动从 Word 文件中提取图像既耗时又容易出错。在本教程中，您将了解如何使用 GroupDocs.Parser for Java 自动 **从 word 中提取图像**，并随后 **保存 word 图像为 png** 以供后续处理。您将清晰了解该库为何快速、如何设置以及最佳实践技巧，帮助您将图像提取嵌入任何 Java 应用程序。

## 快速答案
- **库的作用是什么？** 它解析 Word、PDF 以及许多其他格式，以提供文本、表格和图像。  
- **代码行数是多少？** 大约 30 行 Java 代码，加上一些配置行。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要完整许可证。  
- **我可以提取嵌入的图像吗？** 可以——`getImages()` 方法返回所有嵌入的图像。  
- **支持的输出格式？** 默认是 PNG，但可以通过 `ImageFormat` 使用其他格式。  

## 什么是“从 word 中提取图像”？
从 word 中提取图像是指以编程方式检索 Microsoft Word 文档中嵌入的所有图片文件。GroupDocs.Parser 读取 DOCX 或 DOC 文件的二进制结构，并将每个图像呈现为 `PageImageArea` 对象，使您无需在 Microsoft Word 中打开文档即可提取所有图片。此方法消除手动复制粘贴，降低人为错误，并能在批处理作业中扩展到数千个文件。

## 为什么使用 GroupDocs.Parser for Java？
您可以使用 **速度**、**可靠性** 和 **跨平台灵活性** 从 Word 文档中提取图像。GroupDocs.Parser 在标准的 2 CPU 服务器上可在 2 秒内处理 200 页的 DOCX，并且在 Windows、Linux 和 macOS 上均可运行，无需 Microsoft Office。该库还能够容忍损坏的文件，返回仍可访问的图像，这使其非常适合大规模迁移项目。

## 先决条件
- **GroupDocs.Parser for Java**（版本 25.5 或更高）  
- **JDK 8+** 已在您的开发机器上安装  
- IDE（如 IntelliJ IDEA、Eclipse 或 NetBeans）用于编辑和运行代码  

## 设置 GroupDocs.Parser for Java
将库添加到您的 Maven 项目中：

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

或者，直接从 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下载最新版本。

### 许可证获取步骤
- **免费试用：** 开始使用免费试用以探索功能。  
- **临时许可证：** 如有需要，可获取临时许可证以进行更长时间的测试。  
- **购买：** 获取完整许可证用于生产部署。

## 实现指南
下面是完整的、可直接运行的 Java 代码，**从 word 中提取图像** 并将其保存为 PNG 文件。

### 步骤 1：初始化解析器
`Parser` 类是读取文档的入口点。它将文件加载到内存中，并准备好所有内容流以供提取。

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### 步骤 2：提取图像
`PageImageArea` 对象表示文档中找到的每张图片，无论图像是内联、浮动还是形状的一部分。

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### 步骤 3：配置图像选项
`ImageOptions` 允许您在保存每张图片之前指定输出格式、分辨率和其他渲染设置。

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### 步骤 4：保存每张图像
`ImageFormat` 枚举定义了输出图像格式，如 PNG、JPEG 或 BMP。  
`save` 方法将二进制图像数据写入磁盘文件。通过传递 `ImageFormat.Png`，即可满足 **save word images png** 的需求。

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### 步骤 5：定义路径辅助方法
实用方法简化了路径处理，使主提取逻辑保持简洁且易于维护。

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

将 `YOUR_DOCUMENT_DIRECTORY` 和 `YOUR_OUTPUT_DIRECTORY` 替换为您实际使用的文件系统路径。

## 如何从 docx 中提取嵌入的图像？
`getImages()` 方法返回一个 `PageImageArea` 对象集合，代表每个嵌入的图像。  
使用 `new Parser("input.docx")` 加载 DOCX 并调用 `parser.getImages()` ——该方法会自动返回所有嵌入的图像，包括内联图片、浮动形状和 VML 绘图。无需额外的 API 调用，您可以直接遍历返回的集合并处理每个 `PageImageArea`。

## 如何从 docx 中提取图像并保存为 PNG？
创建 `ImageOptions` 实例，设置 `options.setImageFormat(ImageFormat.Png)`，并将其传递给 `image.save(outputPath, options)`。此配置确保每个提取的图片以 PNG 文件写入，满足 **save word images png** 的目标，同时保留原始分辨率和色彩深度。

## 实际应用
1. **内容管理：** 将遗留 Word 文件中的图像提取出来，用于数字资产库。  
2. **数据迁移：** 将嵌入的图形迁移到新 CMS，无需手动复制粘贴。  
3. **文档归档：** 将图像单独存储，以减少归档大小并提升可搜索性。  
4. **自动化发布：** 将提取的 PNG 直接供网页生成器或电子邮件模板使用。  

## 性能考虑因素
- **内存使用：** 处理大文档时至少分配 `-Xmx2g`；解析器会流式处理数据以保持堆占用低。  
- **批处理：** 在循环中对每个文档复用单个 `Parser` 实例，以最小化对象创建开销。  
- **文件句柄：** try‑with‑resources 块确保解析器及时关闭，防止描述符泄漏。  

## 常见问题及解决方案
| 问题 | 解决方案 |
|-------|----------|
| **OutOfMemoryError** on huge DOCX files | 增加 JVM 堆内存或将文档分成更小的批次处理。 |
| **No images returned** | 确认文档确实包含嵌入的图像；某些“图片”是 VML 绘图，未以图像形式暴露。 |
| **Incorrect image orientation** | 某些 DOCX 图像存储了 EXIF 旋转信息；如有需要，可使用图像库进行后处理。 |

## 常见问题
**Q: GroupDocs.Parser 支持哪些文件格式的图像提取？**  
A: 它支持 DOC、DOCX、PDF、PPT、PPTX 以及许多其他格式，通过相同的 `getImages()` 方法暴露图像。

**Q: 我能从受密码保护的 Word 文件中提取图像吗？**  
A: 可以——将密码传递给 `Parser` 构造函数，库将在提取前解密文档。

**Q: 是否可以只提取特定类型的图像（例如仅 JPEG）？**  
A: 在获取 `PageImageArea` 对象后，检查 `image.getFormat()` 并在保存前进行相应过滤。

**Q: 该库支持异步处理吗？**  
A: 虽然核心 API 是同步的，但您可以将提取逻辑包装在单独的线程中，或使用 Java 的 `CompletableFuture` 实现并行处理。

**Q: 生产环境使用是否需要商业许可证？**  
A: 免费试用适用于评估，但商业部署需要付费许可证。

---

**最后更新：** 2026-08-05  
**测试版本：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

**资源**
- **文档：** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)  
- **API 参考：** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)  
- **下载：** [Latest Release](https://releases.groupdocs.com/parser/java/)  
- **GitHub：** [Source code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **免费支持：** [GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **临时许可证：** [Obtain a temporary license](https://purchase.groupdocs.com/temporary-license/)

## 相关教程
- [如何使用 GroupDocs.Parser for Java 保存图像](/parser/java/image-extraction/extract-images-groupdocs-parser-java/)
- [如何在 Java 中使用 GroupDocs.Parser 从 PDF 提取图像：分步指南](/parser/java/image-extraction/extract-images-pdf-groupdocs-parser-java/)
- [如何在 Java 中使用 GroupDocs.Parser 从 Word 文档提取文本](/parser/java/text-extraction/extract-text-word-docs-groupdocs-parser-java/)