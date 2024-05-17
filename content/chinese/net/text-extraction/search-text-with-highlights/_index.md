---
title: 突出显示搜索文本
linktitle: 突出显示搜索文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 搜索和突出显示文档中的文本。高效提取有价值的见解。
type: docs
weight: 24
url: /zh/net/text-extraction/search-text-with-highlights/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 在文档中搜索文本并突出显示搜索结果。GroupDocs.Parser 是一个功能强大的库，可让您处理各种文档格式并提取文本、元数据等。
## 先决条件
在开始之前，请确保您已准备好以下物品：
1.  GroupDocs.Parser for .NET：从以下网址下载并安装该库[这里](https://releases.groupdocs.com/parser/net/).
2. IDE：使用 Visual Studio 或任何首选 IDE 进行 .NET 开发。
3. 示例文件：准备一个示例文档（例如 PDF、DOCX）以进行文本搜索。

## 导入命名空间
首先，在您的 .NET 项目中导入必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器实例
首先实例化`Parser`类以及示例文件的路径：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //您的代码在这里
}
```
## 第 2 步：定义突出显示选项
指定`HighlightOptions`配置搜索结果的突出显示方式。例如，设置 15 个字符的上下文窗口：
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## 步骤 3：搜索文本
现在，在文档中执行文本搜索。提供要搜索的关键字（例如“lorem”）：
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## 步骤 4：处理搜索结果
遍历搜索结果并显示找到的文本以及突出显示的内容：
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## 结论
在本教程中，您学习了如何使用 GroupDocs.Parser for .NET 在文档中搜索文本并突出显示搜索结果。此功能对于 .NET 应用程序中的文本提取和分析非常有用。

## 常见问题解答
### GroupDocs.Parser 是否适合处理各种文档格式？
是的，GroupDocs.Parser 支持多种文档格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Parser 从文档中提取元数据吗？
当然！GroupDocs.Parser 允许您从文档中提取元数据、文本和结构化数据。
### 在哪里可以找到支持或询问有关 GroupDocs.Parser 的问题？
您可以访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17)对于任何与支持相关的疑问。
### GroupDocs.Parser 有免费试用版吗？
是的，您可以访问[免费试用](https://releases.groupdocs.com/) GroupDocs.Parser 来评估其功能。
### 如何购买 GroupDocs.Parser 的许可证？
您可以从购买许可证[这里](https://purchase.groupdocs.com/buy)并获得临时执照[这里](https://purchase.groupdocs.com/temporary-license/).