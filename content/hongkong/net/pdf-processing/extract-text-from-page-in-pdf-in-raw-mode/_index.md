---
title: 在原始模式下從 PDF 頁面中提取文本
linktitle: 在原始模式下從 PDF 頁面中提取文本
second_title: GroupDocs.Parser .NET API
description: 使用 C# 中的 GroupDocs.Parser 從 PDF 中提取文字。使用這個強大的 .NET 程式庫學習高效的 PDF 文字擷取。
weight: 16
url: /zh-hant/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# 在原始模式下從 PDF 頁面中提取文本

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 使用原始模式從 PDF 文件的頁面中擷取文字。 GroupDocs.Parser 是一個功能強大的工具，使開發人員能夠以程式設計方式處理各種文件格式。
## 先決條件
在開始本教學之前，請確保您具備以下條件：
- Visual Studio 安裝在您的電腦上。
- C# 程式設計基礎知識。
- GroupDocs.Parser for .NET 函式庫，您可以[在這裡下載](https://releases.groupdocs.com/parser/net/).
- 用於測試目的的範例 PDF 檔案。

## 導入命名空間
首先，確保在 C# 專案中導入必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先，實例化`Parser`類，透過提供範例 PDF 文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //你的程式碼放在這裡
}
```
## 第 2 步：取得文件資訊並迭代頁面
接下來，檢索文件資訊並迭代每個頁面以提取文字。
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    //您的文字擷取程式碼位於此處
}
```
## 第 3 步：從每個頁面中提取文本
在循環內，使用`GetText`方法從每個頁面提取文字並列印它。
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Parser for .NET 以原始模式從 PDF 頁面中擷取文字。這個過程涉及創建一個`Parser`例如，獲取文件信息，迭代每個頁面，並使用`GetText`方法。

## 常見問題解答
### 什麼是 .NET 的 GroupDocs.Parser？
GroupDocs.Parser for .NET 是一個文件解析 API，允許開發人員以程式設計方式從各種文件格式中提取文字、元資料和其他資訊。
### 如何下載 .NET 版 GroupDocs.Parser？
您可以從以下位置下載該程式庫[集團文件網站](https://releases.groupdocs.com/parser/net/).
### 有免費試用嗎？
是的，您可以存取 GroupDocs.Parser for .NET 的免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到對 GroupDocs.Parser for .NET 的支援？
如需技術援助和社區支持，請訪問[集團文檔論壇](https://forum.groupdocs.com/c/parser/17).
### 如何購買 GroupDocs.Parser for .NET 的授權？
您可以從以下位置購買許可證[購買頁面](https://purchase.groupdocs.com/buy)或獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).