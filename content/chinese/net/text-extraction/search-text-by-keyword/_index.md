---
title: 按关键字搜索文本
linktitle: 按关键字搜索文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 在文档中按关键字搜索文本。轻松高效地提取相关内容。
type: docs
weight: 21
url: /zh/net/text-extraction/search-text-by-keyword/
---
## 介绍
在本教程中，我们将深入研究如何使用 GroupDocs.Parser for .NET 在文档中按关键字搜索文本。GroupDocs.Parser 是一个功能强大的库，使开发人员能够从各种文件格式（如 PDF、Microsoft Office 文档等）中提取文本、元数据和其他信息。对于处理大量文本数据的应用程序来说，在这些文档中搜索特定关键字至关重要。
## 先决条件
在开始之前，请确保您已进行以下设置：
1. 开发环境：Visual Studio 或任何首选的 .NET IDE。
2.  GroupDocs.Parser for .NET：从以下网址下载该库[这里](https://releases.groupdocs.com/parser/net/).
3. 访问示例文件：准备一个示例文件（例如 PDF、DOCX）来测试关键字搜索功能。

## 导入命名空间
首先，您需要在项目中包含必要的命名空间。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 步骤 1：实例化解析器类
首先创建一个实例`Parser`类并提供示例文件的路径。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //搜索关键字
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    //迭代搜索结果
    foreach (SearchResult result in searchResults)
    {
        //打印索引和找到的文本
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## 第 2 步：搜索关键字
在`using`阻止，调用`Search`方法`parser`对象，将所需的关键字作为参数传递。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
代替`"test"`使用您想要在文档中搜索的关键字。
## 步骤 3：迭代搜索结果
接下来，迭代从`Search`方法使用`foreach`环形。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
对于每个`SearchResult`目的`result`，您可以访问其`Position`（索引）和`Text`（找到的文本）。

## 结论
在本教程中，我们探索了如何使用 GroupDocs.Parser for .NET 轻松地在文档中按关键字搜索文本。利用`Search`方法`Parser`该类允许根据特定搜索词有效检索相关文本片段。

## 常见问题解答
### GroupDocs.Parser 是否兼容各种文档格式？
是的，GroupDocs.Parser 支持多种文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Parser 执行高级文本提取操作吗？
当然！除了文本搜索之外，GroupDocs.Parser 还支持元数据提取、结构化文本提取等。
### 在哪里可以找到 GroupDocs.Parser 的详细文档？
探索完整文档[这里](https://reference.groupdocs.com/parser/net/).
### 如何获得与 GroupDocs.Parser 相关的查询的支持或帮助？
访问 GroupDocs 论坛以获得支持和讨论[这里](https://forum.groupdocs.com/c/parser/17).
### 购买之前是否有试用版可供评估 GroupDocs.Parser？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).