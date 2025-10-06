---
title: 使用模板中链接位置的字段
linktitle: 使用模板中链接位置的字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中高效提取数据。带有代码示例的分步教程。
weight: 12
url: /zh/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# 使用模板中链接位置的字段

## 介绍
GroupDocs.Parser for .NET 是一个强大的库，旨在促进文档解析和数据提取任务。它支持多种文件格式，包括 PDF、DOCX、XLSX 等。它的一个主要功能是基于模板的数据提取，它允许您定义文档中的字段并根据这些预定义的模板提取特定数据。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- 对 C# 编程有基本了解
- 系统上安装了 Visual Studio
-  GroupDocs.Parser for .NET 库（下载自[这里](https://releases.groupdocs.com/parser/net/）)
- 要使用的示例文档文件

## 导入命名空间
首先在 C# 项目中包含必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 步骤 1：定义模板字段
首先，使用正则表达式和链接位置定义模板字段：
```csharp
//使用正则表达式定义字段
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
//定义具有特定位置设置的链接字段
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## 第 2 步：创建模板
接下来，创建一个包含定义字段的模板：
```csharp
//创建具有定义字段的模板
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## 步骤 3：使用模板解析文档
现在，初始化`Parser`类并使用模板解析文档：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //根据模板解析文档
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的数据并打印结果
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## 结论
GroupDocs.Parser for .NET 简化了使用模板从文档中提取结构化数据的过程。通过定义字段和应用模板，您可以高效地提取相关信息，从而提高文档处理任务的自动化程度和生产力。

## 常见问题解答
### GroupDocs.Parser 可以从加密的 PDF 文件中提取数据吗？
是的，GroupDocs.Parser 支持通过在解析过程中提供密码来解析加密的 PDF 文件。
### 基于模板的提取支持哪些文件格式？
GroupDocs.Parser 支持多种文件格式，包括 PDF、DOCX、XLSX、PPTX、TXT 等。
### GroupDocs.Parser 有试用版吗？
是的，你可以从以下网站下载免费试用版[这里](https://releases.groupdocs.com/).
### 我可以使用 GroupDocs.Parser 批量处理文档吗？
是的，GroupDocs.Parser 允许批处理同时解析多个文档。
### 在哪里可以获得 GroupDocs.Parser 的技术支持？
您可以在以下位置寻求技术支持并与社区互动[GroupDocs 论坛](https://forum.groupdocs.com/c/parser/17).