---
date: '2026-10-12'
description: 了解如何在 Java 中使用 GroupDocs.Parser 从 PDF 中提取 QR，并将 barcode 数据导出为 XML 以进行下游处理。
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: 了解如何在 Java 中使用 GroupDocs.Parser 从 PDF 中提取 QR，并将 barcode 数据导出为 XML
  以进行下游处理。
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: 如何在 Java 中使用 GroupDocs.Parser 从 PDF 中提取 QR
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: 如何在 Java 中使用 GroupDocs.Parser 从 PDF 中提取 QR
type: docs
url: /zh/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Parser 从 PDF 中提取 QR

在现代业务工作流中，**提取 PDF 中的 QR** 文件可以将手动数据录入的瓶颈转变为全自动化流水线。无论您处理的是装运清单、零售收据还是产品目录，快速且可靠地获取 QR 信息对下游系统至关重要。本教程将指导您使用 **GroupDocs.Parser for Java** 从 PDF 中读取 QR 码（以及其他条形码），并将结果导出为干净的 XML 文件，供您的 ERP、库存或分析平台使用。

## 快速答案
- **GroupDocs.Parser for Java 的作用是什么？** 它读取 PDF 文件并提取结构化数据，如条形码、表格和文本。  
- **如何提取 QR 码？** 使用 `BarcodeOptions` 配置 QR 类型并调用 `parser.getBarcodes()`。  
- **我可以在 Java 中读取 QR 码吗？** 可以——在选项中将条形码类型设为 `"QR"`。  
- **我需要许可证吗？** 试用版可用于测试；生产环境需要商业许可证。  
- **需要哪个 Java 版本？** 推荐使用 Java 8 或更高版本。

## 在 PDF 处理上下文中，“提取 PDF 中的 QR” 是什么？
提取 PDF 中的 QR 意味着扫描每一页的 QR 编码图形，解码嵌入的数据，并以程序友好的格式返回。GroupDocs.Parser 抽象了底层图像分析，让您可以专注于业务逻辑，而无需处理像素级操作。

## 为什么使用 GroupDocs.Parser 进行 QR 提取？
GroupDocs.Parser 支持 **30 多种输入格式**，并且能够在不将整个文件加载到内存中的情况下处理高达 **500 MB** 的 PDF，即使在低分辨率扫描下也能提供高精度结果。您可以选择 `QualityMode.Low` 以提升速度，或 `QualityMode.High` 以获得最高精度，同一套 API 适用于 PDF、图像和 Office 文档，免除使用多个库的需求。

## 前提条件
- **GroupDocs.Parser for Java**（版本 25.5 或更高）。  
- Maven 或手动 JAR 下载。  
- Java 8+ 开发环境（IntelliJ IDEA、Eclipse 或任意编辑器）。  

## 设置 GroupDocs.Parser for Java
### 使用 Maven
将 GroupDocs 仓库和依赖添加到您的 `pom.xml`：

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
或者，从 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下载最新的 JAR。

#### 许可证获取步骤
- **免费试用：** 30 天完整功能试用。  
- **临时许可证：** 请求临时密钥以进行扩展评估。  
- **购买：** 获取用于生产部署的商业许可证。

### 基本初始化和设置
创建指向要分析的 PDF 的 `Parser` 实例：

`Parser` 是 GroupDocs.Parser 中的核心类，表示文档并提供提取文本、表格和条形码等内容的方法。  

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

## 如何使用 GroupDocs.Parser 在 Java PDF 中读取 QR 码
使用 GroupDocs.Parser 读取 Java PDF 中的 QR 码涉及创建解析器实例、配置条形码选项以定位 QR 类型、调用条形码提取方法，然后处理返回的条形码对象。该过程简洁、适用于任何 PDF 页面，并返回解码值及其位置信息，以便后续处理。

### 步骤 1：验证条形码支持
在尝试提取之前，确认文档格式支持条形码扫描：

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*说明：* 此检查可防止在不支持的文件类型上出现运行时错误。

