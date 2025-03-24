---
title: 从文档页面提取表格
linktitle: 从文档页面提取表格
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 以编程方式从文档中提取表格。本综合教程提供分步指导。
weight: 11
url: /zh/net/table-extraction/extract-tables-from-document-page/
---

# 从文档页面提取表格

## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 从文档页面中提取表格。GroupDocs.Parser 是一个功能强大的库，允许开发人员处理各种文档格式，如 PDF、DOCX、XLSX 等。通过利用其功能，我们可以有效地从这些文档中提取表格等结构化数据，使我们能够以编程方式操作和分析信息。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- 您的机器上安装了 Visual Studio。
- 对 C# 和 .NET 开发有基本的了解。
-  GroupDocs.Parser for .NET 库。您可以从以下位置下载[这里](https://releases.groupdocs.com/parser/net/).
- 访问包含要提取的表格的示例文档（PDF、DOCX 等）。

## 导入命名空间
首先，在 C# 项目中导入必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## 步骤 1：创建解析器类的实例
实例化`Parser`通过提供示例文档的路径来添加类：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //您的代码在这里继续...
}
```
## 步骤 2：检查文档表格提取支持
继续之前，请验证文档是否支持表格提取：
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## 步骤 3：定义表格布局
定义要从文档中提取的表格的布局。根据文档的结构指定列宽和行高：
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  //列宽
    new double[] { 325, 340, 365, 395 });         //行高
```
## 步骤 4：配置表提取选项
使用指定的布局创建表格提取选项：
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 步骤 5：检索文档信息
获取有关文档的信息，包括页数：
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 步骤 6：迭代文档页面
遍历文档的每一页以提取表格：
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //从当前页面提取表格
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    //迭代提取的表
    foreach (PageTableArea table in tables)
    {
        //迭代表格的行
        for (int row = 0; row < table.RowCount; row++)
        {
            //迭代表的列
            for (int column = 0; column < table.ColumnCount; column++)
            {
                //获取表格单元格
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    //打印表格单元格的文本
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## 结论
在本教程中，我们介绍了使用 GroupDocs.Parser for .NET 从文档页面中提取表格的过程。通过遵循提供的步骤，您可以将表格提取功能无缝集成到 .NET 应用程序中，从而高效处理和操作文档中的结构化数据。

## 常见问题解答
### GroupDocs.Parser 可以从所有类型的文档中提取表格吗？
GroupDocs.Parser 支持各种文档格式，如 PDF、DOCX、XLSX 等，可以从兼容的文件类型中提取表格。
### GroupDocs.Parser for .NET 是否适合大规模文档处理？
是的，GroupDocs.Parser 旨在有效处理大型文档，使其适合处理大量数据集。
### GroupDocs.Parser 在表格提取期间是否保留格式？
是的，GroupDocs.Parser 在表格提取期间保留了格式细节，例如单元格边框、文本样式和对齐方式。
### 我可以根据内容标准提取特定表格吗？
GroupDocs.Parser 提供灵活的选项，可以根据布局模板或内容条件针对特定表进行提取。
### GroupDocs.Parser 是否与 .NET Core 兼容？
是的，GroupDocs.Parser 与 .NET Framework 和 .NET Core 环境兼容。