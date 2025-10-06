---
title: 以原始模式從頁面中提取文本
linktitle: 以原始模式從頁面中提取文本
second_title: GroupDocs.Parser .NET API
description: 在這個綜合教程中學習使用 Groupdocs.Parser for .NET 從文件頁面中高效提取文字。
weight: 17
url: /zh-hant/net/text-extraction/extract-text-from-page-in-raw-mode/
type: docs
---
# 以原始模式從頁面中提取文本

## 介紹
在本教程中，您將學習如何使用 Groupdocs.Parser for .NET 以原始模式從文件頁面中提取文字。該程式庫提供了高效的工具來解析和提取各種文件格式的內容，使開發人員能夠將文件文字提取合併到他們的 .NET 應用程式中。
## 先決條件
在開始之前，請確保您具備以下先決條件：
- C# 和 .NET 程式設計的基礎知識
- 您的電腦上安裝了 Visual Studio
- 存取 .NET 庫的 Groupdocs.Parser
- 用於測試的範例文件文件

## 導入命名空間
首先在您的 C# 專案中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：初始化解析器
首先，建立一個實例`Parser`類，透過提供範例文檔文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //你的程式碼在這裡
}
```
## 第 2 步：檢索文件資訊
使用檢索有關文件的信息`GetDocumentInfo()`方法。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 第 3 步：迭代頁面並提取文本
迭代文件的每一頁並提取文字內容。
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //從頁面中提取文本
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 結論
現在您已經了解如何使用 Groupdocs.Parser for .NET 以原始模式從文件頁面中提取文字。對於需要分析或處理各種文件格式的文字內容的應用程式來說，這可能是一個強大的功能。

## 常見問題解答
### Groupdocs.Parser for .NET 是否與所有文件格式相容？
Groupdocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX、EPUB 等。
### 我可以使用此庫提取元資料和文字嗎？
是的，Groupdocs.Parser 允許您從文件中提取文字和元資料。
### 有試用版可供測試嗎？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 Groupdocs.Parser 的技術支援？
如需技術協助，請訪問[Groupdocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).
### 在哪裡可以購買 Groupdocs.Parser for .NET 的授權？
您可以購買許可證[這裡](https://purchase.groupdocs.com/buy).