---
date: '2026-06-22'
description: 了解如何使用 GroupDocs.Parser for Java 获取格式。本指南向您展示如何检索受支持的文件格式并提升文档解析效率。
keywords:
- how to get formats
- GroupDocs.Parser Java
- supported file formats
- document parsing Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get formats with GroupDocs.Parser for Java. This guide
    shows you how to retrieve supported file formats and boost your document parsing
    efficiency.
  headline: How to Get Formats Using GroupDocs.Parser for Java
  type: TechArticle
- description: Learn how to get formats with GroupDocs.Parser for Java. This guide
    shows you how to retrieve supported file formats and boost your document parsing
    efficiency.
  name: How to Get Formats Using GroupDocs.Parser for Java
  steps:
  - name: Import Required Classes
    text: '`FileType` is the entry point class that provides access to the library’s
      format catalog. Import it before you call any methods.'
  - name: Retrieve Supported File Types
    text: '`FileType.getSupportedFileTypes()` returns an `Iterable<FileType>` containing
      every format the parser recognises.'
  - name: Iterate and Print File Type Details
    text: Loop through each supported file type, printing its properties for verification.
      This helps you confirm that a given document’s extension is on the allowed list.
      **Explanation** - `getSupportedFileTypes()` returns an iterable collection of
      all formats GroupDocs.Parser can handle. - The iteration pri
  type: HowTo
