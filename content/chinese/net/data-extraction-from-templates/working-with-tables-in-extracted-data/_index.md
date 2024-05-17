---
title: 使用提取数据中的表格
linktitle: 使用提取数据中的表格
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取表格数据。使用预定义模板高效解析结构化内容。
type: docs
weight: 12
url: /zh/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 从文档中的表中提取数据。GroupDocs.Parser 是一个功能强大的工具，可让开发人员从各种文件格式（如 PDF、DOCX、XLSX 等）解析和提取文本、元数据和结构化内容。具体来说，我们将重点介绍如何使用预定义模板高效地提取表数据。
## 先决条件
开始之前，请确保已准备好以下事项：
- 您的机器上安装了 Visual Studio。
- 对 C# 和 .NET 框架有基本的了解。
- GroupDocs.Parser 库通过 NuGet 包管理器安装。

## 导入命名空间
首先导入使用 GroupDocs.Parser 和相关功能所需的命名空间。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 步骤 1：创建表格模板
要从表中提取数据，首先，定义一个模板来表示要提取的表的结构。指定表在文档中的位置和尺寸。
```csharp
//定义表参数（位置和大小）
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
//创建带参数的表模板
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## 第 2 步：定义模板
创建一个包含您定义的表模板的模板。此模板将指导解析器在提取表数据时查找什么。
```csharp
//使用表格创建模板
Template template = new Template(new TemplateItem[] { table });
```
## 步骤 3：解析文档并提取表格数据
利用 GroupDocs.Parser 中的 Parser 类使用您定义的模板来解析特定文档。
```csharp
//指定示例文件的路径
string filePath = "YourSampleFile.pdf";
//创建 Parser 类的实例
using (Parser parser = new Parser(filePath))
{
    //根据模板解析文档
    DocumentData data = parser.ParseByTemplate(template);
    //迭代所有提取的数据
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        //检查提取的字段是否是表
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        //迭代表格行
        for (int row = 0; row < area.RowCount; row++)
        {
            //迭代表列
            for (int column = 0; column < area.ColumnCount; column++)
            {
                //获取单元格值
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                //打印单元格值（如果为空则为空字符串）
                Console.Write(cellValue == null ? "" : cellValue.Text);
                //打印列之间的制表符空间
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            //打印完每行后移至下一行
            Console.WriteLine();
        }
    }
}
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Parser for .NET 从文档中提取表格数据。通过定义模板并利用解析方法，开发人员可以有效地从各种文件格式中提取表格等结构化数据。

## 常见问题解答
### GroupDocs.Parser 是否兼容所有文档格式？
是的，GroupDocs.Parser 支持多种文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以从文档中的特定区域提取数据吗？
当然，您可以定义针对文档内特定区域（如表格）进行提取的模板。
### GroupDocs.Parser 是否适合大型文档？
是的，GroupDocs.Parser 经过优化，可以有效处理大型文档，让开发人员能够无缝提取数据。
### GroupDocs.Parser 是否支持提取结构化数据的文本？
是的，除了结构化数据提取（如表格）之外，GroupDocs.Parser 还可以从文档中提取纯文本和元数据。
### 如何获得 GroupDocs.Parser 集成的支持或帮助？
如需支持和讨论，请访问 GroupDocs 社区论坛[这里](https://forum.groupdocs.com/c/parser/17).