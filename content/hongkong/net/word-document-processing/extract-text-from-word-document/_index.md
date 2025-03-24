---
title: 從 Word 文件中提取文本
linktitle: 從 Word 文件中提取文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從 Word 文件中提取文字。帶有程式碼範例的分步指南。
weight: 15
url: /zh-hant/net/word-document-processing/extract-text-from-word-document/
---

# 從 Word 文件中提取文本

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從 Word 文件中擷取文字。 GroupDocs.Parser 是一個功能強大的 .NET 程式庫，可讓開發人員處理各種文件格式，包括 Word 文件、PDF 等。在本指南結束時，您將能夠使用簡單的 C# 程式碼有效地從 Word 文件中提取文字。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
- Visual Studio（或任何首選的 C# 開發環境）
- 安裝了 .NET 函式庫的 GroupDocs.Parser（下載[這裡](https://releases.groupdocs.com/parser/net/）)
- C# 程式設計基礎知識

## 導入命名空間
首先，您需要在 C# 專案中匯入必要的命名空間以存取 GroupDocs.Parser 功能。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## 第 1 步：建立 Parser 類別的實例
首先建立一個實例`Parser`類，提供 Word 文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //您的文字擷取程式碼將位於此處
}
```
代替`"YourSampleFile.docx"`與實際 Word 文件的路徑。
## 第 2 步：將文字提取到 TextReader 中
內`using`塊的`Parser`實例，使用`GetText()`方法將文字內容提取到`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    //您的文字處理程式碼將放在此處
}
```
## 第 3 步：讀取並顯示提取的文本
現在，在`TextReader`區塊，您可以閱讀並列印從 Word 文件中提取的文字。
```csharp
using (TextReader reader = parser.GetText())
{
    //讀取提取的文字並列印
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
恭喜！您已了解如何使用 GroupDocs.Parser for .NET 從 Word 文件中提取文字。這個簡單但功能強大的程式庫可讓您將文字擷取功能有效地整合到您的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Parser 是否與所有版本的 .NET 相容？
是的，GroupDocs.Parser for .NET 與 .NET Framework 4.6.1 及更高版本相容。
### 我可以從加密或受密碼保護的 Word 文件中提取文字嗎？
GroupDocs.Parser 支援從受密碼保護的 Word 文件中提取文字。
### GroupDocs.Parser 是否支援 Word 文件以外的其他文件格式？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、Excel、PowerPoint 等。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以為 GroupDocs.Parser 申請臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到有關 GroupDocs.Parser 的其他支援或提出問題？
您可以造訪 GroupDocs.Parser 論壇[這裡](https://forum.groupdocs.com/c/parser/17)以尋求支持和討論。