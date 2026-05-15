---
date: '2026-02-09'
description: 学习如何使用 OCR 在 Java 中通过 GroupDocs.Parser 从图像和文档中提取文本。本指南涵盖设置、Java 图像转文本的转换以及实现高效文档处理的实际案例。
keywords:
- OCR Text Extraction
- GroupDocs.Parser Java
- Java OCR Integration
title: 如何在 GroupDocs.Parser Java 中使用 OCR：从图像和文档中提取文本
type: docs
url: /zh/java/ocr-integration/ocr-text-extraction-groupdocs-parser-java/
weight: 1
---

# 如何在 GroupDocs.Parser Java 中使用 OCR

您是否希望高效地从图像或扫描文档中提取文本？使用 GroupDocs.Parser Java 库的 **如何使用 OCR** 提供了强大的解决方案，使光学字符识别（OCR）能够无缝集成到您的应用程序中。本综合指南将引导您使用 Aspose OCR 连接器与 GroupDocs.Parser 在 Java 中从图像文件中提取文本区域，提升文档处理能力。

**您将学习**
- 设置并使用 GroupDocs.Parser for Java。
- `ParserSettings` 初始化与 OCR 连接器。
- 使用 Aspose OCR 技术从图像中提取文本区域的技术。
- 此功能在实际场景中的应用，例如 **java image to text** 转换和在 Java 中提取文本位置。

## 快速答案
- **“how to use OCR” 是什么意思？** 它指的是集成 OCR 引擎以读取基于图像的文件中的文本。  
- **哪个库为 Java 提供 OCR？** GroupDocs.Parser 与 Aspose OCR 连接器相结合。  
- **我需要许可证吗？** 提供免费试用；生产环境需要永久许可证。  
- **我可以获取文本坐标吗？** 可以，API 返回文本区域的位置（左、上、宽、高）。  
- **需要哪个 Java 版本？** 推荐使用 Java 8 或更高版本。

## 什么是 OCR 文本提取？

光学字符识别（OCR）将可视文本——出现在扫描图像、PDF 或照片中——转换为机器可读的字符。当您在 Java 中 **如何使用 OCR** 时，便使您的应用程序能够搜索、编辑和分析先前静态的文档。

## 为什么在 OCR 中使用 GroupDocs.Parser？

- **统一的 API** – 使用单一代码库处理 PDF、图像及许多其他格式。  
- **精准识别** – 由 Aspose OCR 提供支持，支持多种语言和字体。  
- **位置信息** – 获取每个文本块的精确坐标，适用于布局感知的处理。  
- **可扩展** – 适用于小图像或大批量作业，可在本地或云端运行。

## 前提条件

在开始之前，请确保您具备以下条件：

### 必需的库和依赖项
- **GroupDocs.Parser for Java**：版本 25.5 或更高。  
- **Maven** 或直接下载方式用于库的安装。  
- **Aspose OCR Connector**：需要访问 Aspose 的 OCR 技术。

### 环境设置要求
- 兼容的 IDE（IntelliJ IDEA、Eclipse 等），运行在 Java 8+ 上。  
- 如果您偏好 Maven 仓库方式，需要已安装 Maven。

### 知识前提
- 基础的 Java 编程技能。  
- 熟悉项目依赖的处理。

## 设置 GroupDocs.Parser for Java

您可以通过 Maven 添加库或直接下载。

### 使用 Maven

在您的 `pom.xml` 文件中添加以下配置：

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

### 直接下载

或者，从 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下载最新版本。

#### 许可证获取步骤
- **免费试用** – 免费评估该库。  
- **临时许可证** – 使用限时密钥进行扩展测试。  
- **购买** – 获取完整许可证用于生产部署。

### 基本初始化和设置

库可用后，您可以初始化解析器。下面是创建带有 Aspose OCR 连接器的 `ParserSettings` 实例的关键 Java 代码：

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.ParserSettings;
import com.groupdocs.parser.ocr.AsposeOcrOnPremise;

ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

基本完成后，让我们深入提取 OCR 文本区域。

## 如何使用 OCR 提取文本区域（逐步）

### 1. 使用 OCR 连接器初始化 `ParserSettings`

OCR 连接器使得在仅包含图像的文档中识别文本成为可能。

```java
// Initialize ParserSettings with OCR Connector
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```

### 2. 打开文档并配置提取选项

我们使用 `PageTextAreaOptions` 告诉解析器返回每个识别单词的位置信息。

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

#### 代码功能说明
- **创建** 指向您文档文件夹的 `Parser` 实例。  
- **启用** 通过 `PageTextAreaOptions(true)` 的 OCR。  
- **遍历** 每个 `PageTextArea`，为您提供识别的文本 **以及** 其精确矩形（位置和尺寸）。  
- **允许** 您存储或操作这些数据，例如插入数据库或在 UI 上叠加显示。

### 3. 处理结果

现在您可以将提取的文本和坐标用于各种场景：

- **文档数字化** – 将扫描的合同转换为可搜索的 PDF。  
- **数据录入自动化** – 直接从收据图像中提取发票号码等字段。  
- **内容管理** – 为高级搜索高亮建立文本位置索引。

## 常见问题及解决方案

| 症状 | 可能原因 | 解决方案 |
|---------|--------------|-----|
| 未返回文本区域 | OCR 连接器未配置或图像路径不正确 | 验证 `AsposeOcrOnPremise` 实例已正确授权且文件路径可访问。 |
| 字符乱码 | 图像质量低或语言不受支持 | 使用更高分辨率的扫描并配置 OCR 语言包。 |
| 大 PDF 处理时内存不足错误 | 一次处理大量高分辨率页面 | 分批处理页面或启用流模式（`ParserSettings.setEnableStreaming(true)`）。 |

## 常见问题

**问：如何安装 GroupDocs.Parser for Java？**  
答：将其添加为 Maven 依赖（参见上面的 XML 代码片段）或直接从官方发布页面下载。

**问：什么是 Aspose OCR，为什么要与 GroupDocs.Parser 一起使用？**  
答：Aspose OCR 是高精度的文本识别引擎。与 GroupDocs.Parser 配合使用，可扩展解析器的功能，以处理仅图像文件并提供精确的文本位置。

**问：我可以处理多种图像格式吗？**  
答：可以。GroupDocs.Parser 支持 JPEG、PNG、BMP、TIFF 等格式——只需确保 OCR 连接器能够读取该格式。

**问：如果未提取到文本区域该怎么办？**  
答：检查文件路径，确认 OCR 连接器已授权，并验证文档类型是否受 Aspose OCR 支持。

**问：在哪里可以找到更多关于 GroupDocs.Parser 的资源？**  
答：访问 [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) 获取详细指南和 API 参考。

## 资源
- [文档](https://docs.groupdocs.com/parser/java/)
- [API 参考](https://reference.groupdocs.com/parser/java)
- [下载最新版本](https://releases.groupdocs.com/parser/java/)
- [GitHub 仓库](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/parser)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

探索这些资源，以加深理解并在项目中扩展 GroupDocs.Parser 的功能。

---

**最后更新：** 2026-02-09  
**测试环境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs