---
date: '2026-02-19'
description: 学习如何使用 GroupDocs.Parser 在 Java PDF 中读取 QR 码并将条形码数据导出为 XML。
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: 如何使用 GroupDocs.Parser 在 Java PDF 中读取二维码
type: docs
url: /zh/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

We need to translate headings content: e.g., "# How to Read QR Codes in Java PDFs with GroupDocs.Parser" -> "# 如何在 Java PDF 中读取 QR 码，使用 GroupDocs.Parser". Keep "GroupDocs.Parser" unchanged.

Proceed section by section.

Also tables: translate headers and cells.

Let's craft.

# 如何在 Java PDF 中读取 QR 码，使用 GroupDocs.Parser

在现代业务工作流中，**如何读取 QR** 码从 PDF 文档可以决定是手动数据录入的瓶颈还是全自动化的流水线。无论是处理装运清单、零售收据还是产品目录，快速且可靠地提取 QR 信息都是必不可少的。本教程将演示如何使用 **GroupDocs.Parser for Java** 从 PDF 中读取 QR 码（以及其他条形码），并将结果导出为干净的 XML 文件，以供下游系统使用。

## 快速答案
- **GroupDocs.Parser for Java 是做什么的？** 它读取 PDF 文件并提取结构化数据，如条形码。  
- **如何提取 QR 码？** 通过在 `BarcodeOptions` 中配置 QR 类型并调用 `parser.getBarcodes()`。  
- **我可以在 Java 中读取 QR 码吗？** 可以——在选项中将条形码类型设为 `"QR"`。  
- **需要许可证吗？** 试用版可用于测试；生产环境需要商业许可证。  
- **需要哪个 Java 版本？** 推荐使用 Java 8 或更高版本。

## 在 PDF 处理上下文中，“如何读取 QR” 是指什么？
从 PDF 中读取 QR 码意味着扫描每一页的 QR 编码图形，解码嵌入的数据，并以程序友好的格式返回。GroupDocs.Parser 抽象了底层图像分析，让你可以专注于业务逻辑，而不是像素操作。

## 为什么使用 GroupDocs.Parser 提取 QR？
- **高准确率：** 内置的图像处理算法能够处理低分辨率扫描。  
- **性能选项：** 可选择 `QualityMode.Low` 以提升速度，或 `QualityMode.High` 以获得最高精度。  
- **跨格式支持：** 支持 PDF、图像，甚至 Office 文档，因而可以复用同一代码库处理不同文件类型。

## 前置条件
- **GroupDocs.Parser for Java**（版本 25.5 或更高）。  
- Maven 或手动下载 JAR。  
- Java 8+ 开发环境（IntelliJ IDEA、Eclipse 或任意编辑器）。  

## 设置 GroupDocs.Parser for Java
### 使用 Maven
在 `pom.xml` 中添加 GroupDocs 仓库和依赖：

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
- **临时许可证：** 申请临时密钥以延长评估时间。  
- **购买：** 为生产部署获取商业许可证。

### 基本初始化和设置
创建指向待分析 PDF 的 `Parser` 实例：

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

## 如何在 Java PDF 中使用 GroupDocs.Parser 读取 QR 码
### 步骤 1：验证条形码支持
在尝试提取之前，确认文档格式支持条形码扫描：

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*说明：* 此检查可防止在不支持的文件类型上出现运行时错误。

### 步骤 2：配置条形码选项（在 Java 中读取 QR 码）
设置扫描质量并指定只关注 QR 码：

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*说明：* `QualityMode.Low` 可加快处理速度；如果需要更高精度，可切换为 `High`。`"QR"` 参数告诉引擎仅查找 QR 类型的条形码。

### 步骤 3：提取 QR 数据
从 PDF 的每一页获取条形码信息：

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*说明：* `parser.getBarcodes` 返回一个可迭代的 `PageBarcodeArea` 集合，每个对象包含已解码的 QR 值及其在页面上的位置。

## 将提取的数据导出为 XML
### 步骤 4：初始化 XML 导出器
创建一个导出器，将条形码集合转换为结构化的 XML 文件：

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

## 实际应用场景
1. **库存管理：** 通过读取入库 PDF 中的 QR 标签自动填充库存数据库。  
2. **供应链可视化：** 从物流文档中提取 QR 标识符，实现包裹实时追踪。  
3. **零售收据：** 从数字收据上的 QR 码获取促销或保修信息。

## 性能考虑因素
- **内存管理：** 对于超大 PDF，采用流式方式逐页处理，而不是一次性加载整个文件。  
- **QualityMode 选择：** 大批量处理时使用 `Low`；处理低分辨率扫描时切换为 `High`。  
- **库更新：** 保持 GroupDocs.Parser 为最新版本，以获得最新的性能提升和 bug 修复。

## 常见问题与故障排除
| 症状 | 可能原因 | 解决方案 |
|------|----------|----------|
| 未返回条形码 | 条形码类型设置错误 | 将 `"QR"` 改为相应的类型（例如 `"CODE_128"`）。 |
| 大 PDF 出现内存溢出 | 整个文档一次性加载 | 逐页处理或增大 JVM 堆大小（`-Xmx2g`）。 |
| 导出的 XML 为空 | 在提取之前调用了 `exportBarcodes` | 确保 `parser.getBarcodes(options)` 已返回数据后再导出。 |

## 常见问答
**问：我可以使用 GroupDocs.Parser 从图像文件中提取条形码吗？**  
答：可以，库支持从常见图像格式（PNG、JPEG、TIFF）中提取条形码。

**问：支持哪些条形码格式？**  
答：QR、Code 39、Code 128、DataMatrix、PDF417 等等。完整列表请参阅 API 文档。

**问：如何处理受密码保护的 PDF？**  
答：在 `Parser` 构造函数中传入密码，例如 `new Parser(filePath, "password")`。

**问：试用版能满足生产测试吗？**  
答：试用版提供全部功能，但会在提取的数据中添加水印。生产环境请获取商业许可证。

**问：如果我的 PDF 同时包含 QR 和线性条形码怎么办？**  
答：可以创建多个 `BarcodeOptions` 实例，或在一次扫描中传入包含所有需要类型的数组。

---

**最后更新：** 2026-02-19  
**测试环境：** GroupDocs.Parser 25.5  
**作者：** GroupDocs  

## 资源
- [GroupDocs.Parser Java 文档](https://docs.groupdocs.com/parser/java/)
- [API 参考](https://reference.groupdocs.com/parser/java)
- [下载 GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub 仓库](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/parser)
- [临时许可证申请](https://purchase.groupdocs.com/temporary-license/)