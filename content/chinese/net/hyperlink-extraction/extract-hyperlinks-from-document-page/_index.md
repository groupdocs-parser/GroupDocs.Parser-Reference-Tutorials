---
title: 从文档页面提取超链接
linktitle: 从文档页面提取超链接
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取超链接。使用 C# 进行超链接提取的分步指南。
weight: 11
url: /zh/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---

# 从文档页面提取超链接

## 介绍
在本教程中，我们将逐步探索如何使用 GroupDocs.Parser for .NET 从文档中提取超链接。GroupDocs.Parser 是一个功能强大的库，使开发人员能够解析各种文档格式并提取文本、元数据和其他元素。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- Visual Studio：在您的开发机器上安装 Visual Studio。
-  GroupDocs.Parser 库：下载并引用 GroupDocs.Parser 库。您可以从以下位置获取[这里](https://releases.groupdocs.com/parser/net/).
- 示例文档：准备一个包含超链接的示例文档（例如 DOCX、PDF）以供测试。

## 导入命名空间
首先，包含使用 GroupDocs.Parser 功能所需的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器实例
实例化`Parser`类与示例文档的路径。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //代码在这里...
}
```
## 步骤 2：检查超链接提取支持
在继续之前，请确保文档支持超链接提取。
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## 步骤 3：检索文档信息
获取文档的基本信息并检查其是否包含页面。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 步骤 4：迭代文档页面
遍历文档的每一页。
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //从当前页面提取超链接
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    //迭代提取的超链接
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); //为方便阅读，请留空一行
    }
}
```

## 结论
在本教程中，我们介绍了使用 GroupDocs.Parser for .NET 从文档中提取超链接的基础知识。您学习了如何初始化解析器、检查超链接支持、检索文档信息以及遍历文档页面以有效提取超链接。

## 常见问题解答
### 我可以从不同的文档格式中提取超链接吗？
是的，GroupDocs.Parser 支持各种格式，如 DOCX、PDF、PPTX 等，用于超链接提取。
### GroupDocs.Parser 是否易于集成到现有的 .NET 应用程序中？
当然，GroupDocs.Parser 的设计非常简单，可以轻松集成到您的 .NET 项目中。
### 我可以使用 GroupDocs.Parser 提取超链接以及其他元数据吗？
是的，除了超链接，您还可以使用此库从文档中提取文本、图像和元数据。
### GroupDocs.Parser 是否处理加密或受密码保护的文档？
如果提供了密码，GroupDocs.Parser 可以解析受密码保护的文档。
### 购买前是否有试用版可供测试？
是的，您可以下载免费试用版[这里](https://releases.groupdocs.com/).