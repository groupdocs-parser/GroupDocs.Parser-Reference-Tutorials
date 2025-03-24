---
title: 從本機磁碟載入文檔
linktitle: 從本機磁碟載入文檔
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從各種文件格式中擷取文字。使用 C# 輕鬆有效率地擷取文字。
weight: 11
url: /zh-hant/net/document-loading/load-document-from-local-disk/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從文件中擷取文字。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員以程式設計方式解析各種文件格式並提取文字內容。我們將介紹開始使用此庫進行文字擷取的必要步驟。
## 先決條件
在開始之前，請確保您已安裝以下先決條件：
- Visual Studio 安裝在您的系統上。
- C# 程式語言的基礎知識。
- 安裝了 .NET 函式庫的 GroupDocs.Parser（下載[這裡](https://releases.groupdocs.com/parser/net/)）。

## 導入命名空間
首先，您需要將必要的命名空間匯入到您的 C# 專案中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## 步驟1：從本機磁碟載入文檔
首先從本機磁碟載入文件。代替`"Your Sample File"`與目標文檔的路徑。
```csharp
//設定檔案路徑
string filePath = "Your Sample File";
//使用 filePath 建立 Parser 類別的實例
using (Parser parser = new Parser(filePath))
{
    //將文字擷取到閱讀器中
    using (TextReader reader = parser.GetText())
    {
        //列印從文件中提取的文本
        //如果不支援文字擷取，則 reader 將為 null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## 步驟說明
1. 設定文件路徑：首先指定要從中提取文字的文件的路徑（`filePath`多變的）。
2. 建立解析器實例：實例化`Parser`類別透過透過`filePath`.
3. 提取文字：使用`GetText()`的方法`Parser`實例獲得一個`TextReader`包含從文件中提取的文字的物件。
4. 讀取提取的文字：利用`ReadToEnd()`的方法`TextReader`檢索從文件中提取的整個文字內容。
5. 處理不支援的格式：如果文件格式不支援文字擷取，則`reader`對象將是`null`，您可以相應地處理這種情況。

## 結論
在本教學中，我們介紹了使用 GroupDocs.Parser for .NET 從文件中擷取文字的初始步驟。該程式庫提供了廣泛的文檔解析功能，使開發人員能夠在其應用程式中有效地處理各種文件格式。

## 常見問題解答
### GroupDocs.Parser 是否與所有文件格式相容？
GroupDocs.Parser 支援多種格式，包括 PDF、Microsoft Office 文件（Word、Excel、PowerPoint）等。
### 我可以使用 GroupDocs.Parser 提取元資料和文字嗎？
是的，GroupDocs.Parser 允許從支援的文件格式中提取文字內容和元資料。
### 在哪裡可以找到有關 GroupDocs.Parser 的更多資源和支援？
參觀[GroupDocs.Parser 文檔](https://tutorials.groupdocs.com/parser/net/)取得詳細的 API 參考並探索[集團文檔論壇](https://forum.groupdocs.com/c/parser/17)以獲得社區支持。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以請求[臨時執照](https://purchase.groupdocs.com/temporary-license/)用於評估和測試目的。
### GroupDocs.Parser 是否有免費試用版？
是的，您可以下載一個[免費試用](https://releases.groupdocs.com/)GroupDocs.Parser 的版本。