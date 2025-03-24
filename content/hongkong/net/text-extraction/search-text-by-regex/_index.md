---
title: 透過正規表示式 (Regex) 搜尋文本
linktitle: 透過正規表示式 (Regex) 搜尋文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 在文件中使用正規表示式搜尋文字。輕鬆提取特定內容。
weight: 23
url: /zh-hant/net/text-extraction/search-text-by-regex/
---
## 介紹
在本教程中，我們將深入研究使用 GroupDocs.Parser for .NET 透過正規表示式 (Regex) 在文件中搜尋文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員從各種文件格式（例如 PDF、DOCX、XLSX 等）中提取文字和元資料。使用正規表示式搜尋文字對於有效率地尋找文件中的模式或特定內容特別有用。
## 先決條件
在深入學習本教學之前，請確保您具備以下條件：
1. Visual Studio：安裝 Visual Studio IDE 以進行 .NET 開發。
2.  GroupDocs.Parser for .NET：從下列位置下載並安裝 GroupDocs.Parser for .NET[這裡](https://releases.groupdocs.com/parser/net/).
3. 範例文件：準備範例文件（PDF、DOCX 等）以測試搜尋功能。

## 導入命名空間
首先，首先在 C# 程式碼中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
實例化`Parser`類別透過提供範例檔案的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //代碼放在這裡
}
```
代替`"YourSampleFile.pdf"`與您的實際文件的路徑。
## 步驟 2： 使用正規表示式搜尋
使用正規表示式模式定義並執行搜尋。例如，要在文件中尋找數字序列（例如整數）：
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
在這個例子中，`[0-9]+`是符合一個或多個數字的正規表示式模式。
## 第 3 步：檢查搜尋支持
驗證文檔類型是否支援搜尋操作：
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## 第 4 步：迭代搜尋結果
迭代搜尋結果並處理每個匹配項：
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
此循環將列印文件中找到的位置和匹配文字。

## 結論
總之，利用 GroupDocs.Parser for .NET 可以使用正規表示式跨各種文件格式進行高效率的文字搜尋。透過遵循本指南，開發人員可以將文件解析和基於正規表示式的文字提取無縫整合到他們的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Parser 可以在加密文件中搜尋嗎？
不可以，GroupDocs.Parser 無法在加密或受密碼保護的文件中進行搜尋。
### GroupDocs.Parser 支援 OCR（光學字元辨識）嗎？
不，GroupDocs.Parser 不執行 OCR。它依賴於從文件內部結構中提取文字。
### 我可以使用正規表示式搜尋複雜模式嗎？
是的，GroupDocs.Parser 支援成熟的正規表示式，因此可以在文件中進行複雜的模式匹配。
### 文字擷取支援哪些文件格式？
GroupDocs.Parser 支援多種格式，包括 PDF、DOCX、XLSX、PPTX 等。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 與 .NET Core 相容，可進行跨平台開發。