---
title: 以原始模式从 PDF 页面中提取文本
linktitle: 以原始模式从 PDF 页面中提取文本
second_title: GroupDocs.Parser .NET API
description: 使用 C# 中的 GroupDocs.Parser 从 PDF 中提取文本。学习如何使用这个强大的 .NET 库高效地提取 PDF 文本。
weight: 16
url: /zh/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Parser for .NET 使用原始模式从 PDF 文档中的页面中提取文本。GroupDocs.Parser 是一个功能强大的工具，使开发人员能够以编程方式处理各种文档格式。
## 先决条件
在开始本教程之前，请确保您已具备以下条件：
- 您的机器上安装了 Visual Studio。
- C# 编程的基本知识。
- GroupDocs.Parser for .NET 库，您可以[在这里下载](https://releases.groupdocs.com/parser/net/).
- 用于测试目的的示例 PDF 文件。

## 导入命名空间
首先，确保在 C# 项目中导入必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器类的实例
首先，实例化`Parser`通过提供示例 PDF 文件的路径来类。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //您的代码在此处
}
```
## 步骤 2：获取文档信息并迭代页面
接下来，检索文档信息并遍历每一页以提取文本。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //您的文本提取代码放在此处
}
```
## 步骤 3：从每个页面提取文本
在循环内，使用`GetText`方法从每一页提取文本并打印。
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Parser for .NET 从原始模式下的 PDF 页面中提取文本。此过程涉及创建`Parser`实例，获取文档信息，遍历每一页，并使用`GetText`方法。

## 常见问题解答
### 什么是适用于 .NET 的 GroupDocs.Parser？
GroupDocs.Parser for .NET 是一个文档解析 API，允许开发人员以编程方式从各种文件格式中提取文本、元数据和其他信息。
### 如何下载适用于 .NET 的 GroupDocs.Parser？
您可以从[GroupDocs 网站](https://releases.groupdocs.com/parser/net/).
### 有免费试用吗？
是的，您可以从以下网址免费试用 GroupDocs.Parser for .NET[这里](https://releases.groupdocs.com/).
### 在哪里可以找到对 .NET 的 GroupDocs.Parser 的支持？
如需技术协助和社区支持，请访问[GroupDocs 论坛](https://forum.groupdocs.com/c/parser/17).
### 如何购买 GroupDocs.Parser for .NET 许可证？
您可以从[购买页面](https://purchase.groupdocs.com/buy)或获取临时执照[这里](https://purchase.groupdocs.com/temporary-license/).