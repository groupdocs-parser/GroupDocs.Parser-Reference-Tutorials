---
title: 以 Raw 模式从 Excel 表中提取文本
linktitle: 以 Raw 模式从 Excel 表中提取文本
second_title: GroupDocs.Parser .NET API
description: 在本综合教程中了解如何使用 GroupDocs.Parser for .NET 从 Excel 表中提取文本。下载并开始解析。
weight: 15
url: /zh/net/excel-document-processing/extract-text-from-excel-sheet-in-raw-mode/
type: docs
---
# 以 Raw 模式从 Excel 表中提取文本

## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 在原始模式下从 Excel 工作表中提取文本。GroupDocs.Parser 是一个功能强大的 API，允许开发人员使用各种文档格式（包括 Excel 文件）进行文本提取和分析。我们将介绍先决条件、导入命名空间并分解每个步骤以演示从 Excel 工作表中提取文本的过程。
## 先决条件
在开始之前，请确保已设置以下先决条件：
- Visual Studio：在您的机器上安装 Visual Studio IDE。
- 适用于 .NET 的 GroupDocs.Parser：从[下载页面](https://releases.groupdocs.com/parser/net/).
- 示例 Excel 文件：准备一个用于文本提取的示例 Excel 文件。

## 导入命名空间
首先将必要的命名空间导入到您的 C# 项目中以访问 GroupDocs.Parser 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 步骤 1：创建解析器类的实例
首先，创建一个实例`Parser`通过提供示例 Excel 文件的路径来添加类：
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //您的文本提取代码将放在此处
}
```
## 第 2 步：获取文档信息
使用检索文档信息`GetDocumentInfo()`方法：
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 步骤 3：迭代工作表
循环遍历 Excel 文件中的每个工作表：
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.RawPageCount));
    
    //从每张工作表中提取文本的代码将放在此处
}
```
## 步骤 4：从每张表中提取文本
使用`TextReader`：
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 结论
在本教程中，我们介绍了如何使用 GroupDocs.Parser for .NET 从 Excel 表中提取文本。通过遵循上面概述的步骤，您可以有效地从 Excel 文件中检索文本数据，以便在 .NET 应用程序中进一步处理或分析。

## 常见问题解答
### GroupDocs.Parser 可以从其他文档格式中提取文本吗？
是的，GroupDocs.Parser 支持多种文档格式，包括 Word、PDF、PowerPoint 等。
### GroupDocs.Parser 是否适合处理大型 Excel 文件？
是的，GroupDocs.Parser 旨在有效地处理大型文档。
### 在哪里可以找到有关 GroupDocs.Parser 的更多文档？
您可以参考[文档](https://tutorials.groupdocs.com/parser/net/)了解详细信息和示例。
### 如何获得 GroupDocs.Parser 的临时许可证？
访问[此链接](https://purchase.groupdocs.com/temporary-license/)申请临时执照。
### GroupDocs.Parser 是否提供客户支持？
是的，您可以寻求帮助或提问[GroupDocs 论坛](https://forum.groupdocs.com/c/parser/17).