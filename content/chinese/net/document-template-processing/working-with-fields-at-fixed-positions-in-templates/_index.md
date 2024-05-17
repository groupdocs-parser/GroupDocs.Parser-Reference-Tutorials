---
title: 使用模板中固定位置的字段
linktitle: 使用模板中固定位置的字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取数据。带有代码示例的综合教程。
type: docs
weight: 11
url: /zh/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 处理模板中固定位置的字段。GroupDocs.Parser 是一个功能强大的文档解析库，使开发人员能够从各种文档格式（如 PDF、Word、Excel 等）中提取数据。具体来说，我们将专注于定义和利用模板字段来根据其固定位置提取目标信息。
## 先决条件
在开始之前，请确保您已准备好以下物品：
- 对 C# 和 .NET 开发有基本的了解。
- 您的系统上安装了 Visual Studio。
- 已安装 GroupDocs.Parser for .NET 库。您可以从以下位置下载[这里](https://releases.groupdocs.com/parser/net/).
- 用于测试的示例文档文件。

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
首先，在模板中定义一个固定位置的字段。此字段表示将从中提取数据的区域。
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
这里：
- `Rectangle`指定字段的位置和大小。
- `Point(35, 135)`表示左上角坐标。
- `Size(100, 10)`定义字段的宽度和高度。
- `"FromCompany"`是分配给该字段的名称。
## 第 2 步：创建模板
使用定义的字段构建模板。
```csharp
Template template = new Template(new TemplateItem[] { field });
```
这`Template`对象保存定义的字段。
## 步骤 3：使用模板解析文档
实例化`Parser`类与目标文档路径，然后使用创建的模板解析文档。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的数据
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
这里：
- `Parser`使用示例文档文件路径进行初始化。
- `ParseByTemplate`方法用于根据提供的模板提取数据。
- 使用以下方式访问提取的数据`DocumentData`，其中每个项目对应一个定义的字段。

## 结论
在本教程中，我们介绍了使用 GroupDocs.Parser for .NET 处理模板中固定位置字段的过程。通过定义具有特定字段位置的模板，开发人员可以从各种文档格式中准确提取目标数据。

## 常见问题解答
### GroupDocs.Parser 是否兼容所有文档格式？
 GroupDocs.Parser 支持多种文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。请参阅[文档](https://reference.groupdocs.com/parser/net/)以获取详细列表。
### 如何获得 GroupDocs.Parser 的临时许可证？
您可以从以下网站获取临时许可证以进行测试[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以找到对 GroupDocs.Parser 的支持？
如需技术援助和讨论，请访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).
### 我可以在购买之前试用 GroupDocs.Parser 吗？
是的，你可以免费试用探索图书馆[这里](https://releases.groupdocs.com/).
### 如何购买 GroupDocs.Parser 的许可证？
要购买许可证，请访问[购买页面](https://purchase.groupdocs.com/buy).