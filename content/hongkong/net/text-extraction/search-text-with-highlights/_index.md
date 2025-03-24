---
title: 搜尋帶有突出顯示的文本
linktitle: 搜尋帶有突出顯示的文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 搜尋和突出顯示文件中的文字。有效地提取有價值的見解。
weight: 24
url: /zh-hant/net/text-extraction/search-text-with-highlights/
---
## 介紹
在本教程中，我們將探討如何使用 GroupDocs.Parser for .NET 在文件中搜尋文字並突出顯示搜尋結果。 GroupDocs.Parser 是一個功能強大的程式庫，可讓您處理各種文件格式並提取文字、元資料等。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1.  GroupDocs.Parser for .NET：從以下位置下載並安裝該程式庫[這裡](https://releases.groupdocs.com/parser/net/).
2. IDE：使用 Visual Studio 或任何首選 IDE 進行 .NET 開發。
3. 範例文件：準備用於文字搜尋的範例文件（例如PDF、DOCX）。

## 導入命名空間
首先，首先在 .NET 專案中匯入必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立解析器實例
首先實例化`Parser`類別與範例檔案的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //你的程式碼在這裡
}
```
## 第 2 步：定義反白選項
指定`HighlightOptions`配置如何突出顯示搜尋結果。例如，設定15個字元的上下文視窗：
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## 第 3 步：搜尋文本
現在，在文件中執行文字搜尋。提供您要搜尋的關鍵字（例如“lorem”）：
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## 第 4 步：處理搜尋結果
遍歷搜尋結果並顯示找到的文字以及突出顯示的內容：
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## 結論
在本教學中，您學習如何使用 GroupDocs.Parser for .NET 在文件中搜尋文字並突出顯示搜尋結果。此功能對於 .NET 應用程式中的文字擷取和分析非常有用。

## 常見問題解答
### GroupDocs.Parser適合處理各種文件格式嗎？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Parser 從文件中提取元資料嗎？
絕對地！ GroupDocs.Parser 可讓您從文件中提取元資料、文字和結構化資料。
### 在哪裡可以找到有關 GroupDocs.Parser 的支援或提出問題？
您可以訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)任何與支援相關的查詢。
### GroupDocs.Parser 是否有免費試用版？
是的，您可以訪問[免費試用](https://releases.groupdocs.com/) GroupDocs.Parser 來評估其功能。
### 如何購買 GroupDocs.Parser 的許可證？
您可以從以下位置購買許可證[這裡](https://purchase.groupdocs.com/buy)並獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).