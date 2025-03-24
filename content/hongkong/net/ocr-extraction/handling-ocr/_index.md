---
title: 處理 OCR
linktitle: 處理 OCR
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 處理 OCR。有效率地從圖像和掃描文件中提取文字。
weight: 11
url: /zh-hant/net/ocr-extraction/handling-ocr/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 高效處理光學字元辨識 (OCR) 任務。該庫提供了從文件中提取文字的強大工具，並且透過 OCR，您甚至可以從圖像或掃描文件中提取文字。讓我們逐步深入了解這個過程。
## 先決條件
在開始之前，請確保您已進行以下設定：
- GroupDocs.Parser for .NET Library：從以下位置下載該程式庫[這裡](https://releases.groupdocs.com/parser/net/).
- 您的範例文件：準備一個要從中提取文字的範例文件（文件或圖像）。
- C# 和 .NET 環境的基礎知識。

## 導入命名空間
首先，您需要匯入必要的命名空間以在 .NET 應用程式中使用 GroupDocs.Parser 功能。
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
## 第 1 步：使用 OCR 連接器建立解析器設置
初始化`ParserSettings`與 OCR 連接器的類別。例如，在本地使用 Aspose OCR。
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 步驟 2：配置 OCR 選項
設立一個`OcrEventHandler`處理 OCR 處理期間的警告。
```csharp
OcrEventHandler handler = new OcrEventHandler();
OcrOptions ocrOptions = new OcrOptions(handler);
```
## 步驟 3：設定文字擷取選項
創造`TextOptions`啟用基於 OCR 的文字擷取。
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 第 4 步：使用 OCR 提取文本
實例化`Parser`類別與設定並使用 OCR 提取文字。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    using (TextReader reader = parser.GetText(options))
    {
        if (reader == null)
        {
            Console.WriteLine("Text extraction isn't supported.");
        }
        else
        {
            Console.WriteLine(reader.ReadToEnd());
        }
    }
    if (handler.HasWarnings)
    {
        Console.WriteLine("The following warnings occurred during text recognition:");
        foreach (string w in handler.Warnings)
        {
            Console.WriteLine("\t* " + w);
        }
    }
    else
    {
        Console.WriteLine("Text recognition was performed without any warnings.");
    }
}
```

## 結論
透過執行這些步驟，您可以利用 GroupDocs.Parser for .NET 在應用程式中有效處理 OCR 任務。利用該庫提供的強大功能，可以無縫地從圖像或掃描文件中提取文字。

## 常見問題解答
### GroupDocs.Parser for .NET 是否與不同的檔案格式相容？
是的，GroupDocs.Parser 支援多種檔案格式，包括 PDF、DOCX、PPTX、XLSX、映像（JPEG、PNG、TIFF）等。
### 我可以在我的商業專案中使用 GroupDocs.Parser for .NET 嗎？
是的，您可以在購買許可證後將 GroupDocs.Parser for .NET 整合到您的商業應用程式中。
### GroupDocs.Parser 是否處理加密或受密碼保護的檔案？
GroupDocs.Parser 可以從受密碼保護的 PDF 文件中解析和提取文字。
### GroupDocs.Parser for .NET 是否有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到與 GroupDocs.Parser for .NET 相關的支援或提出問題？
您可以訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)任何支援查詢或討論。