---
title: 从 Excel 文档中提取文本作为 HTML
linktitle: 从 Excel 文档中提取文本作为 HTML
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取文本并将其转换为 HTML。
weight: 13
url: /zh/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# 从 Excel 文档中提取文本作为 HTML

## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取文本并将其转换为 HTML 格式。GroupDocs.Parser 是一个功能强大的库，允许开发人员处理各种文档格式，高效地提取文本和元数据。
## 先决条件
在开始之前，请确保您已进行以下设置：
- 您的系统上安装了 Visual Studio。
- 对 C# 编程有基本的了解。
- 适用于 .NET 的 GroupDocs.Parser 库。您可以从以下位置下载[这里](https://releases.groupdocs.com/parser/net/).
## 导入命名空间
首先在 C# 项目中包含必要的命名空间以访问 GroupDocs.Parser 功能。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器类的实例
首先，实例化`Parser`通过提供 Excel 文档的路径来类。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //进一步的代码将放在此处
}
```
代替`"YourSampleFile.xlsx"`使用您的 Excel 文件的路径。
## 步骤 2：将文本提取为 HTML
在`using`块的`Parser`例如，使用`GetFormattedText`方法以HTML模式提取格式化的文本。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //进一步的代码将放在此处
    }
}
```
## 步骤 3：读取并打印提取的 HTML 文本
接下来，从`TextReader`并将其打印到控制台。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
一旦执行，该代码将从 Excel 文档中提取文本并将其以 HTML 格式显示在控制台中。
## 结论
在本教程中，我们学习了如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取文本并将其转换为 HTML 格式。该库提供了一种处理各种文档格式的简单方法，使开发人员能够有效地处理其应用程序中的文本提取任务。

## 常见问题解答
### GroupDocs.Parser 除了处理 Excel 之外还能处理其他文档格式吗？
是的，GroupDocs.Parser 支持多种文件格式，包括 PDF、Word、PowerPoint 等。
### GroupDocs.Parser 是否与 .NET Core 兼容？
是的，GroupDocs.Parser 与 .NET Framework 和 .NET Core 兼容。
### GroupDocs.Parser 在文本提取期间是否保留格式？
是的，GroupDocs.Parser 可以在文本提取期间保留字体、样式和布局等格式。
### 我可以使用 GroupDocs.Parser 从文档中提取元数据吗？
是的，GroupDocs.Parser 允许从支持的文档类型中提取元数据，例如作者、创建日期等。
### GroupDocs.Parser 有免费试用版吗？
是的，你可以从下载免费试用版[这里](https://releases.groupdocs.com/).