### 步骤 2：配置条形码选项（读取 Java 中的 QR 码）
`BarcodeOptions` 是一个配置对象，允许您指定要检测的条形码符号集、设置扫描质量模式，并微调检测阈值等参数，以确保针对目标 QR 码的最佳性能。  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*说明：* `QualityMode.Low` 加快处理速度；如果需要更高精度，可切换为 `High`。`"QR"` 参数指示引擎仅查找 QR 类型的条形码。

### 步骤 3：提取 QR 数据
`parser.getBarcodes(options)` 使用提供的 `BarcodeOptions` 扫描文档，并返回一组 `PageBarcodeArea` 对象，每个对象封装了解码后的 QR 值、页码以及条形码在页面内的精确坐标，便于精确的下游处理。  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*说明：* `parser.getBarcodes` 返回一个可迭代的 `PageBarcodeArea` 集合，每个对象包含解码后的 QR 值及其在页面上的位置。

## 将提取的数据导出为 XML
### 步骤 4：初始化 XML 导出器
`XmlExporter` 是一个实用类，可将条形码对象集合转换为结构良好的 XML 文档，自动为每个条形码生成带有页索引、位置和解码值属性的元素，随后可保存或流式传输至其他系统。  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*说明：* `XmlExporter` 负责将条形码对象序列化为标准 XML，便于与 ERP 或库存系统集成。

### 步骤 5：写入 XML 文件
将提取的 QR 信息保存到磁盘：

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*说明：* 生成的 `data.xml` 为每个 QR 码包含一个 `<Barcode>` 元素，属性包括页码、坐标和解码值。

## 实际应用
1. **库存管理：** 通过读取入库 PDF 中的 QR 标签自动填充库存数据库。  
2. **供应链可视化：** 通过提取物流文档中嵌入的 QR 标识实时跟踪包裹。  
3. **零售收据：** 从数字收据上打印的 QR 码中提取促销或保修信息。

## 性能考虑因素
- **内存管理：** 对于超大 PDF，采用流式方式逐页处理，而不是一次性加载整个文件到内存。  
- **QualityMode 选择：** 大批量处理使用 `Low`；处理低分辨率扫描时切换到 `High`。  
- **库更新：** 保持 GroupDocs.Parser 为最新版本，以获得最新的性能提升和错误修复。

## 常见问题与故障排除
| 症状 | 可能原因 | 解决方案 |
|------|----------|----------|
| 未返回条形码 | 指定的条形码类型错误 | 将 `"QR"` 更改为适当的类型（例如 `"CODE_128"`）。 |
| 大 PDF 导致内存不足错误 | 一次性加载整个文档 | 逐页处理或增加 JVM 堆大小（`-Xmx2g`）。 |
| XML 文件为空 | 在提取之前调用了 `exportBarcodes` | 确保在导出前 `parser.getBarcodes(options)` 已返回数据。 |

## 常见问答
**Q: 我可以在 GroupDocs.Parser 中从图像文件提取条形码吗？**  
A: 可以，库支持从常见图像格式（PNG、JPEG、TIFF）中提取条形码。

**Q: 识别哪些条形码格式？**  
A: 支持 QR、Code 39、Code 128、DataMatrix、PDF417 等多种格式。完整列表请参阅 API 文档。

**Q: 如何处理受密码保护的 PDF？**  
A: 将密码传递给 `Parser` 构造函数：`new Parser(filePath, "password")`。

**Q: 试用版足以进行生产测试吗？**  
A: 试用版提供完整功能，但会在提取的数据上添加水印。生产环境请获取商业许可证。

**Q: 如果我的 PDF 同时包含 QR 和线性条形码怎么办？**  
A: 创建多个 `BarcodeOptions` 实例，或传入类型数组一次性扫描所有所需格式。

---

**最后更新：** 2026-10-12  
**测试版本：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

## 资源
- [GroupDocs.Parser Java 文档](https://docs.groupdocs.com/parser/java/)
- [API 参考](https://reference.groupdocs.com/parser/java)
- [下载 GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub 仓库](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/parser)
- [临时许可证申请](https://purchase.groupdocs.com/temporary-license/)

## 相关教程

- [提取条形码 PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [如何使用 GroupDocs.Parser for Java 从 URL 加载 PDF](/parser/java/document-loading/)
- [使用 GroupDocs.Parser 在 Java 中提取 PDF 表单数据](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)