---
title: 按目錄 (TOC) 項目提取文本
linktitle: 按目錄 (TOC) 項目提取文本
second_title: GroupDocs.Parser .NET API
description: 使用 GroupDocs.Parser for .NET 按目錄 (TOC) 擷取文字。學習用於結構化資料擷取的高效文件解析技術。
weight: 15
url: /zh-hant/net/text-extraction/extract-text-by-toc-item/
---

# 按目錄 (TOC) 項目提取文本

## 介紹
在本教學中，我們將探討如何利用 GroupDocs.Parser for .NET 根據文件中的目錄 (TOC) 項目來擷取文字。 GroupDocs.Parser 是一個功能強大的工具，可以進行高效率的文件解析和擷取。
## 先決條件
在繼續本教學之前，請確保您符合以下先決條件：
1. Visual Studio：在您的系統上安裝 Visual Studio IDE。
2.  GroupDocs.Parser for .NET：從下列位置下載並安裝 GroupDocs.Parser for .NET[這裡](https://releases.groupdocs.com/parser/net/).
3. 帶目錄的範例文件：準備包含目錄的文件（例如 PDF、DOCX）。

## 導入命名空間
首先，在 C# 專案中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## 第 1 步：建立 Parser 類別的實例
實例化`Parser`類別與範例文件的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    //在此繼續後續步驟...
}
```
## 第 2 步：提取目錄 (TOC)
從文件中取得目錄 (TOC) 項目：
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## 第 3 步：迭代 TOC 項並提取文本
迭代每個目錄項目並提取相應的文字：
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 結論
本教學課程示範如何使用 GroupDocs.Parser for .NET 從基於目錄 (TOC) 專案的文件中擷取文字。透過遵循概述的步驟，您可以以程式設計方式有效地解析和提取文件中的特定內容。

## 常見問題解答
### GroupDocs.Parser 支援哪些文件格式？
GroupDocs.Parser 支援多種文件格式，包括 PDF、Microsoft Word (DOC/DOCX)、Excel (XLS/XLSX)、PowerPoint (PPT/PPTX) 等。
### 我可以使用 GroupDocs.Parser 提取表格或圖像等結構化資料嗎？
是的，GroupDocs.Parser 提供了 API 來從各種文件類型中提取結構化數據，例如表格、圖像和元數據。
### GroupDocs.Parser 適合大型文件嗎？
GroupDocs.Parser 經過最佳化，可有效處理大型文檔，因此能夠從大量文件中無縫提取內容。
### 如何獲得 GroupDocs.Parser 的技術支援？
您可以尋求技術支援並與社區互動：[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).
### GroupDocs 是否提供免費試用評估？
是的，您可以從以下位置下載 GroupDocs.Parser 的免費試用版：[這裡](https://releases.groupdocs.com/).