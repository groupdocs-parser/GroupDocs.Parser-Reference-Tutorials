---
title: 按目录 (TOC) 项目提取文本
linktitle: 按目录 (TOC) 项目提取文本
second_title: GroupDocs.Parser .NET API
description: 使用 GroupDocs.Parser for .NET 按目录 (TOC) 提取文本。了解用于结构化数据提取的高效文档解析技术。
weight: 15
url: /zh/net/text-extraction/extract-text-by-toc-item/
---

# 按目录 (TOC) 项目提取文本

## 介绍
在本教程中，我们将探讨如何利用 GroupDocs.Parser for .NET 从文档中提取基于目录 (TOC) 项的文本。GroupDocs.Parser 是一个功能强大的工具，可以高效地解析和提取文档。
## 先决条件
在继续本教程之前，请确保您满足以下先决条件：
1. Visual Studio：在您的系统上安装 Visual Studio IDE。
2.  GroupDocs.Parser for .NET：从以下网址下载并安装 GroupDocs.Parser for .NET[这里](https://releases.groupdocs.com/parser/net/).
3. 带有目录的示例文档：准备一个包含目录的文档（例如 PDF、DOCX）。

## 导入命名空间
首先，在你的 C# 项目中包含必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## 步骤 1：创建解析器类的实例
实例化`Parser`类与示例文档的路径：
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    //继续此处的后续步骤...
}
```
## 第 2 步：提取目录 (TOC)
从文档中获取目录 (TOC) 项目：
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## 步骤 3：迭代目录项并提取文本
遍历每个目录项并提取相应的文本：
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 结论
本教程演示了如何使用 GroupDocs.Parser for .NET 根据目录 (TOC) 项从文档中提取文本。通过遵循概述的步骤，您可以高效地以编程方式解析和提取文档中的特定内容。

## 常见问题解答
### GroupDocs.Parser 支持哪些文件格式？
GroupDocs.Parser 支持多种文档格式，包括 PDF、Microsoft Word (DOC/DOCX)、Excel (XLS/XLSX)、PowerPoint (PPT/PPTX) 等。
### 我可以使用 GroupDocs.Parser 提取表格或图像等结构化数据吗？
是的，GroupDocs.Parser 提供 API 来从各种文档类型中提取结构化数据，如表格、图像和元数据。
### GroupDocs.Parser 是否适合大型文档？
GroupDocs.Parser 经过优化，可有效处理大型文档，从而能够从大量文件无缝提取内容。
### 如何获得 GroupDocs.Parser 的技术支持？
您可以在以下位置寻求技术支持并与社区互动[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).
### GroupDocs 是否提供免费试用评估？
是的，您可以从以下网址下载 GroupDocs.Parser 的免费试用版[这里](https://releases.groupdocs.com/).