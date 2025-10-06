---
title: 从 Word 文档中提取图像
linktitle: 从 Word 文档中提取图像
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从 Word 文档中提取图像。本教程提供将图像集成到 .NET 的分步指导。
weight: 11
url: /zh/net/word-document-processing/extract-images-from-word-document/
type: docs
---
# 从 Word 文档中提取图像

## 介绍
在本教程中，您将学习如何使用 GroupDocs.Parser for .NET 从 Word 文档中提取图像。GroupDocs.Parser 是一个功能强大的 .NET 库，可让您从包括 Word (DOCX) 在内的各种文档格式中解析和提取文本、元数据、图像等。
## 先决条件
开始之前，请确保已设置以下先决条件：
- 您的机器上安装了 Visual Studio。
- C# 编程的基本知识。
- 已安装 GroupDocs.Parser for .NET 库。您可以从以下位置下载[这里](https://releases.groupdocs.com/parser/net/).
## 导入命名空间
首先，您需要在 C# 项目中导入必要的命名空间以使用 GroupDocs.Parser 功能：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
现在，让我们将从 Word 文档中提取图像的过程分解为简单的步骤：
## 步骤 1：创建解析器类的实例
首先创建一个`Parser`类，提供 Word 文档的路径作为输入。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //此处提供图像提取代码
}
```
## 第 2 步：从 Word 文档中提取图像
接下来，使用`GetImages()`方法`Parser`对象从文档中提取图像。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 步骤 3：定义图像保存选项
指定保存提取图像的选项。例如，您可以选择图像格式（例如 PNG）并配置其他设置。
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 步骤 4：迭代提取的图像并保存
遍历每个提取的图像并使用指定的选项将其保存到文件中。
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
在本教程中，您学习了如何使用 GroupDocs.Parser for .NET 从 Word 文档中提取图像。通过遵循这些步骤，您可以轻松地将文档解析和图像提取功能集成到您的 .NET 应用程序中。

## 常见问题解答
### GroupDocs.Parser 除了可以从 Word 中提取其他文档格式的图像吗？
是的，GroupDocs.Parser 支持各种文档格式，包括 PDF、PowerPoint、Excel 等。
### 如何获得 GroupDocs.Parser 的临时许可证？
您可以从以下网站获取临时许可证以进行测试[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以找到有关 GroupDocs.Parser for .NET 的更多文档？
您可以参考完整文档[这里](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 有免费试用版吗？
是的，您可以通过免费试用探索 GroupDocs.Parser 的功能[这里](https://releases.groupdocs.com/).
### 我如何获得支持或询问与 GroupDocs.Parser 相关的问题？
您可以在[GroupDocs.Parser 论坛](https://forum.groupdocs.com/c/parser/17).