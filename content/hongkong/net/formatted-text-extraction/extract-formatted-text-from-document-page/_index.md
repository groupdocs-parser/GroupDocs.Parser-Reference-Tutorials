---
title: 從文件頁面中提取格式化文本
linktitle: 從文件頁面中提取格式化文本
second_title: GroupDocs.Parser .NET API
description: 使用 GroupDocs.Parser for .NET 從文件頁面中擷取格式化文字。高效可靠的文字擷取解決方案。
type: docs
weight: 11
url: /zh-hant/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## 介紹
在本教學中，我們將指導您完成使用 GroupDocs.Parser for .NET 從文件頁面提取格式化文字的過程。該程式庫允許您有效地解析和提取各種文件格式（如 PDF、Word、Excel 等）中的文字。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- Visual Studio 安裝在您的系統上。
- C# 程式設計基礎知識。
- 用於 .NET 函式庫的 GroupDocs.Parser。你可以下載它[這裡](https://releases.groupdocs.com/parser/net/).

## 導入命名空間
首先，先將必要的命名空間匯入到您的 C# 專案中。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先建立一個實例`Parser`類別透過提供範例文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //代碼將放在這裡
}
```
## 步驟2：檢查是否支援格式化文字擷取
在繼續進行文字擷取之前，請先驗證文件是否支援格式化文字擷取。
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## 第三步：取得文件資訊
檢索有關文件的信息，例如頁數。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 第 4 步：迭代文件頁面並提取格式化文本
迭代文件的每一頁並使用指定選項（例如，Markdown 格式）提取格式化文字。
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 結論
現在您知道如何使用 GroupDocs.Parser for .NET 從文件頁面中擷取格式化文字。該庫提供了一個強大且易於使用的解決方案，用於從各種文件格式中提取文字。

## 常見問題解答
### GroupDocs.Parser 可以處理不同的檔案格式嗎？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 支援 .NET Core 和 .NET Framework。
### GroupDocs.Parser 在擷取過程中是否保留文字格式？
是的，GroupDocs.Parser 在提取文字時可以保留樣式和字體等格式。
### 我可以使用 GroupDocs.Parser 提取圖像和元資料嗎？
是的，GroupDocs.Parser 允許從文件中提取圖像、元資料和文字。
### 如何獲得 GroupDocs.Parser 的支援？
您可以從以下方面獲得支持[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).