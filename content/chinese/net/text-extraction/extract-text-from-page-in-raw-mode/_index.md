---
title: 以原始模式从页面提取文本
linktitle: 以原始模式从页面提取文本
second_title: GroupDocs.Parser .NET API
description: 在本综合教程中学习如何使用 Groupdocs.Parser for .NET 从文档页面中进行有效的文本提取。
weight: 17
url: /zh/net/text-extraction/extract-text-from-page-in-raw-mode/
type: docs
---
# 以原始模式从页面提取文本

## 介绍
在本教程中，您将学习如何使用 Groupdocs.Parser for .NET 以原始模式从文档页面中提取文本。此库提供了有效的工具来解析和提取各种文件格式的内容，使开发人员能够将文档文本提取合并到他们的 .NET 应用程序中。
## 先决条件
开始之前，请确保您满足以下先决条件：
- 具备 C# 和 .NET 编程基础知识
- 您的机器上安装了 Visual Studio
- 访问 Groupdocs.Parser for .NET 库
- 用于测试的示例文档文件

## 导入命名空间
首先在 C# 项目中包含必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：初始化解析器
首先，创建一个实例`Parser`通过提供示例文档文件的路径来类。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //您的代码在这里
}
```
## 第 2 步：检索文档信息
使用以下方法检索有关文档的信息`GetDocumentInfo()`方法。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 步骤 3：遍历页面并提取文本
遍历文档的每一页并提取文本内容。
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //从页面中提取文本
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 结论
您现在已经了解了如何使用 Groupdocs.Parser for .NET 以原始模式从文档页面中提取文本。对于需要分析或处理各种文件格式的文本内容的应用程序来说，这可能是一项强大的功能。

## 常见问题解答
### Groupdocs.Parser for .NET 是否兼容所有文件格式？
Groupdocs.Parser 支持多种文件格式，包括 PDF、DOCX、XLSX、PPTX、EPUB 等。
### 我可以使用该库提取元数据和文本吗？
是的，Groupdocs.Parser 允许您从文档中提取文本和元数据。
### 是否有可供测试的试用版？
是的，你可以从以下网站下载免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 Groupdocs.Parser 的技术支持？
如需技术帮助，请访问[Groupdocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).
### 我可以在哪里购买 Groupdocs.Parser for .NET 的许可证？
您可以购买许可证[这里](https://purchase.groupdocs.com/buy).