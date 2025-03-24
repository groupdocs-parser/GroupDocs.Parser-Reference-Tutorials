---
title: 擷取純文字
linktitle: 擷取純文字
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中提取純文字。將文字擷取整合到您的應用程式中的簡單步驟。
weight: 14
url: /zh-hant/net/formatted-text-extraction/extract-plain-text/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從各種文件格式中擷取純文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員無縫地處理文檔，有效地提取文字和元資料。本指南將引導您完成在 .NET 應用程式中整合和使用該程式庫的必要步驟。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1. Visual Studio：在開發電腦上安裝 Visual Studio。
2.  GroupDocs.Parser 函式庫：從下列位置下載並安裝適用於 .NET 的 GroupDocs.Parser[下載頁面](https://releases.groupdocs.com/parser/net/).
3. 範例文件：準備用於文字擷取的範例文件（例如 DOCX、PDF、TXT）。

## 導入命名空間
首先，在 C# 專案中包含必要的命名空間以存取 GroupDocs.Parser 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 第 1 步：初始化解析器
建立一個實例`Parser`透過指定範例文件的路徑來建立類別。
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    //文字擷取程式碼位於此處
}
```
## 第 2 步：提取格式化文本
內`using`塊的`Parser`，使用提取格式化文本`GetFormattedText`方法與`PlainText`模式。
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    //用於讀取和處理提取的文本的程式碼
}
```
## 第 3 步：讀取提取的文本
使用`TextReader`實例讀取並輸出提取的純文字。
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 結論
在本教程中，我們介紹了使用 GroupDocs.Parser for .NET 從文件中提取純文字的基礎知識。透過執行這些步驟，您可以將文字擷取功能無縫整合到您的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Parser 是否相容於多種文件格式？
是的，GroupDocs.Parser 支援多種文件格式，包括 DOCX、PDF、TXT 等。
### 我可以使用 GroupDocs.Parser 提取元資料和文字嗎？
當然，GroupDocs.Parser 允許提取文字內容和元數據，如作者、創建日期等。
### GroupDocs.Parser 是否有免費試用版？
是的，您可以存取 GroupDocs.Parser 的免費試用版[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到 GroupDocs.Parser 的技術支援？
如需技術協助，請造訪 GroupDocs.Parser[論壇](https://forum.groupdocs.com/c/parser/17).
### 如何獲得 GroupDocs.Parser 的臨時許可證？
若要取得臨時許可證，請造訪 GroupDocs.Parser[臨時許可證頁面](https://purchase.groupdocs.com/temporary-license/).