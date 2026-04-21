---
date: '2025-12-29'
description: 了解如何使用 GroupDocs.Parser for Java 从文档中提取图像以及如何过滤资源。本指南涵盖配置、自定义处理程序和实际示例。
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: 使用 GroupDocs.Parser Java 从文档中提取图像 – 指南
type: docs
url: /zh/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# 从文档中提取图像并使用 GroupDocs.Parser Java 过滤资源

从文档中提取图像是构建文档处理流水线时的常见需求。在本教程中，你将了解 **如何使用 GroupDocs.Parser for Java 提取文档中的图像**，并学习 **如何过滤资源**，只加载所需的文件。我们将演示如何设置库、创建自定义 `ExternalResourceHandler`，以及应用过滤逻辑以保持应用程序的高效和安全。

## 快速答案
- **GroupDocs.Parser 的作用是什么？** 它解析多种文档格式，并提供对文本、图像和其他嵌入资源的访问。  
- **我可以跳过不需要的图像吗？** 可以——通过实现自定义 `ExternalResourceHandler`，你可以决定加载哪些资源。  
- **需要哪个 Maven 版本？** 使用 GroupDocs.Parser Java 25.5 或更高版本。  
- **是否需要许可证？** 免费试用可用于评估；生产环境需要永久许可证。  
- **这种方式线程安全吗？** 解析对象不在多个线程之间共享；每个线程创建一个新的 `Parser` 实例。

## 什么是“从文档中提取图像”？
当文档包含嵌入的图片、图表或其他媒体时，“从文档中提取图像”指的是以编程方式检索这些二进制文件，以便在原始文件之外存储、显示或进一步处理它们。

## 为什么在提取图像时要过滤资源？
过滤资源可以帮助你：
- 通过忽略大型或不相关的文件来降低内存消耗。  
- 通过防止加载潜在不安全的内容来提升安全性。  
- 加快处理速度，尤其是处理包含大量嵌入对象的大型文档时。

## 前置条件

- **Java Development Kit (JDK)** – 版本 8 或更高。  
- **Maven** – 用于依赖管理。  
- 对 Java I/O 和异常处理有基本了解。

## 为 Java 设置 GroupDocs.Parser

将 GroupDocs 仓库和 parser 依赖添加到你的 `pom.xml`：

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

或者，从 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下载最新版本。

### 许可证获取
- **免费试用** – 免费探索核心功能。  
- **临时许可证** – 在评估期间解锁全部功能。  
- **购买许可证** – 商业部署所必需。

## 如何在提取图像时过滤资源

### 步骤 1：创建自定义处理器
定义一个继承自 `ExternalResourceHandler` 的类。在 `onLoading` 方法中决定保留哪些资源。

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

### 步骤 2：使用处理器配置 `ParserSettings`
将你的 `Handler` 实例传递给 `ParserSettings`，并在打开文档时使用它。

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

### 步骤 3：微调过滤逻辑
如果需要更复杂的规则——例如按图像大小、格式或 URI 模式过滤——请相应地扩展 `onLoading` 方法：

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## 实际应用场景

1. **文档管理系统** – 从扫描的合同中仅提取必要的图像以生成缩略图。  
2. **数据提取服务** – 跳过装饰性图形，专注于包含有价值数据的图表。  
3. **网页抓取工具** – 在检索基于 HTML 的文档时过滤掉跟踪像素，只保留有意义的媒体。

## 性能考虑
- **提前过滤**：在遍历资源之前应用自定义处理器，以避免将不需要的数据加载到内存中。  
- **及时释放**：使用 try‑with‑resources (`try (Parser parser = …)`) 释放本机资源。  
- **异步处理**：对于大批量文件，可在并行流中处理文档，同时确保每个 `Parser` 实例仅限单线程使用。

## 常见问题与解决方案
| 问题 | 原因 | 解决办法 |
|------|------|----------|
| 未返回图像 | 处理器不小心跳过了所有资源 | 检查 `if` 条件，确保仅对不需要的 URI 调用 `args.setSkipped(true)`。 |
| 大文件出现 `IOException` | 堆内存不足 | 增加 JVM 堆大小（`-Xmx2g`）或将页面分成更小的块处理。 |
| 许可证未被识别 | 在生产代码中使用了试用 DLL | 通过 `License.setLicense("path/to/license")` 正确设置许可证文件路径。 |

## 常见问答

**问：使用自定义 `ExternalResourceHandler` 的主要目的是什么？**  
答：它让你能够控制加载哪些外部资源，通过过滤不必要提升安全性和性能。

**问：可以在没有许可证的情况下使用 GroupDocs.Parser for Java 吗？**  
答：可以，免费试用可用，但某些高级功能在获取临时或正式许可证前可能受限。

**问：在使用 GroupDocs.Parser 解析时如何处理异常？**  
答：将解析调用包装在 `try‑catch` 块中，捕获 `IOException` 及其他特定异常，以优雅地处理错误。

**问：过滤资源时常见的陷阱有哪些？**  
答：URI 检查不当可能导致跳过所需文件；使用日志或断点验证你的条件。

**问：是否可以使用 GroupDocs.Parser for Java 解析非 HTML 文档？**  
答：完全可以——GroupDocs.Parser 支持 PDF、Word、Excel、PowerPoint 等多种格式。

## 后续步骤
通过浏览 [API Reference](https://reference.groupdocs.com/parser/java) 或尝试 `ParserSettings.setDetectTables(true)` 等额外设置（用于表格提取），进一步深入了解库的功能。

---

**最后更新：** 2025-12-29  
**测试环境：** GroupDocs.Parser 25.5 for Java  
**作者：** GroupDocs  

**资源**  
- **文档：** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API 参考：** [API Details](https://reference.groupdocs.com/parser/java)  
- **下载：** [Latest Versions](https://releases.groupdocs.com/parser/java/)