---
title: 从文档中提取格式化文本
linktitle: 从文档中提取格式化文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取格式化文本。为您的应用程序提供简单而高效的文本提取。
weight: 10
url: /zh/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Parser for .NET 从各种类型的文档中提取格式化文本。GroupDocs.Parser 是一个功能强大的库，允许开发人员以简化和高效的方式处理文档。在本指南结束时，您将能够将文本提取功能无缝集成到您的 .NET 应用程序中。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- Visual Studio：确保您的系统上安装了 Visual Studio。
-  GroupDocs.Parser for .NET：从以下位置下载并安装 GroupDocs.Parser 库[这里](https://releases.groupdocs.com/parser/net/).
- 文档样本：准备用于文本提取的示例文档（例如 PDF、DOCX）。
## 导入命名空间
首先，在 C# 代码中包含必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器类的实例
首先初始化一个`Parser`对象与示例文档的路径。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //此处显示文本提取代码
}
```
代替`"YourSampleFile.pdf"`以及您的文档文件的路径。

## 步骤 2：提取格式化文本
在`using`块，使用`GetFormattedText`方法从文档中提取格式化的文本。使用以下方法指定所需的输出格式（例如 HTML）`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //将格式化的文本提取到阅读器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //检查是否支持提取
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            //读取并显示提取的文本
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## 结论
恭喜！您已经学会了如何使用 GroupDocs.Parser for .NET 从文档中提取格式化文本。这个多功能库为您的应用程序内的文本处理和分析开辟了可能性。

## 常见问题解答
### 问：GroupDocs.Parser 可以从受密码保护的文档中提取文本吗？
答：是的，GroupDocs.Parser 支持从受密码保护的文档中提取文本。
### 问：GroupDocs.Parser 支持哪些文档格式？
答：GroupDocs.Parser 支持多种格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 问：如何获得 GroupDocs.Parser 的临时许可证？
答：你可以从[这里](https://purchase.groupdocs.com/temporary-license/).
### 问：GroupDocs.Parser 是否提供从文档中提取图像的支持？
答：是的，GroupDocs.Parser 支持图像提取和文本提取。
### 问：在哪里可以找到更多支持或询问有关 GroupDocs.Parser 的问题？
答：访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17)寻求支持和讨论。