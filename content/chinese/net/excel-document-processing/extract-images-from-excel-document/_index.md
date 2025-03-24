---
title: 从 Excel 文档中提取图像
linktitle: 从 Excel 文档中提取图像
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取图像。带有代码示例的分步指南。
weight: 10
url: /zh/net/excel-document-processing/extract-images-from-excel-document/
---

# 从 Excel 文档中提取图像

## 介绍
在本教程中，您将学习如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取图像。GroupDocs.Parser 是一个功能强大的库，可让您解析和提取包括 Excel 文件在内的各种文档格式中的文本、元数据和图像。
## 先决条件
开始之前，请确保已设置以下先决条件：
1. 开发环境：安装 Visual Studio 或任何首选的 .NET 开发环境。
2.  GroupDocs.Parser 库：下载并引用 GroupDocs.Parser 库。您可以从以下位置获取该库[这里](https://releases.groupdocs.com/parser/net/).
3. 示例 Excel 文件：准备一个要从中提取图像的示例 Excel 文件。
## 导入命名空间
在您的项目中包含必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
请按照以下步骤从 Excel 文档中提取图像：
## 步骤 1：实例化解析器类
首先，创建一个实例`Parser`通过提供 Excel 文件的路径来类。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //您的代码在这里...
}
```
## 步骤 2：从 Excel 文档中检索图像
使用`GetImages()`从Excel文件中提取图像的方法。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 步骤 3：定义图像提取选项
指定用于保存提取图像的图像格式和其他选项。例如，要以 PNG 格式保存图像：
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 步骤 4：迭代并保存图像
遍历提取的图像并将每张图像保存到文件中。
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    //将图像保存为 PNG 文件
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## 结论
在本教程中，您学习了如何使用 GroupDocs.Parser for .NET 从 Excel 文档中提取图像。通过遵循这些步骤，您可以有效地将图像提取功能整合到您的 .NET 应用程序中。

## 常见问题解答
### 问：GroupDocs.Parser 除了能从 Excel 中提取其他文档格式的图像吗？
答：是的，GroupDocs.Parser 支持多种文档格式，包括 Word、PowerPoint、PDF 等。
### 问：如何获得 GroupDocs.Parser 集成的支持或帮助？
答：如需支持和帮助，请访问[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).
### 问：GroupDocs.Parser 可以免费使用吗？
答：GroupDocs.Parser 提供免费试用，但若要继续使用，您可能需要购买许可证。检查[定价和许可](https://purchase.groupdocs.com/buy)细节。
### 问：在购买许可证之前我可以试用 GroupDocs.Parser 吗？
答：是的，您可以获得[免费试用](https://releases.groupdocs.com/)评估 GroupDocs.Parser。
### 问：在哪里可以找到 GroupDocs.Parser 的详细文档？
答：请参阅综合[文档](https://tutorials.groupdocs.com/parser/net/)有关使用 GroupDocs.Parser 的详细信息。