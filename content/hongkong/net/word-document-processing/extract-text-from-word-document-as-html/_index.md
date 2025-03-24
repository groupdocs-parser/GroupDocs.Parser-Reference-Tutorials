---
title: 從 Word 文件中提取文字為 HTML
linktitle: 從 Word 文件中提取文字為 HTML
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從 Word 文件中提取文字並將其儲存為 HTML。帶有程式碼範例的分步教程。
weight: 16
url: /zh-hant/net/word-document-processing/extract-text-from-word-document-as-html/
---

# 從 Word 文件中提取文字為 HTML

## 介紹
GroupDocs.Parser for .NET 是一個功能強大的文件解析庫，使開發人員能夠從各種文件格式中無縫提取文字和元資料。在本教程中，我們將重點介紹如何利用 GroupDocs.Parser 從 Word 文件中提取文字並將其另存為 HTML。此過程對於內容分析、索引或將文件轉換為網路友善格式等任務至關重要。閱讀本指南後，您將清楚地了解如何在 .NET 應用程式中有效地使用 GroupDocs.Parser。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
- C# 程式設計基礎知識。
- Visual Studio 安裝在您的開發電腦上。
- 用於 .NET 函式庫的 GroupDocs.Parser。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
- 出於測試目的存取範例 Word 文件。
## 導入命名空間
首先，您需要將必要的命名空間匯入到您的 C# 專案中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
請依照以下詳細步驟，使用 GroupDocs.Parser for .NET 從 Word 文件中擷取文字並將其儲存為 HTML：
## 第 1 步：建立 Parser 類別的實例
首先，建立一個實例`Parser`類，透過提供範例 Word 文件的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //繼續步驟 2...
}
```
代替`"YourSampleFile.docx"`以及您的 Word 文件的路徑。
## 步驟 2：將格式化文字提取為 HTML
接下來，使用`GetFormattedText`方法連同`FormattedTextOptions`提取 HTML 格式的文字：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //將格式化文字擷取到閱讀器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //繼續步驟 3...
    }
}
```
## 步驟 3：讀取並輸出擷取的 HTML
最後，讀取擷取的HTML內容`TextReader`並將其列印到控制台：
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //將格式化文字擷取到閱讀器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //將格式化文字列印為 HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## 結論
在本教學中，我們探討如何使用 GroupDocs.Parser for .NET 從 Word 文件中提取文字並將其儲存為 HTML。該程式庫提供了一種簡單而有效的方法來解析文件內容，使其成為 .NET 應用程式中文件處理任務的寶貴工具。

## 常見問題解答
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以向以下機構申請臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到有關 GroupDocs.Parser 的更多文件？
提供詳細文檔[這裡](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 是否有免費試用版？
是的，您可以存取免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得對 GroupDocs.Parser 的支援？
造訪支援論壇[這裡](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser 支援哪些類型的文件？
GroupDocs.Parser 支援多種文件格式，包括 Word、PDF、Excel、PowerPoint 等。