---
title: 按關鍵字搜尋文本
linktitle: 按關鍵字搜尋文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 在文件中按關鍵字搜尋文字。輕鬆有效率地提取相關內容。
weight: 21
url: /zh-hant/net/text-extraction/search-text-by-keyword/
---

# 按關鍵字搜尋文本

## 介紹
在本教程中，我們將深入研究使用 GroupDocs.Parser for .NET 在文件中按關鍵字搜尋文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員從各種文件格式（例如 PDF、Microsoft Office 文件等）中提取文字、元資料和其他資訊。對於處理大量文字資料的應用程式來說，在這些文件中搜尋特定關鍵字至關重要。
## 先決條件
在開始之前，請確保您已進行以下設定：
1. 開發環境：Visual Studio 或任何首選的 .NET IDE。
2.  GroupDocs.Parser for .NET：從下列位置下載程式庫[這裡](https://releases.groupdocs.com/parser/net/).
3. 存取範例文件：準備範例文件（例如PDF、DOCX）來測試關鍵字搜尋功能。

## 導入命名空間
首先，您需要在專案中包含必要的命名空間。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 第 1 步：實例化解析器類
首先建立一個實例`Parser`類別並提供範例文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //搜尋關鍵字
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    //迭代搜尋結果
    foreach (SearchResult result in searchResults)
    {
        //列印索引和找到的文本
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## 第 2 步：搜尋關鍵字
內`using`塊，調用`Search`方法上的`parser`對象，傳遞所需的關鍵字作為參數。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
代替`"test"`使用您想要在文件中搜尋的關鍵字。
## 第 3 步：迭代搜尋結果
接下來，迭代從取得的搜尋結果`Search`方法使用`foreach`環形。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
對於每個`SearchResult`目的`result`，您可以訪問其`Position`（索引）和`Text`（找到的文字）。

## 結論
在本教學中，我們探索如何使用 GroupDocs.Parser for .NET 在文件中按關鍵字輕鬆搜尋文字。利用`Search`的方法`Parser`類別允許根據特定搜尋字詞有效檢索相關文字片段。

## 常見問題解答
### GroupDocs.Parser 是否相容於各種文件格式？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Parser 執行高級文字擷取操作嗎？
絕對地！除了文字搜尋之外，GroupDocs.Parser 還支援元資料提取、結構化文字擷取等。
### 在哪裡可以找到 GroupDocs.Parser 的詳細文件？
探索完整的文檔[這裡](https://tutorials.groupdocs.com/parser/net/).
### 如何獲得有關 GroupDocs.Parser 相關查詢的支援或協助？
請造訪 GroupDocs 論壇以獲得支援和討論[這裡](https://forum.groupdocs.com/c/parser/17).
### 購買前是否有試用版評估 GroupDocs.Parser？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).