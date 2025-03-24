---
title: 使用选项从文档中提取条形码
linktitle: 使用选项从文档中提取条形码
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取条形码。包含代码示例和常见问题解答的综合教程。
weight: 14
url: /zh/net/barcode-extraction/extract-barcodes-from-document-with-options/
---

# 使用选项从文档中提取条形码

## 介绍
在本教程中，我们将介绍使用 GroupDocs.Parser for .NET 从文档中提取条形码的过程。GroupDocs.Parser 是一个功能强大的库，可让您从各种文档格式（如 PDF、Microsoft Word、Excel 等）中提取文本、元数据和条形码。
## 先决条件
开始之前，请确保您已满足以下先决条件：
1. 开发环境：确保您的机器上安装了 Visual Studio。
2.  GroupDocs.Parser 库：从以下位置下载并安装 GroupDocs.Parser for .NET 库[这里](https://releases.groupdocs.com/parser/net/).
3. 示例文档：准备一个包含条形码的示例文档（例如 PDF、DOCX）以供提取。

## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 项目中以利用 GroupDocs.Parser 功能。
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## 步骤 1：创建解析器类的实例
首先，创建一个实例`Parser`通过将路径传递到示例文档来添加类。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //下一步要添加的代码
}
```
## 步骤 2：检查条形码提取支持
接下来，使用`Features`的财产`Parser`实例。
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## 步骤 3：定义条形码提取选项
现在，使用以下选项指定条形码提取选项`BarcodeOptions`.可设置质量模式、条码类型等参数。
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## 步骤 4：从文档中提取条形码
使用`GetBarcodes`方法`Parser`根据定义的选项提取条形码的类。
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## 步骤 5：迭代并显示提取的条形码
最后，遍历提取的条形码并显示其页面索引和值。
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Parser for .NET 从文档中提取条形码。此过程涉及创建`Parser`实例、定义提取选项并遍历提取的条形码。GroupDocs.Parser 简化了从各种文档格式中提取条形码的任务，从而能够在 .NET 应用程序中高效地处理文档。

## 常见问题解答
### GroupDocs.Parser 可以从 PDF 文档中提取条形码吗？
是的，GroupDocs.Parser 支持从 PDF 文档以及其他格式（如 DOCX、XLSX 等）中提取条形码。
### GroupDocs.Parser 支持哪些条形码类型？
GroupDocs.Parser 支持各种条形码类型，包括二维码、Code 39、Code 128 等。
### GroupDocs.Parser 用于商业用途需要许可证吗？
是的，商业使用需要有效的许可证。你可以从[这里](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser 是否适合批量处理文档？
是的，GroupDocs.Parser 可以有效地处理文档的批处理，包括文本提取、元数据检索和条形码提取。
### 在哪里可以找到 GroupDocs.Parser 的技术支持？
您可以获得技术支持或咨询[GroupDocs 论坛](https://forum.groupdocs.com/c/parser/17).