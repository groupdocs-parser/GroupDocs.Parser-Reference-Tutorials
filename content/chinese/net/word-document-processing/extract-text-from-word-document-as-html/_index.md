---
title: 从 Word 文档中提取文本作为 HTML
linktitle: 从 Word 文档中提取文本作为 HTML
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从 Word 文档中提取文本并将其保存为 HTML。带有代码示例的分步教程。
weight: 16
url: /zh/net/word-document-processing/extract-text-from-word-document-as-html/
---

# 从 Word 文档中提取文本作为 HTML

## 介绍
GroupDocs.Parser for .NET 是一个功能强大的文档解析库，它使开发人员能够无缝地从各种文件格式中提取文本和元数据。在本教程中，我们将重点介绍如何利用 GroupDocs.Parser 从 Word 文档中提取文本并将其保存为 HTML。此过程对于内容分析、索引或将文档转换为 Web 友好格式等任务至关重要。在本指南结束时，您将清楚地了解如何在 .NET 应用程序中有效地使用 GroupDocs.Parser。
## 先决条件
在深入学习本教程之前，请确保您满足以下先决条件：
- C# 编程的基本知识。
- 您的开发机器上安装了 Visual Studio。
-  GroupDocs.Parser for .NET 库。您可以从以下位置下载[这里](https://releases.groupdocs.com/parser/net/).
- 访问示例 Word 文档以用于测试目的。
## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
按照以下详细步骤从 Word 文档中提取文本并使用 GroupDocs.Parser for .NET 将其保存为 HTML：
## 步骤 1：创建解析器类的实例
首先，创建一个实例`Parser`通过提供示例 Word 文档的路径来添加类：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //继续步骤2...
}
```
代替`"YourSampleFile.docx"`以及您的 Word 文档的路径。
## 步骤 2：将格式化的文本提取为 HTML
接下来，使用`GetFormattedText`方法以及`FormattedTextOptions`提取 HTML 格式的文本：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //将格式化的文本提取到阅读器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //继续步骤 3...
    }
}
```
## 步骤 3：读取并输出提取的 HTML
最后，从中读取提取的 HTML 内容`TextReader`并将其打印到控制台：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //将格式化的文本提取到阅读器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //将格式化的文本打印为 HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Parser for .NET 从 Word 文档中提取文本并将其保存为 HTML。该库提供了一种直接有效的方法来解析文档内容，使其成为 .NET 应用程序中文档处理任务的宝贵工具。

## 常见问题解答
### 如何获得 GroupDocs.Parser 的临时许可证？
您可以从申请临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以找到有关 GroupDocs.Parser 的更多文档？
有详细文档可供查阅[这里](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 有免费试用版吗？
是的，您可以访问免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Parser 的支持？
访问支持论坛[这里](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser 支持哪些类型的文档？
GroupDocs.Parser 支持各种文档格式，包括 Word、PDF、Excel、PowerPoint 等。