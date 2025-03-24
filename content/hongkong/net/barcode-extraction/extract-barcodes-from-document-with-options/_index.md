---
title: 使用選項從文件中提取條碼
linktitle: 使用選項從文件中提取條碼
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中提取條碼。包含程式碼範例和常見問題的綜合教學。
weight: 14
url: /zh-hant/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## 介紹
在本教學中，我們將逐步介紹使用 GroupDocs.Parser for .NET 從文件中擷取條碼的流程。 GroupDocs.Parser 是一個功能強大的程式庫，可讓您從各種文件格式（例如 PDF、Microsoft Word、Excel 等）中提取文字、元資料和條碼。
## 先決條件
在開始之前，請確保您具備以下先決條件：
1. 開發環境：確保您的電腦上安裝了 Visual Studio。
2.  GroupDocs.Parser 函式庫：下載並安裝適用於 .NET 函式庫的 GroupDocs.Parser[這裡](https://releases.groupdocs.com/parser/net/).
3. 範例文件：準備包含要擷取的條碼的範例文件（例如 PDF、DOCX）。

## 導入命名空間
首先，您需要將必要的命名空間匯入 C# 專案中以利用 GroupDocs.Parser 功能。
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## 第 1 步：建立 Parser 類別的實例
首先，建立一個實例`Parser`透過傳遞範例文件的路徑來建立類別。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //後續步驟中要新增的程式碼
}
```
## 第 2 步：檢查條碼提取支持
接下來，使用以下命令檢查文件是否支援條碼擷取`Features`的財產`Parser`實例。
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## 第 3 步：定義條碼提取選項
現在，使用指定條碼提取選項`BarcodeOptions`。您可以設定品質模式和條碼類型等參數。
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## 步驟 4：從文件中提取條碼
使用`GetBarcodes`的方法`Parser`類別根據定義的選項提取條碼。
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## 第 5 步：迭代並顯示提取的條碼
最後，迭代提取的條碼並顯示其頁面索引和值。
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Parser for .NET 從文件中擷取條碼。這個過程涉及創建一個`Parser`例如，定義提取選項，並迭代提取的條碼。 GroupDocs.Parser 簡化了從各種文件格式中提取條碼的任務，從而在 .NET 應用程式中實現高效的文件處理。

## 常見問題解答
### GroupDocs.Parser可以從PDF文件中提取條碼嗎？
是的，GroupDocs.Parser 支援從 PDF 文件以及 DOCX、XLSX 等其他格式中提取條碼。
### GroupDocs.Parser 支援哪些條碼類型？
GroupDocs.Parser 支援各種條碼類型，包括 QR 碼、Code 39、Code 128 等。
### GroupDocs.Parser 是否需要商業用途許可證？
是的，商業用途需要有效的許可證。您可以從以下位置取得許可證[這裡](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser適合批次處理文件嗎？
是的，GroupDocs.Parser 可以有效地處理文件的批次處理，以進行文字提取、元資料檢索和條碼提取。
### 在哪裡可以找到 GroupDocs.Parser 的技術支援？
您可以透過以下方式獲得技術支援或提問[集團文檔論壇](https://forum.groupdocs.com/c/parser/17).