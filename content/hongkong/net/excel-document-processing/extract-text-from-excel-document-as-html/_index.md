---
title: 從 Excel 文件中擷取文字為 HTML
linktitle: 從 Excel 文件中擷取文字為 HTML
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從 Excel 文件中提取文字並將其轉換為 HTML。
weight: 13
url: /zh-hant/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# 從 Excel 文件中擷取文字為 HTML

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從 Excel 文件中擷取文字並將其轉換為 HTML 格式。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員使用各種文件格式，有效地提取文字和元資料。
## 先決條件
在開始之前，請確保您已進行以下設定：
- Visual Studio 安裝在您的系統上。
- 對 C# 程式設計有基本了解。
- 用於 .NET 的 GroupDocs.Parser 函式庫。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
## 導入命名空間
首先在 C# 專案中包含必要的命名空間以存取 GroupDocs.Parser 功能。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先，實例化`Parser`類，透過提供 Excel 文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //更多程式碼將在此處
}
```
代替`"YourSampleFile.xlsx"`以及 Excel 檔案的路徑。
## 第 2 步：將文字提取為 HTML
內`using`塊的`Parser`實例，使用`GetFormattedText`方法在 HTML 模式下提取格式化文字。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //更多程式碼將在此處
    }
}
```
## 第 3 步：讀取並列印提取的 HTML 文字
接下來，讀取從中提取的 HTML 文本`TextReader`並將其列印到控制台。
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
執行後，此程式碼將從 Excel 文件中提取文字並將其以 HTML 格式顯示在控制台中。
## 結論
在本教學中，我們學習如何使用 GroupDocs.Parser for .NET 從 Excel 文件中提取文字並將其轉換為 HTML 格式。該程式庫提供了一種處理各種文件格式的簡單方法，使開發人員能夠有效地處理其應用程式中的文字擷取任務。

## 常見問題解答
### GroupDocs.Parser 可以處理除 Excel 之外的其他文件格式嗎？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、Word、PowerPoint 等。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 與 .NET Framework 和 .NET Core 也相容。
### GroupDocs.Parser 在文字擷取過程中是否保留格式？
是的，GroupDocs.Parser 可以在文字擷取過程中保留字體、樣式和佈局等格式。
### 我可以使用 GroupDocs.Parser 從文件中提取元資料嗎？
是的，GroupDocs.Parser 允許從支援的文件類型中提取作者、建立日期等元資料。
### GroupDocs.Parser 是否有免費試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).