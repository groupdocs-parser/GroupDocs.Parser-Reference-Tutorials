---
title: 從串流載入文檔
linktitle: 從串流載入文檔
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser 從 .NET 中的各種文件格式中擷取文字。帶有程式碼範例的分步指南。
weight: 12
url: /zh-hant/net/document-loading/load-document-from-stream/
---
## 介紹
在 .NET 應用程式的文檔處理領域，從各種文件格式中提取文字是常見的要求。 GroupDocs.Parser for .NET 提供了一個強大的解決方案，可以從各種文件中無縫解析和提取文字。本教學將指導您逐步完成使用 GroupDocs.Parser 從文件中提取文字的過程。
## 先決條件
在深入使用 GroupDocs.Parser for .NET 之前，請確保您已進行以下設定：
- 開發環境：Visual Studio 或任何其他.NET 開發環境。
-  GroupDocs.Parser for .NET 套件：從下列位置下載並安裝 GroupDocs.Parser for .NET 程式庫[這裡](https://releases.groupdocs.com/parser/net/).
- 文件範例：準備好範例文件以進行文字擷取。
## 導入命名空間
首先將必要的命名空間匯入到 .NET 專案中以存取 GroupDocs.Parser 功能。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

以下步驟示範如何使用 GroupDocs.Parser 從流程中擷取文件中的文字。
## 第 1 步：從流程載入文檔
```csharp
//創建流
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    //使用流建立 Parser 類別的實例
    using (Parser parser = new Parser(stream))
    {
        //將文字擷取到閱讀器中
        using (TextReader reader = parser.GetText())
        {
            //列印文件中的文字
            //如果不支援文字擷取，則 reader 將為 null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
在這個例子中：
- 我們開啟文檔文件的文件流（`YourSampleFile.docx`）。
- 初始化一個`Parser`與流的實例。
- 使用`parser.GetText()`檢索一個`TextReader`包含提取的文字。
- 如果文件格式不支援文字擷取，則列印提取的文字或訊息。
## 結論
GroupDocs.Parser for .NET 簡化了從各種文件格式中提取文字的過程，使開發人員能夠在其應用程式中有效地處理和利用文字內容。透過遵循本教學中概述的步驟，您可以將文件文字擷取功能無縫整合到您的 .NET 專案中。

## 常見問題解答
### GroupDocs.Parser for .NET 支援哪些文件格式？
GroupDocs.Parser 支援多種文件格式，包括 DOCX、PDF、XLSX、PPTX、EPUB 等。
### GroupDocs.Parser 可以從文件中提取圖像或元資料嗎？
是的，GroupDocs.Parser 可以從各種文件類型中提取圖像、元資料和文字。
### GroupDocs.Parser 與 .NET Core 應用程式相容嗎？
是的，GroupDocs.Parser 與 .NET Framework 和 .NET Core 應用程式相容。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以從以下地址取得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到有關 GroupDocs.Parser 的更多支援或文件？
如需更多支持，請訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)或參考[文件](https://tutorials.groupdocs.com/parser/net/).
