---
title: 按頁搜尋文本
linktitle: 按頁搜尋文本
second_title: GroupDocs.Parser .NET API
description: 了解使用 GroupDocs.Parser for .NET 按頁面搜尋文字。從 .NET 應用程式中的文件中有效地提取特定內容。
weight: 22
url: /zh-hant/net/text-extraction/search-text-by-pages/
type: docs
---
# 按頁搜尋文本

## 介紹
在 .NET 開發領域，從文件中有效地解析和提取文字是一項至關重要的任務。 GroupDocs.Parser for .NET 提供了處理各種文件格式的強大功能，使開發人員能夠無縫搜尋和提取特定內容。本教學將引導您完成利用 GroupDocs.Parser 在 .NET 應用程式中按頁面搜尋文字的過程。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
- 對 C# 和 .NET 架構有基本了解
- 您的系統上安裝了 Visual Studio
- GroupDocs.Parser for .NET 程式庫已安裝（從[這裡](https://releases.groupdocs.com/parser/net/）)
- 用於測試搜尋功能的範例文件
## 導入命名空間
首先，在專案中包含必要的命名空間以存取 GroupDocs.Parser 功能：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先實例化`Parser`類別與範例檔案的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //你的程式碼放在這裡
}
```
## 第 2 步：使用頁碼搜尋文本
利用`Search`尋找文件中特定關鍵字以及頁碼的方法：
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## 第 3 步：檢查搜尋支持
驗證文檔類型是否支援搜尋操作：
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## 第 4 步：迭代搜尋結果
迭代搜尋結果以檢索索引位置、頁碼和找到的文字：
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## 結論
在本教學中，我們探討如何使用 GroupDocs.Parser for .NET 按頁面實作文字搜尋。透過執行這些步驟，您可以有效地將文件解析和搜尋功能整合到您的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Parser 是否相容於各種文件格式？
是的，GroupDocs.Parser 支援多種文件格式，包括 DOCX、PDF、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Parser 從文件中提取圖像和元資料嗎？
當然，GroupDocs.Parser 允許從文件中提取圖像、元資料和文字。
### 在哪裡可以找到 GroupDocs.Parser 的詳細文件？
您可以存取文檔[這裡](https://tutorials.groupdocs.com/parser/net/).
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以申請臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 我可以在哪裡獲得 GroupDocs.Parser 的支援或協助？
如需支援和討論，請造訪 GroupDocs.Parser 論壇[這裡](https://forum.groupdocs.com/c/parser/17).