- questions:
  - answer: GroupDocs.Parser aids in extracting data from various document formats,
      making it ideal for parsing tasks in Java applications.
    question: What is GroupDocs.Parser used for?
  - answer: Set up a simple Maven project with the GroupDocs.Parser dependency and
      run the provided code snippets.
    question: How can I test the supported file types feature locally?
  - answer: It supports a wide range of formats, but you should consult the latest
      documentation for the exact list.
    question: Does GroupDocs.Parser support all document formats?
  - answer: Yes, a free trial or temporary license lets you evaluate the library before
      buying.
    question: Can I use GroupDocs.Parser without purchasing a license?
  - answer: Explore the [API Reference](https://reference.groupdocs.com/parser/java)
      and official documentation for deeper functionality.
    question: Where can I find more advanced features of GroupDocs.Parser?
  type: FAQPage
title: 如何使用 GroupDocs.Parser for Java 获取格式
type: docs
url: /zh/java/document-information/groupdocs-parser-java-get-supported-file-formats-tutorial/
weight: 1
---

# 如何使用 GroupDocs.Parser for Java 获取格式

在本教程中，您将学习 **how to get formats**，即 GroupDocs.Parser for Java 支持的格式，这是在 Java 项目中处理多种文档时的关键步骤。该库提供了一种高效的方式，以编程方式检索所有受支持的文件格式。按照以下步骤操作，您将提升应用程序的兼容性，并在使用文档解析器时更加自信。

## 快速答案
`FileType` 是一个帮助类，公开了 GroupDocs.Parser 可以处理的文件格式目录。  

- **“how to get formats” 是什么意思？** 它指的是检索解析器能够处理的文件类型列表。  
- **哪个库提供此功能？** GroupDocs.Parser for Java 提供 `FileType.getSupportedFileTypes()` 方法。  
- **我需要许可证吗？** 免费试用可用于评估；生产环境需要商业许可证。  
- **需要 Maven 吗？** Maven 简化依赖管理，但您也可以直接下载 JAR。  
- **我可以过滤结果吗？** 可以——遍历集合并挑选所需的格式。

## 在 GroupDocs.Parser 中，“how to get formats” 是什么？
它是返回解析器能够处理的所有文件类型的操作，允许您以编程方式发现受支持的扩展名。  
该短语描述了查询解析器其支持的文档类型的过程。了解这些格式有助于您设计只接受兼容文件的稳健摄取管道。

## 为什么使用 GroupDocs.Parser for Java？
GroupDocs.Parser 支持 **50+ 输入和输出格式**——包括 PDF、DOCX、XLSX、PPTX、HTML、TXT 以及常见的图像类型——使其成为最通用的 Java 解析库之一。得益于低内存、高吞吐的引擎，它能够在普通服务器上在 2 秒内处理数百页的文档。当您需要零配置提取且无需为每种格式编写自定义解析器时，请使用它。

## 前提条件
- Java Development Kit (JDK) 8 或更高。  
- Maven 构建工具。  
- GroupDocs.Parser 库版本 25.5。  

## 为 Java 设置 GroupDocs.Parser

### 安装信息

**Maven**

将以下仓库和依赖添加到您的 `pom.xml` 文件中：

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

**直接下载**  
或者，从 [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) 下载最新版本。

### 获取许可证的步骤
要使用 GroupDocs.Parser：
- 通过下载库开始免费试用。  
- 通过 [Temporary License page](https://purchase.groupdocs.com/temporary-license/) 获取临时许可证，以探索全部功能。  
- 在生产环境中，从其官方网站购买商业许可证。

### 基本初始化和设置
安装完成后，通过导入必要的类来使用 GroupDocs.Parser 初始化您的项目：

```java
import com.groupdocs.parser.FileType;
```

## 如何使用 GroupDocs.Parser 获取格式
要检索格式列表，实例化解析器（或直接使用静态方法），并调用 `FileType.getSupportedFileTypes()`。该方法返回一个可迭代的 `FileType` 对象集合，代表每种受支持的格式。然后，您可以遍历此集合，根据应用需求显示或过滤扩展名。

### 检索受支持的文件格式

**概览**  
此功能使您能够识别所有可解析的文件类型，这对于构建灵活的文档处理管道至关重要。

#### 步骤 1：导入所需类
`FileType` 是入口类，提供对库的格式目录的访问。在调用任何方法之前请先导入它。

```java
import com.groupdocs.parser.FileType;
```

#### 步骤 2：检索受支持的文件类型
`FileType.getSupportedFileTypes()` 返回一个 `Iterable<FileType>`，其中包含解析器识别的每种格式。

```java
Iterable<FileType> supportedFileTypes = FileType.getSupportedFileTypes();
```

#### 步骤 3：遍历并打印文件类型详情
遍历每个受支持的文件类型，打印其属性以进行验证。这有助于您确认给定文档的扩展名是否在允许列表中。

```java
for (FileType fileType : supportedFileTypes) {
    System.out.println(fileType);
}
```

**说明**  
- `getSupportedFileTypes()` 返回 GroupDocs.Parser 能处理的所有格式的可迭代集合。  
- 迭代过程打印每种格式的属性，帮助您在处理文档前验证兼容性。

## 实际应用
以下是一些 **how to get formats** 特别有用的真实场景：

1. **文档管理系统** – 根据文件类型自动对导入文件进行分类。  
2. **数据提取工具** – 在尝试提取之前验证文件格式是否受支持。  
3. **云集成** – 在将文件与 AWS S3 或 Azure Blob Storage 等服务同步时确保兼容性。

## 性能考虑
为了保持 GroupDocs.Parser 平稳运行：

- 如果需要快速查找格式，请使用高效的数据结构（例如 `HashSet`）。  
- 及时释放资源；完成后关闭任何流或解析器。  

**内存管理最佳实践**  
- 定期对应用程序进行性能分析，以检测泄漏。  
- 将解析逻辑包装在 try‑with‑resources 块中，以确保清理。

## 常见问题及解决方案

| 问题 | 解决方案 |
|-------|----------|
| **调用 `getSupportedFileTypes()` 时出现 NullPointerException** | 确保在调用方法之前已正确加载库并应用许可证。 |
| **未列出意外的格式** | 确保您使用的是最新的库版本；新版本会添加格式支持。 |
| **大批量处理时性能下降** | 将受支持的格式列表缓存，而不是重复查询。 |

## 常见问题

**问：GroupDocs.Parser 的用途是什么？**  
答：GroupDocs.Parser 有助于从各种文档格式中提取数据，使其成为 Java 应用程序中解析任务的理想选择。

**问：如何在本地测试受支持的文件类型功能？**  
答：设置一个包含 GroupDocs.Parser 依赖的简单 Maven 项目，并运行提供的代码片段。

**问：GroupDocs.Parser 是否支持所有文档格式？**  
答：它支持广泛的格式，但您应查阅最新文档以获取完整列表。

**问：我可以在不购买许可证的情况下使用 GroupDocs.Parser 吗？**  
答：可以，免费试用或临时许可证让您在购买前评估该库。

**问：在哪里可以找到 GroupDocs.Parser 的更高级功能？**  
答：浏览 [API Reference](https://reference.groupdocs.com/parser/java) 和官方文档以获取更深入的功能。

## 资源
- [文档](https://docs.groupdocs.com/parser/java/)  
- [API 参考](https://reference.groupdocs.com/parser/java)  
- [下载 GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)  
- [GitHub 仓库](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- [免费支持论坛](https://forum.groupdocs.com/c/parser)  
- [临时许可证获取](https://purchase.groupdocs.com/temporary-license/)  

开启您的文档解析之旅，使用 GroupDocs.Parser 改变在 Java 应用中处理文件的方式！

---

**最后更新：** 2026-06-22  
**测试版本：** GroupDocs.Parser 25.5  
**作者：** GroupDocs

## 相关教程

- [GroupDocs.Parser Java 文档信息提取教程](/parser/java/document-information/)  
- [使用 GroupDocs.Parser for Java 在 ZIP 档案中检测文件类型](/parser/java/container-formats/detect-file-types-zip-groupdocs-parser-java/)  
- [Java 文档解析精通：GroupDocs.Parser 文本提取指南](/parser/java/text-extraction/mastering-document-parsing-groupdocs-parser-java/)