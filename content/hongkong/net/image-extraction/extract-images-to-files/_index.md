---
title: 將圖像提取到文件
linktitle: 將圖像提取到文件
second_title: GroupDocs.Parser .NET API
description: 使用 GroupDocs.Parser for .NET 輕鬆從 PDF 和 DOCX 等各種文件類型中擷取影像。簡化您的文件解析任務。
type: docs
weight: 13
url: /zh-hant/net/image-extraction/extract-images-to-files/
---
## 介紹
在本教學中，您將學習如何使用 GroupDocs.Parser for .NET 從各種文件格式（例如 PDF、Word、Excel 和 PowerPoint）中提取圖像。 GroupDocs.Parser 是一個功能強大的程式庫，使開發人員能夠以簡單的方式從文件中解析和提取文字、元資料、圖像等。本指南將引導您完成使用 C# 擷取影像並將其儲存為單獨檔案的過程。
## 先決條件
在開始之前，請確保您具備以下先決條件：
1. Visual Studio：確保您的系統上安裝了 Visual Studio。
2.  GroupDocs.Parser for .NET：從下列位置下載並安裝 GroupDocs.Parser for .NET[這裡](https://releases.groupdocs.com/parser/net/).
3. 範例文件：準備要從中提取影像的範例文件（例如，PDF、DOCX、XLSX）。

## 導入命名空間
首先，在 C# 程式碼中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立解析器實例
實例化`Parser`類，透過提供範例文檔的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //代碼放在這裡
}
```
## 步驟 2：從文件中擷取影像
使用`GetImages()`的方法`Parser`物件從文件中檢索影像。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 第 3 步：檢查對影像擷取的支持
驗證文件是否支援影像擷取。
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## 步驟 4：設定影像儲存選項
指定格式（`ImageFormat`），您要在其中保存提取的圖像（例如，PNG）。
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 第 5 步：迭代並儲存圖像
循環遍歷提取的圖像並將每個圖像保存到文件中。
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    //將圖片儲存為 PNG 文件
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## 結論
在本教學中，您學習如何使用 GroupDocs.Parser for .NET 使用 C# 從文件中擷取圖像。這個強大的程式庫簡化了從各種文件格式中解析和提取資料的過程，使其成為 .NET 應用程式中文件處理任務的重要工具。

## 常見問題解答
### 我可以從受密碼保護的文件中提取圖像嗎？
是的，如果您在解析過程中提供正確的密碼，GroupDocs.Parser 支援從受密碼保護的文件中提取圖像。
### 影像擷取支援哪些文件格式？
GroupDocs.Parser 支援多種格式，包括 PDF、DOCX、XLSX、PPTX、EPUB 等。
### 影像擷取過程中出現異常如何處理？
您可以在程式碼中實現錯誤處理，以擷取和管理影像擷取過程中可能發生的異常。
### GroupDocs.Parser適合批次處理文件嗎？
是的，您可以使用 GroupDocs.Parser 批次處理多個文檔，有效地提取圖像和其他資料。
### GroupDocs.Parser 是否為掃描文件提供 OCR 功能？
GroupDocs.Parser 目前不支援 OCR（光學字元辨識），但擅長解析文件中的結構化資料。