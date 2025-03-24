---
title: 從 Word 文件中提取圖像
linktitle: 從 Word 文件中提取圖像
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從 Word 文件中擷取圖片。本教程提供了將圖像整合到 .NET 中的逐步指南。
weight: 11
url: /zh-hant/net/word-document-processing/extract-images-from-word-document/
---
## 介紹
在本教學中，您將學習如何使用 GroupDocs.Parser for .NET 從 Word 文件中提取圖像。 GroupDocs.Parser 是一個功能強大的 .NET 程式庫，可讓您從包括 Word (DOCX) 在內的各種文件格式中解析和提取文字、元資料、圖像等。
## 先決條件
在開始之前，請確保您已設定以下先決條件：
- Visual Studio 安裝在您的電腦上。
- C# 程式設計基礎知識。
- 安裝了 .NET 函式庫的 GroupDocs.Parser。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
## 導入命名空間
首先，您需要在 C# 專案中匯入必要的命名空間才能使用 GroupDocs.Parser 功能：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
現在，讓我們把從 Word 文件中提取圖像的過程分解為簡單的步驟：
## 第 1 步：建立 Parser 類別的實例
您將首先建立一個實例`Parser`類，提供 Word 文件的路徑作為輸入。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //圖像提取程式碼在這裡
}
```
## 步驟 2：從 Word 文件中擷取影像
接下來，使用`GetImages()`的方法`Parser`物件從文件中提取圖像。
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 第 3 步：定義圖像保存選項
指定保存擷取的影像的選項。例如，您可以選擇圖像格式（例如 PNG）並配置其他設定。
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 第 4 步：迭代提取的圖像並保存
迭代每個提取的圖像並使用指定的選項將其保存到文件中。
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
在本教學中，您學習如何使用 GroupDocs.Parser for .NET 從 Word 文件中擷取圖片。透過執行這些步驟，您可以輕鬆地將文件解析和影像擷取功能整合到您的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Parser 可以從 Word 以外的其他文件格式中提取圖片嗎？
是的，GroupDocs.Parser 支援各種文件格式，包括 PDF、PowerPoint、Excel 等。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以從以下位置取得用於測試目的的臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到更多關於 GroupDocs.Parser for .NET 的文件？
你可以參考完整的文檔[這裡](https://tutorials.groupdocs.com/parser/net/).
### GroupDocs.Parser 是否有免費試用版？
是的，您可以透過免費試用版探索 GroupDocs.Parser 的功能[這裡](https://releases.groupdocs.com/).
### 我該如何獲得與 GroupDocs.Parser 相關的支援或提出問題？
您可以在以下位置發表您的疑問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).