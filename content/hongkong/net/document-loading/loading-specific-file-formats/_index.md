---
title: 載入特定文件格式
linktitle: 載入特定文件格式
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser 從 .NET 中的各種文件格式中提取文字。高效文件處理的逐步教學。
weight: 14
url: /zh-hant/net/document-loading/loading-specific-file-formats/
type: docs
---
# 載入特定文件格式

## 介紹
在 .NET 開發領域，從各種文件格式解析和提取文字是一個常見的需求。 GroupDocs.Parser for .NET 提供了強大的工具來簡化此任務。本教學將指導您逐步使用 GroupDocs.Parser 從特定文件格式載入和提取文字。
## 先決條件
在深入學習本教學之前，請確保您具備以下條件：
- C# 和 .NET 開發的基礎知識。
- 安裝了 Visual Studio 或其他用於 .NET 開發的 IDE。
- 用於 .NET 函式庫的 GroupDocs.Parser。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
- 採用受支援格式之一（例如 Word、PDF、Markdown）的範例文件。

## 導入命名空間
首先將必要的命名空間加入 C# 檔案：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```

請按照以下步驟從特定文件格式載入和提取文字：
## 第 1 步：開啟檔案流
首先，打開範例文件的流：
```csharp
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    //繼續下一步
}
```
代替`"YourSampleFile.docx"`以及範例文件的路徑。
## 步驟2：建立解析器實例
實例化`Parser`類別與開啟的流並指定檔案格式：
```csharp
using (Parser parser = new Parser(stream, new LoadOptions(FileFormat.Docx)))
{
    //繼續下一步
}
```
代替`FileFormat.Docx`根據您的範例文件使用適當的文件格式枚舉（例如，`FileFormat.Pdf`, `FileFormat.Markup`對於 Markdown）。
## 第 3 步：檢查文字擷取支持
驗證載入的文件格式是否支援文字擷取：
```csharp
if (!parser.Features.Text)
{
    Console.WriteLine("Text extraction isn't supported.");
    return;
}
```
## 步驟 4：從文件中提取文本
使用`parser.GetText()`獲得一個`TextReader`實例並讀取提取的文字：
```csharp
using (TextReader reader = parser.GetText())
{
    string extractedText = reader.ReadToEnd();
    Console.WriteLine(extractedText);
}
```

## 結論
GroupDocs.Parser for .NET 簡化了從各種文件格式中提取文字的過程，從而在 C# 應用程式中實現高效的文件處理。透過學習本教程，您已經了解如何使用 GroupDocs.Parser 載入特定文件格式並提取文字。

## 常見問題解答
### GroupDocs.Parser for .NET 可以免費使用嗎？
GroupDocs.Parser for .NET 提供免費和付費授權選項。你可以探索它們[這裡](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser for .NET 支援哪些文件格式？
 GroupDocs.Parser 支援多種文件格式，包括 Word、PDF、Excel、PowerPoint、Markdown 等。參考文檔[這裡](https://tutorials.groupdocs.com/parser/net/)取得完整清單。
### 我可以在購買前試用 GroupDocs.Parser for .NET 嗎？
是的，您可以存取免費試用版[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到有關 GroupDocs.Parser for .NET 的支援或提出問題？
造訪 GroupDocs.Parser 論壇[這裡](https://forum.groupdocs.com/c/parser/17)如有任何疑問或支持需求。
### 如何取得 GroupDocs.Parser for .NET 的臨時授權？
您可以獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).