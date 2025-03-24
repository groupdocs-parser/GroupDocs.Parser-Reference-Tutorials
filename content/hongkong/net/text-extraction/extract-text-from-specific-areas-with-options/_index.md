---
title: 使用選項從特定區域提取文本
linktitle: 使用選項從特定區域提取文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中的特定區域擷取文字。透過本教學探索進階文字擷取選項。
weight: 14
url: /zh-hant/net/text-extraction/extract-text-from-specific-areas-with-options/
---

# 使用選項從特定區域提取文本

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 使用可自訂選項從文件中的特定區域擷取文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員輕鬆地從各種文件格式解析和擷取文字。
## 先決條件
在我們深入編碼之前，請確保您具備以下條件：
1. 開發環境：安裝 Visual Studio 或任何其他 .NET 開發 IDE。
2.  GroupDocs.Parser 函式庫：從下列位置下載並安裝適用於 .NET 的 GroupDocs.Parser[這裡](https://releases.groupdocs.com/parser/net/).
3. 範例文件：準備一個範例文件（例如 PDF、DOCX 等）以從中提取文字。

## 導入命名空間
首先，您需要匯入必要的命名空間來存取 GroupDocs.Parser 類別和方法。
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
初始化一個實例`Parser`類別透過提供範例文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //文字區域提取的程式碼將放在此處
}
```
## 第 2 步：定義文字區域擷取選項
創造`PageTextAreaOptions`指定文字擷取的標準。
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
在這個例子中：
- `"\\s[a-z]{2}\\s"`是一個正規表示式模式，用於匹配僅包含小寫字母的文字區域。
- `new Rectangle(new Point(0, 0), new Size(300, 100))`定義頁面上從中提取文字的矩形（位置和大小）。
## 第 3 步：提取文字區域
使用定義的選項提取符合指定條件的文字區域。
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## 第 4 步：檢查並迭代提取的文字區域
檢查是否支援文字區域提取，然後迭代提取的區域。
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## 結論
在本教學中，我們介紹如何使用 GroupDocs.Parser for .NET 從文件中的特定區域擷取文字。該程式庫提供了解析各種文件格式的廣泛功能，使其成為文字擷取任務的寶貴工具。

## 常見問題解答
### GroupDocs.Parser 可以從掃描文件中提取文字嗎？
是的，GroupDocs.Parser 支援對掃描文件進行基於 OCR 的文字擷取。
### GroupDocs.Parser 是否相容於多種文件格式？
是的，它可以從 PDF、DOCX、XLSX、PPTX 和其他流行格式中解析和提取文字。
### GroupDocs.Parser 是否提供對 .NET Core 的支援？
是的，GroupDocs.Parser 與 .NET Core 以及 .NET Framework 相容。
### 我可以使用 GroupDocs.Parser 提取元資料和文字嗎？
是的，您可以從文件中提取文字內容和元資料。
### GroupDocs.Parser 是否有試用版？
是的，您可以從以下位置獲得免費試用[這裡](https://releases.groupdocs.com/).