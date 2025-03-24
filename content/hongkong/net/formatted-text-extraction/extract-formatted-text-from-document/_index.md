---
title: 從文件中提取格式化文本
linktitle: 從文件中提取格式化文本
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中擷取格式化文字。為您的應用程式提供簡單且有效率的文字擷取。
weight: 10
url: /zh-hant/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從各種類型的文件中擷取格式化文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員以簡化且有效率的方式處理文件。閱讀本指南後，您將能夠將文字擷取功能無縫整合到您的 .NET 應用程式中。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- Visual Studio：確保您的系統上安裝了 Visual Studio。
-  GroupDocs.Parser for .NET：下載並安裝 GroupDocs.Parser 函式庫[這裡](https://releases.groupdocs.com/parser/net/).
- 文件範例：準備用於文字擷取的範例文件（例如 PDF、DOCX）。
## 導入命名空間
首先，在 C# 程式碼中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 第 1 步：建立 Parser 類別的實例
首先初始化一個`Parser`物件與範例文件的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //文字提取程式碼放在這裡
}
```
代替`"YourSampleFile.pdf"`以及文檔文件的路徑。

## 第 2 步：提取格式化文本
內`using`塊，使用`GetFormattedText`從文件中提取格式化文字的方法。使用指定所需的輸出格式（例如，HTML）`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //將格式化文字擷取到閱讀器中
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        //檢查是否支援提取
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            //讀取並顯示提取的文本
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## 結論
恭喜！您已了解如何使用 GroupDocs.Parser for .NET 從文件中提取格式化文字。這個多功能庫為您的應用程式中的文字處理和分析提供了可能性。

## 常見問題解答
### Q：GroupDocs.Parser 可以從受密碼保護的文件中提取文字嗎？
答：是的，GroupDocs.Parser 支援從受密碼保護的文件中提取文字。
### Q：GroupDocs.Parser 支援哪些文檔格式？
答：GroupDocs.Parser 支援多種格式，包括 PDF、DOCX、XLSX、PPTX 等。
### Q：如何取得 GroupDocs.Parser 的臨時許可證？
答：您可以從以下機構獲得臨時許可證：[這裡](https://purchase.groupdocs.com/temporary-license/).
### Q：GroupDocs.Parser 是否支援從文件中提取映像？
答：是的，GroupDocs.Parser 支援圖像擷取和文字擷取。
### Q：在哪裡可以找到有關 GroupDocs.Parser 的其他支援或提出問題？
答：訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)以尋求支持和討論。