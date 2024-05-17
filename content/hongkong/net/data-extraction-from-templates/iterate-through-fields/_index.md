---
title: 遍歷字段
linktitle: 遍歷字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中擷取結構化資料。透過文件資料擷取功能增強您的 .NET 應用程式。
type: docs
weight: 11
url: /zh-hant/net/data-extraction-from-templates/iterate-through-fields/
---
## 介紹
GroupDocs.Parser for .NET 是一個功能強大的程式庫，可讓開發人員從各種文件格式（如 PDF、Microsoft Word、Excel 和 PowerPoint）中提取資料。本教學將指導您完成使用 GroupDocs.Parser 迭代文件欄位並使用範本提取特定資料的過程。學完本教學後，您將能夠從 .NET 應用程式中的文件中有效地提取結構化資料。
## 先決條件
在我們開始之前，請確保您已設定以下先決條件：
- C# 程式設計基礎知識。
- Visual Studio 安裝在您的電腦上。
- GroupDocs.Parser for .NET 程式庫在您的專案中安裝並參考。

## 導入命名空間
首先，將必要的命名空間新增到您的 C# 檔案中：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
讓我們將該過程分解為逐步說明。
## 第 1 步：定義模板字段
首先，使用正規表示式定義要從文件中提取的欄位。
```csharp
//定義“價格”字段
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
//定義“電子郵件”字段
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
//建立具有定義欄位的模板
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
在此步驟中，我們定義了兩個欄位：一個用於提取價格（由美元符號和數字標識），另一個用於提取電子郵件地址。
## 第 2 步：解析文檔
接下來，使用`Parser`類別使用定義的範本解析文件。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //透過模板解析文檔
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的數據
    for (int i = 0; i < data.Count; i++)
    {
        //列印欄位名稱
        Console.Write(data[i].Name + ": ");
        //檢查提取的區域是否為文字
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
在這裡，我們初始化`Parser`包含範例文件的路徑，然後使用定義的範本解析文件。然後，我們迭代提取的資料並列印欄位名稱以及提取的文字。
## 結論
在本教學中，我們探討如何使用 GroupDocs.Parser for .NET 使用範本從文件中擷取特定資料。透過利用正規表示式和模板，您可以有效地從各種文件格式中提取結構化資訊。嘗試不同的範本和文件類型，以滿足您的特定提取需求。

## 常見問題解答
### GroupDocs.Parser 可以從掃描文件中提取資料嗎？
是的，GroupDocs.Parser 可以從掃描和可搜尋的 PDF 文件中提取文字和元資料。
### GroupDocs.Parser 與 .NET Core 應用程式相容嗎？
是的，GroupDocs.Parser 支援 .NET Core 和 .NET Framework。
### GroupDocs.Parser 支援哪些文件格式？
GroupDocs.Parser 支援多種格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 如何使用 GroupDocs.Parser 處理大型文件？
GroupDocs.Parser 提供從大型文件的特定頁面或部分提取資料的選項，確保高效處理。
### 我可以僅使用 GroupDocs.Parser 進行文字擷取嗎？
是的，您可以使用 GroupDocs.Parser 從文件中提取純文字內容，而無需複雜的格式設定。