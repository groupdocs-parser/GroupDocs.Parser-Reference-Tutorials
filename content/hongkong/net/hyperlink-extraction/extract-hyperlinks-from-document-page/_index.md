---
title: 從文件頁面提取超鏈接
linktitle: 從文件頁面提取超鏈接
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中提取超連結。 C# 中超連結擷取的逐步指南。
type: docs
weight: 11
url: /zh-hant/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## 介紹
在本教學中，我們將逐步探索如何使用 GroupDocs.Parser for .NET 從文件中提取超連結。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員解析各種文件格式並提取文字、元資料和其他元素。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- Visual Studio：在開發電腦上安裝 Visual Studio。
-  GroupDocs.Parser 函式庫：下載並引用 GroupDocs.Parser 函式庫。你可以從[這裡](https://releases.groupdocs.com/parser/net/).
- 範例文件：準備包含用於測試的超連結的範例文件（例如 DOCX、PDF）。

## 導入命名空間
首先，包含使用 GroupDocs.Parser 功能所需的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立解析器實例
實例化`Parser`類與範例文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //代碼放在這裡...
}
```
## 第 2 步：檢查超連結提取支持
在繼續之前，請確保文件支援超連結提取。
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## 步驟3：檢索文件資訊
取得有關文件的基本資訊並檢查它是否包含頁面。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 第 4 步：迭代文件頁面
遍歷文檔的每一頁。
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //從當前頁面提取超鏈接
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    //迭代提取的超連結
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); //空行以提高可讀性
    }
}
```

## 結論
在本教程中，我們介紹了使用 GroupDocs.Parser for .NET 從文件中提取超連結的基礎知識。您學習如何初始化解析器、檢查超連結支援、檢索文件資訊以及迭代文件頁面以有效地提取超連結。

## 常見問題解答
### 我可以從不同的文件格式中提取超連結嗎？
是的，GroupDocs.Parser 支援多種格式，如 DOCX、PDF、PPTX 等，用於超連結擷取。
### GroupDocs.Parser 是否易於整合到現有的 .NET 應用程式中？
當然，GroupDocs.Parser 的設計非常簡單，可以輕鬆整合到您的 .NET 專案中。
### 我可以使用 GroupDocs.Parser 提取其他元資料以及超連結嗎？
是的，除了超連結之外，您還可以使用此程式庫從文件中提取文字、圖像和元資料。
### GroupDocs.Parser 是否處理加密或受密碼保護的文件？
如果提供了密碼，GroupDocs.Parser 可以解析受密碼保護的文件。
### 購買前是否有試用版可供測試？
是的，您可以下載免費試用版[這裡](https://releases.groupdocs.com/).