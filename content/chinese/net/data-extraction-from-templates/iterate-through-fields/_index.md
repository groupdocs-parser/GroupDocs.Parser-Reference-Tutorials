---
title: 迭代字段
linktitle: 迭代字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取结构化数据。使用文档数据提取功能增强您的 .NET 应用程序。
weight: 11
url: /zh/net/data-extraction-from-templates/iterate-through-fields/
type: docs
---
# 迭代字段

## 介绍
GroupDocs.Parser for .NET 是一个功能强大的库，允许开发人员从各种文档格式（如 PDF、Microsoft Word、Excel 和 PowerPoint）中提取数据。本教程将指导您完成使用 GroupDocs.Parser 遍历文档字段并使用模板提取特定数据的过程。在本教程结束时，您将能够有效地从 .NET 应用程序中的文档中提取结构化数据。
## 先决条件
在开始之前，请确保您已设置以下先决条件：
- C# 编程的基本知识。
- 您的机器上安装了 Visual Studio。
- 您的项目中安装并引用了 .NET 库的 GroupDocs.Parser。

## 导入命名空间
首先，将必要的命名空间添加到你的 C# 文件中：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
让我们将该过程分解为逐步的说明。
## 步骤 1：定义模板字段
首先，使用正则表达式定义要从文档中提取的字段。
```csharp
//定义“价格”字段
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
//定义“电子邮件”字段
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
//创建具有定义字段的模板
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
在此步骤中，我们定义了两个字段：一个用于提取价格（由美元符号和数字标识），另一个用于提取电子邮件地址。
## 第 2 步：解析文档
接下来，使用`Parser`类使用定义的模板来解析文档。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //根据模板解析文档
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的数据
    for (int i = 0; i < data.Count; i++)
    {
        //打印字段名称
        Console.Write(data[i].Name + ": ");
        //检查提取的区域是否为文本
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
在这里，我们初始化`Parser`包含示例文档的路径，然后使用定义的模板解析文档。然后我们遍历提取的数据并打印字段名称以及提取的文本。
## 结论
在本教程中，我们探索了如何使用 GroupDocs.Parser for .NET 通过模板从文档中提取特定数据。通过利用正则表达式和模板，您可以高效地从各种文档格式中提取结构化信息。尝试使用不同的模板和文档类型来满足您的特定提取需求。

## 常见问题解答
### GroupDocs.Parser 可以从扫描文档中提取数据吗？
是的，GroupDocs.Parser 可以从扫描和可搜索的 PDF 文档中提取文本和元数据。
### GroupDocs.Parser 是否与 .NET Core 应用程序兼容？
是的，GroupDocs.Parser 支持 .NET Core 和 .NET Framework。
### GroupDocs.Parser 支持哪些文档格式？
GroupDocs.Parser 支持多种格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 如何使用 GroupDocs.Parser 处理大型文档？
GroupDocs.Parser 提供从大型文档的特定页面或部分提取数据的选项，确保高效处理。
### 我可以仅使用 GroupDocs.Parser 进行文本提取吗？
是的，您可以使用 GroupDocs.Parser 从文档中提取纯文本内容，而无需复杂的格式化。