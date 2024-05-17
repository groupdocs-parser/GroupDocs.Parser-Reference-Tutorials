---
title: 在原始模式下提取文本
linktitle: 在原始模式下提取文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中擷取文字。在 .NET 應用程式中輕鬆、有效率、無縫地提取文字。
type: docs
weight: 19
url: /zh-hant/net/text-extraction/extract-text-in-raw-mode/
---
## 介紹
在本教程中，我們將探索如何利用 GroupDocs.Parser for .NET 從各種文件格式中高效提取文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員從 PDF、Word、Excel、PowerPoint 等文件中提取文字和元數據，從而簡化 .NET 應用程式中的文字擷取任務。
## 先決條件
在深入學習本教學之前，請確保您已設定以下先決條件：
- 您電腦上安裝的 Visual Studio 或任何其他 .NET 開發環境。
- C# 程式語言的基礎知識。
- 存取 .NET 程式庫的 GroupDocs.Parser。

## 導入命名空間
首先，請確保在 C# 專案中匯入 GroupDocs.Parser 所需的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 步驟1：初始化GroupDocs.Parser
若要開始文字擷取，請建立一個實例`Parser`類，傳遞範例文檔的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    //在這裡繼續進行文字提取
}
```
## 第 2 步：提取原始文本
內`using`塊，使用`GetText`方法與`TextOptions`從文件中提取原始文字：
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    //繼續閱讀文件中的文本
}
```
## 第 3 步：從文件中讀取文本
現在，利用`TextReader`物件從文件中讀取提取的文字：
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 結論
透過執行這些步驟，您可以使用 GroupDocs.Parser for .NET 從文件中有效地提取原始文字。本教程提供了在 .NET 應用程式中利用此程式庫進行無縫文字擷取的基礎指南。

## 常見問題解答
### GroupDocs.Parser 支援哪些文件格式？
GroupDocs.Parser 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以使用 GroupDocs.Parser 提取元資料和文字嗎？
是的，GroupDocs.Parser 允許從支援的文件格式中提取文字和元資料。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 與 .NET Core 以及傳統的 .NET Framework 相容。
### GroupDocs.Parser 是否處理受密碼保護的文件？
是的，如果提供正確的密碼，GroupDocs.Parser 可以處理受密碼保護的文件。
### 我可以將 GroupDocs.Parser 整合到我的 Web 應用程式中嗎？
當然，GroupDocs.Parser 可以無縫整合到使用 .NET 技術開發的 Web 應用程式中。