---
title: 以原始模式從 Excel 工作表中擷取文本
linktitle: 以原始模式從 Excel 工作表中擷取文本
second_title: GroupDocs.Parser .NET API
description: 在這個綜合教學中了解如何使用 GroupDocs.Parser for .NET 從 Excel 工作表中擷取文字。下載並開始解析。
weight: 15
url: /zh-hant/net/excel-document-processing/extract-text-from-excel-sheet-in-raw-mode/
type: docs
---
# 以原始模式從 Excel 工作表中擷取文本

## 介紹
在本教學中，我們將探討如何在原始模式下使用 GroupDocs.Parser for .NET 從 Excel 工作表中擷取文字。 GroupDocs.Parser 是一個功能強大的 API，可讓開發人員使用各種文件格式（包括 Excel 文件）進行文字擷取和分析。我們將介紹先決條件、匯入命名空間，並分解每個步驟來示範從 Excel 工作表中提取文字的過程。
## 先決條件
在開始之前，請確保您已設定以下先決條件：
- Visual Studio：在您的電腦上安裝 Visual Studio IDE。
-  GroupDocs.Parser for .NET：從下列位置下載並安裝 GroupDocs.Parser：[下載頁面](https://releases.groupdocs.com/parser/net/).
- 範例 Excel 檔案：準備一個用於文字擷取的範例 Excel 檔案。

## 導入命名空間
首先將必要的命名空間匯入到您的 C# 專案中以存取 GroupDocs.Parser 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先，建立一個實例`Parser`類，透過提供範例 Excel 檔案的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    //您的文字擷取程式碼將位於此處
}
```
## 步驟2：取得文件資訊
使用檢索文件資訊`GetDocumentInfo()`方法：
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## 第 3 步：迭代工作表
循環遍歷 Excel 檔案中的每個工作表：
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.RawPageCount));
    
    //從每張紙中提取文字的代碼將位於此處
}
```
## 第 4 步：從每張紙中提取文本
使用a從每張紙中提取文本`TextReader`:
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 結論
在本教學中，我們介紹如何使用 GroupDocs.Parser for .NET 從 Excel 工作表中擷取文字。透過執行上述步驟，您可以有效率地從 Excel 檔案中擷取文字數據，以便在 .NET 應用程式中進行進一步處理或分析。

## 常見問題解答
### GroupDocs.Parser 可以從其他文件格式中提取文字嗎？
是的，GroupDocs.Parser 支援多種文件格式，包括 Word、PDF、PowerPoint 等。
### GroupDocs.Parser 適合處理大型 Excel 檔案嗎？
是的，GroupDocs.Parser 旨在有效地處理大型文件。
### 在哪裡可以找到有關 GroupDocs.Parser 的更多文件？
您可以參考[文件](https://tutorials.groupdocs.com/parser/net/)取得詳細資訊和範例。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
訪問[這個連結](https://purchase.groupdocs.com/temporary-license/)申請臨時許可證。
### GroupDocs.Parser 是否提供客戶支援？
是的，您可以尋求協助或提出問題[集團文檔論壇](https://forum.groupdocs.com/c/parser/17).