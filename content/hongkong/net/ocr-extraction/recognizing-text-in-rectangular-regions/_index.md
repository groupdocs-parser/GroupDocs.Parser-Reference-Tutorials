---
title: 辨識矩形區域中的文字
linktitle: 辨識矩形區域中的文字
second_title: GroupDocs.Parser .NET API
description: 了解如何使用具有 OCR 功能的 GroupDocs.Parser for .NET 識別文件特定區域中的文字。
type: docs
weight: 14
url: /zh-hant/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 識別文件特定矩形區域內的文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員從各種文件格式（包括 PDF、Word、Excel 和 PowerPoint）中提取文字、元資料等。
## 先決條件
在開始之前，請確保您已進行以下設定：
-  GroupDocs.Parser for .NET：從以下位置下載並安裝該程式庫[這裡](https://releases.groupdocs.com/parser/net/).
- 開發環境：Visual Studio 或任何其他 .NET IDE。
- 範例文件：擁有包含要識別的文字的範例文件（例如 PDF、DOCX）。

## 導入命名空間
首先，您需要將必要的命名空間匯入到 C# 程式碼中：
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：初始化解析器設定
首先設定`ParserSettings`與 OCR 連接器。在這裡，我們將使用 Aspose OCR 本機連接器：
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 步驟2：建立解析器實例
接下來，實例化`Parser`具有先前定義的設定的類別：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    //代碼在這裡繼續
}
```
代替`"YourSampleFile.pdf"`以及您的文件的路徑。
## 第 3 步：定義 OCR 矩形
在文件中定義一個將執行文字辨識的矩形。例如，一個矩形從`(0, 0)`與寬度`400`和身高`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## 步驟 4：設定文字辨識選項
創造`TextOptions`指定 OCR 用法以及定義的矩形：
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 第 5 步：使用 OCR 提取文本
使用`GetText`的方法`Parser`已配置的實例`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    //讀取提取的文字或處理“不支援”的情況
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## 結論
在本教學中，我們示範如何利用 GroupDocs.Parser for .NET 使用 OCR 從文件中的特定矩形區域提取文字。該過程可以進一步自訂並整合到各種應用程式中，以執行自動文字擷取任務。

## 常見問題解答
### GroupDocs.Parser 可以從掃描文件中提取文字嗎？
是的，GroupDocs.Parser 支援 OCR（光學字元辨識）從掃描文件中提取文字。
### GroupDocs.Parser 支援哪些文件格式？
GroupDocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 如何處理不支援文字擷取的文件？
您可以使用檢查是否支援文字擷取`TextReader`傳回的實例`parser.GetText(options)`.
### GroupDocs.Parser適合大規模文字擷取任務嗎？
是的，GroupDocs.Parser 旨在高效處理大規模文字擷取任務。
### 在哪裡可以獲得 GroupDocs.Parser 相關問題的支援？
如需支援和討論，請訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).