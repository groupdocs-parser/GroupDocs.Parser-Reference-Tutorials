---
title: 从本地磁盘加载文档
linktitle: 从本地磁盘加载文档
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从各种文档格式中提取文本。使用 C# 轻松高效地提取文本。
weight: 11
url: /zh/net/document-loading/load-document-from-local-disk/
---
## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Parser for .NET 从文档中提取文本。GroupDocs.Parser 是一个功能强大的库，允许开发人员解析各种文档格式并以编程方式提取文本内容。我们将介绍使用此库开始文本提取所需的步骤。
## 先决条件
在开始之前，请确保您已安装以下先决条件：
- 您的系统上安装了 Visual Studio。
- C# 编程语言的基本知识。
- 已安装 GroupDocs.Parser for .NET 库（下载[这里](https://releases.groupdocs.com/parser/net/)）。

## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## 步骤 1：从本地磁盘加载文档
首先从本地磁盘加载文档。替换`"Your Sample File"`与目标文档的路径一起。
```csharp
//设置文件路径
string filePath = "Your Sample File";
//使用 filePath 创建 Parser 类的实例
using (Parser parser = new Parser(filePath))
{
    //将文本提取到阅读器中
    using (TextReader reader = parser.GetText())
    {
        //打印从文档中提取的文本
        //如果不支持文本提取，则阅读器将为空
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## 步骤说明
1. 设置文件路径：首先指定要从中提取文本的文档的路径（`filePath`多变的）。
2. 创建解析器实例：实例化`Parser`通过`filePath`.
3. 提取文本：使用`GetText()`方法`Parser`实例来获取`TextReader`包含从文档中提取的文本的对象。
4. 阅读摘录的文本：利用`ReadToEnd()`方法`TextReader`检索从文档中提取的全部文本内容。
5. 处理不支持的格式：如果文档格式不支持文本提取，则`reader`对象将`null`，您可以相应地处理这种情况。

## 结论
在本教程中，我们介绍了使用 GroupDocs.Parser for .NET 从文档中提取文本的初始步骤。此库提供了用于文档解析的广泛功能，使开发人员能够在其应用程序中高效地处理各种文件格式。

## 常见问题解答
### GroupDocs.Parser 是否兼容所有文档格式？
GroupDocs.Parser 支持多种格式，包括 PDF、Microsoft Office 文档（Word、Excel、PowerPoint）等。
### 我可以使用 GroupDocs.Parser 和文本一起提取元数据吗？
是的，GroupDocs.Parser 允许从支持的文档格式中提取文本内容和元数据。
### 在哪里可以找到有关 GroupDocs.Parser 的更多资源和支持？
访问[GroupDocs.Parser 文档](https://tutorials.groupdocs.com/parser/net/)了解详细的 API 参考并探索[GroupDocs 论坛](https://forum.groupdocs.com/c/parser/17)寻求社区支持。
### 如何获得 GroupDocs.Parser 的临时许可证？
您可以请求[临时执照](https://purchase.groupdocs.com/temporary-license/)用于评估和测试目的。
### GroupDocs.Parser 有免费试用版吗？
是的，你可以下载[免费试用](https://releases.groupdocs.com/)GroupDocs.Parser 的版本。