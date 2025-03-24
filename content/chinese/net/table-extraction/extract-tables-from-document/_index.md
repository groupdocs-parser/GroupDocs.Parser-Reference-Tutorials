---
title: 从文档中提取表格
linktitle: 从文档中提取表格
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 Groupdocs.Parser for .NET 从文档中提取表格。继续阅读有关集成此功能的详细指南。
weight: 10
url: /zh/net/table-extraction/extract-tables-from-document/
---

# 从文档中提取表格

## 介绍
Groupdocs.Parser for .NET 是一个全面的库，它有助于文档解析，允许您从文档中提取有价值的信息，例如表格、文本、元数据等。在本教程中，我们特别关注使用 Groupdocs.Parser API 从文档中提取表格。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- 您的系统上安装了 Visual Studio。
- 已安装 .NET Framework 或 .NET Core。
- C# 编程的基本知识。

## 导入命名空间
首先，您需要导入必要的命名空间来访问 Groupdocs.Parser 类和方法。
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
初始化一个新的实例`Parser`通过提供示例文档的路径来类。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //您的代码在此处
}
```
## 步骤 2：检查表提取支持
验证文档是否支持使用表格提取`Features`的财产`Parser`班级。
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## 步骤 3：定义表格布局
定义要提取的表格的布局`TemplateTableLayout`根据文档的结构指定列宽和行高。
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## 步骤 4：设置表提取选项
创造`PageTableAreaOptions`使用定义的布局来指定如何提取表格。
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 步骤 5：提取表格
利用`GetTables`方法`Parser`根据指定的选项从文档中提取表格的类。
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## 步骤 6：迭代并访问表数据
遍历提取的表及其各自的行和列以访问单元格数据。
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## 结论
在本教程中，我们介绍了如何使用 Groupdocs.Parser for .NET 高效地从文档中提取表格。利用此库的功能，您可以将表格提取无缝集成到 .NET 应用程序中。

## 常见问题解答
### Groupdocs.Parser 能处理不同的文档格式吗？
是的，Groupdocs.Parser 支持多种文档格式，包括 DOCX、PDF、XLSX 等。
### Groupdocs.Parser for .NET 有试用版吗？
是的，你可以从下载免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得对 Groupdocs.Parser 相关查询的支持？
您可以访问[Groupdocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17)寻求帮助。
### 我可以在哪里购买 Groupdocs.Parser 的许可证？
您可以从购买许可证[这里](https://purchase.groupdocs.com/buy).
### 如何获取用于评估目的的临时许可证？
您可以获得临时驾照[这里](https://purchase.groupdocs.com/temporary-license/).