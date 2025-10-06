---
title: 从文档页面中提取格式化文本
linktitle: 从文档页面中提取格式化文本
second_title: GroupDocs.Parser .NET API
description: 使用 GroupDocs.Parser for .NET 从文档页面中提取格式化文本。高效可靠的文本提取解决方案。
weight: 11
url: /zh/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# 从文档页面中提取格式化文本

## 介绍
在本教程中，我们将指导您使用 GroupDocs.Parser for .NET 从文档页面中提取格式化文本的过程。此库允许您有效地解析和提取各种文档格式（如 PDF、Word、Excel 等）中的文本。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- 您的系统上安装了 Visual Studio。
- C# 编程的基本知识。
-  GroupDocs.Parser for .NET 库。您可以下载它[这里](https://releases.groupdocs.com/parser/net/).

## 导入命名空间
首先，将必要的命名空间导入到您的 C# 项目中。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器类的实例
首先创建一个实例`Parser`通过提供示例文件的路径来添加类。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //代码将放在这里
}
```
## 步骤 2：检查是否支持格式化文本提取
在继续文本提取之前，请验证文档是否支持格式化文本提取。
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## 步骤 3：获取文档信息
检索有关文档的信息，例如页数。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 步骤 4：遍历文档页面并提取格式化文本
遍历文档的每一页并使用指定的选项（例如 Markdown 格式）提取格式化的文本。
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 结论
现在您知道如何使用 GroupDocs.Parser for .NET 从文档页面中提取格式化文本。此库为从各种文件格式中提取文本提供了强大且易于使用的解决方案。

## 常见问题解答
### GroupDocs.Parser 能处理不同的文件格式吗？
是的，GroupDocs.Parser 支持多种文档格式，包括 PDF、DOCX、XLSX、PPTX 等。
### GroupDocs.Parser 是否与 .NET Core 兼容？
是的，GroupDocs.Parser 支持.NET Core 和 .NET Framework。
### GroupDocs.Parser 在提取过程中是否保留文本格式？
是的，GroupDocs.Parser 在提取文本时可以保留样式和字体等格式。
### 我可以使用 GroupDocs.Parser 提取图像和元数据吗？
是的，GroupDocs.Parser 允许从文档中提取图像、元数据和文本。
### 如何获得 GroupDocs.Parser 的支持？
您可以从[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).