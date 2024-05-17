---
title: 识别矩形区域中的文本
linktitle: 识别矩形区域中的文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用具有 OCR 功能的 GroupDocs.Parser for .NET 识别文档特定区域中的文本。
type: docs
weight: 14
url: /zh/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 识别文档特定矩形区域内的文本。GroupDocs.Parser 是一个功能强大的库，允许开发人员从各种文件格式（包括 PDF、Word、Excel 和 PowerPoint）中提取文本、元数据等。
## 先决条件
在开始之前，请确保您已进行以下设置：
-  GroupDocs.Parser for .NET：从以下网址下载并安装该库[这里](https://releases.groupdocs.com/parser/net/).
- 开发环境：Visual Studio 或任何其他.NET IDE。
- 示例文档：有一个包含要识别的文本的示例文件（例如 PDF、DOCX）。

## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 代码中：
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：初始化解析器设置
首先设置`ParserSettings`使用 OCR 连接器。在这里，我们将使用 Aspose OCR 本地连接器：
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 第 2 步：创建解析器实例
接下来，实例化`Parser`具有先前定义的设置的类：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    //代码在这里继续
}
```
代替`"YourSampleFile.pdf"`以及您的文档的路径。
## 步骤 3：定义 OCR 矩形
在文档中定义一个矩形，用于执行文本识别。例如，从`(0, 0)`与宽度`400`和身高`200`：
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## 步骤 4：配置文本识别选项
创造`TextOptions`指定 OCR 使用情况以及定义的矩形：
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 步骤 5：使用 OCR 提取文本
使用`GetText`方法`Parser`已配置的实例`TextOptions`：
```csharp
using (TextReader reader = parser.GetText(options))
{
    //读取提取的文本或处理“不支持”的情况
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## 结论
在本教程中，我们演示了如何利用 GroupDocs.Parser for .NET 使用 OCR 从文档中的特定矩形区域提取文本。此过程可以进一步定制并集成到各种应用程序中，以自动执行文本提取任务。

## 常见问题解答
### GroupDocs.Parser 可以从扫描的文档中提取文本吗？
是的，GroupDocs.Parser 支持 OCR（光学字符识别）从扫描文档中提取文本。
### GroupDocs.Parser 支持哪些文件格式？
GroupDocs.Parser 支持多种文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 如何处理不支持文本提取的文档？
您可以使用以下方式检查是否支持文本提取`TextReader`返回的实例`parser.GetText(options)`.
### GroupDocs.Parser 是否适合大规模文本提取任务？
是的，GroupDocs.Parser 旨在有效地处理大规模文本提取任务。
### 我可以在哪里获得与 GroupDocs.Parser 相关问题的支持？
如需支持和讨论，请访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).