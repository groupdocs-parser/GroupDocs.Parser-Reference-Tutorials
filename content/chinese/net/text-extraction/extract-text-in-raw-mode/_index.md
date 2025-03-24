---
title: 以原始模式提取文本
linktitle: 以原始模式提取文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 从文档中提取文本。在 .NET 应用程序中轻松、高效、无缝地提取文本。
weight: 19
url: /zh/net/text-extraction/extract-text-in-raw-mode/
---

# 以原始模式提取文本

## 介绍
在本教程中，我们将探讨如何利用 GroupDocs.Parser for .NET 有效地从各种文档格式中提取文本。GroupDocs.Parser 是一个功能强大的库，使开发人员能够从 PDF、Word、Excel、PowerPoint 等文档中提取文本和元数据，从而简化 .NET 应用程序中的文本提取任务。
## 先决条件
在深入学习本教程之前，请确保您已设置以下先决条件：
- 您的机器上安装有 Visual Studio 或任何其他 .NET 开发环境。
- C# 编程语言的基本知识。
- 访问 .NET 库的 GroupDocs.Parser。

## 导入命名空间
首先，确保在 C# 项目中导入 GroupDocs.Parser 所需的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 步骤 1：初始化 GroupDocs.Parser
要开始文本提取，请创建一个实例`Parser`类，将路径传递给示例文档：
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    //在此处继续提取文本
}
```
## 第 2 步：提取原始文本
在`using`块，使用`GetText`方法`TextOptions`从文档中提取原始文本：
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    //继续阅读文档中的文本
}
```
## 步骤 3：从文档读取文本
现在，利用`TextReader`对象从文档中读取提取的文本：
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 结论
通过遵循这些步骤，您可以使用 GroupDocs.Parser for .NET 有效地从文档中提取原始文本。本教程提供了在 .NET 应用程序中利用此库进行无缝文本提取的基础指南。

## 常见问题解答
### GroupDocs.Parser 支持哪些文件格式？
GroupDocs.Parser 支持多种文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以使用 GroupDocs.Parser 和文本一起提取元数据吗？
是的，GroupDocs.Parser 允许从支持的文档格式中提取文本和元数据。
### GroupDocs.Parser 是否与 .NET Core 兼容？
是的，GroupDocs.Parser 与 .NET Core 以及传统的 .NET Framework 兼容。
### GroupDocs.Parser 是否处理受密码保护的文档？
是的，如果提供了正确的密码，GroupDocs.Parser 可以处理受密码保护的文档。
### 我可以将 GroupDocs.Parser 集成到我的 Web 应用程序中吗？
当然，GroupDocs.Parser 可以无缝集成到使用.NET 技术开发的 Web 应用程序中。