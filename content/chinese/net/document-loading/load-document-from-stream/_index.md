---
title: 从流加载文档
linktitle: 从流加载文档
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser 从 .NET 中的各种文档格式中提取文本。带有代码示例的分步指南。
weight: 12
url: /zh/net/document-loading/load-document-from-stream/
type: docs
---
# 从流加载文档

## 介绍
在 .NET 应用程序的文档处理领域，从各种文件格式中提取文本是一项常见要求。GroupDocs.Parser for .NET 提供了一个强大的解决方案，可以无缝解析和提取各种文档中的文本。本教程将指导您逐步完成利用 GroupDocs.Parser 从文档中提取文本的过程。
## 先决条件
在深入使用 GroupDocs.Parser for .NET 之前，请确保已完成以下设置：
- 开发环境：Visual Studio 或任何其他.NET 开发环境。
-  GroupDocs.Parser for .NET 包：从以下位置下载并安装 GroupDocs.Parser for .NET 库[这里](https://releases.groupdocs.com/parser/net/).
- 文档样本：准备好用于文本提取的样本文档。
## 导入命名空间
首先将必要的命名空间导入您的 .NET 项目以访问 GroupDocs.Parser 功能。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

以下步骤演示如何使用 GroupDocs.Parser 从流中提取文档中的文本。
## 步骤 1：从流加载文档
```csharp
//创建流
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    //使用流创建 Parser 类的实例
    using (Parser parser = new Parser(stream))
    {
        //将文本提取到阅读器中
        using (TextReader reader = parser.GetText())
        {
            //打印文档中的文本
            //如果不支持文本提取，则阅读器将为空
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
在此示例中：
- 我们为文档文件打开一个文件流（`YourSampleFile.docx`）。
- 初始化一个`Parser`与流一起实例。
- 使用`parser.GetText()`检索`TextReader`包含提取的文本。
- 如果文档格式不支持文本提取，则打印出提取的文本或消息。
## 结论
GroupDocs.Parser for .NET 简化了从各种文档格式中提取文本的过程，使开发人员能够高效地处理和利用其应用程序中的文本内容。通过遵循本教程中概述的步骤，您可以将文档文本提取功能无缝集成到您的 .NET 项目中。

## 常见问题解答
### GroupDocs.Parser for .NET 支持哪些文档格式？
GroupDocs.Parser 支持多种文档格式，包括 DOCX、PDF、XLSX、PPTX、EPUB 等。
### GroupDocs.Parser 可以从文档中提取图像或元数据吗？
是的，GroupDocs.Parser 可以从各种文档类型中提取图像、元数据和文本。
### GroupDocs.Parser 是否与 .NET Core 应用程序兼容？
是的，GroupDocs.Parser 与 .NET Framework 和 .NET Core 应用程序兼容。
### 如何获得 GroupDocs.Parser 的临时许可证？
您可以从[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以找到有关 GroupDocs.Parser 的更多支持或文档？
如需更多支持，请访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17)或参考[文档](https://tutorials.groupdocs.com/parser/net/).
