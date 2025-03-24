---
title: 按關鍵字搜尋 Word 文件中的文本
linktitle: 按關鍵字搜尋 Word 文件中的文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 在 Word 文件中搜尋文字。高效提取特定關鍵字。
weight: 18
url: /zh-hant/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# 按關鍵字搜尋 Word 文件中的文本

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 使用 C# 在 Word 文件中搜尋特定文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員從各種文件格式（包括 Word 文件）中提取文字和元資料。
## 先決條件
在開始之前，請確保您具備以下先決條件：
1. 開發環境：安裝Visual Studio或其他相容的IDE。
2.  GroupDocs.Parser 函式庫：從下列位置下載並安裝 GroupDocs.Parser for .NET 函式庫[網站](https://releases.groupdocs.com/parser/net/).
3. 範例 Word 文件：準備一個範例 Word 文件以用於文字搜尋。

## 導入命名空間
首先在 C# 專案中導入必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## 第 1 步：建立 Parser 類別的實例
首先，建立一個實例`Parser`透過傳遞範例 Word 文件的路徑來建立類別。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //代碼放在這裡
}
```
## 第 2 步：搜尋關鍵字
接下來，使用`Search`的方法`Parser`類別來搜尋文件中的特定關鍵字。
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
代替`"keyword"`以及您要在文件中搜尋的文字。
## 第 3 步：迭代搜尋結果
使用迭代搜尋結果`foreach`循環訪問每個`SearchResult`目的。
```csharp
foreach (SearchResult result in searchResults)
{
    //處理每個搜尋結果的程式碼
}
```
## 第 4 步：訪問搜尋結果詳細信息
在循環中，您可以使用以下命令存取每個搜尋結果的位置和文字`Position`和`Text`的屬性`SearchResult`目的。
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
此程式碼片段列印索引（`Position`）和找到的文字（`Text`) 將每個搜尋結果傳送到控制台。

## 結論
在本教學中，您學習如何使用 GroupDocs.Parser for .NET 在 Word 文件中搜尋特定文字。該庫提供了一種以程式設計方式從各種文件格式中提取和操作內容的便捷方法。

## 常見問題解答
### GroupDocs.Parser 可以處理 Word 以外的其他文件格式嗎？
是的，GroupDocs.Parser 支援多種格式，包括 PDF、Excel、PowerPoint 等。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 與 .NET Framework 和 .NET Core 也相容。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以向以下機構申請臨時許可證[GroupDocs 購買頁面](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到有關 GroupDocs.Parser 的其他支援或提出問題？
參觀[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)以獲得社區支持和討論。
### 我可以在購買前免費試用 GroupDocs.Parser 嗎？
是的，您可以從以下位置下載免費試用版[GroupDocs 發布頁面](https://releases.groupdocs.com/).