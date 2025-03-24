---
title: 按名稱取得字段
linktitle: 按名稱取得字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中提取特定資料欄位。帶有程式碼範例的分步指南。
weight: 10
url: /zh-hant/net/data-extraction-from-templates/get-field-by-name/
---

# 按名稱取得字段

## 介紹
在本教學中，我們將探討如何利用 GroupDocs.Parser for .NET 從文件中提取特定的資料字段，例如價格和電子郵件。這個強大的程式庫簡化了文件解析任務，使其成為各種資料擷取需求的理想選擇。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
- Visual Studio 安裝在您的系統上。
- C# 程式設計基礎知識。
- 下載並安裝 GroupDocs.Parser for .NET 從[這個連結](https://releases.groupdocs.com/parser/net/).

## 導入命名空間
首先將必要的命名空間匯入到您的 C# 專案中：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 第 1 步：定義模板字段
首先，我們將定義用於提取資料的模板欄位。在此範例中，我們將建立欄位來捕獲價格和電子郵件。
```csharp
//定義“價格”字段
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
//定義“電子郵件”字段
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
//建立模板
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
## 步驟2：使用模板解析文檔
接下來，我們將使用定義的範本解析文件。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //透過模板解析文檔
    DocumentData data = parser.ParseByTemplate(template);
    //列印價格
    Console.WriteLine("Prices:");
    foreach (FieldData field in data.GetFieldsByName("Price"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
    //列印電子郵件
    Console.WriteLine("Emails:");
    foreach (FieldData field in data.GetFieldsByName("Email"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Parser for .NET 從文件中擷取特定資料欄位。透過定義範本並利用庫的解析功能，開發人員可以有效地從各種文件格式中檢索結構化數據，例如價格和電子郵件。

## 常見問題解答
### 我可以使用 GroupDocs.Parser for .NET 解析不同類型的文件嗎？
是的，GroupDocs.Parser 支援解析各種文件格式，例如 PDF、DOCX、PPTX 等。
### GroupDocs.Parser適合大規模文件處理嗎？
當然，GroupDocs.Parser 針對效能進行了最佳化，可以有效地處理大量文件。
### 如何將 GroupDocs.Parser 整合到我的 .NET 應用程式中？
您可以透過引用 Visual Studio 專案中的庫並匯入所需的命名空間來輕鬆整合 GroupDocs.Parser。
### GroupDocs.Parser 是否提供提取映像或元資料的支援？
是的，GroupDocs.Parser 提供了從文件中提取圖像、文字和元資料的 API。
### 是否有針對 GroupDocs.Parser 使用者的社群論壇？
是的，您可以在 GroupDocs.Parser 論壇上尋求協助並與其他使用者互動[這裡](https://forum.groupdocs.com/c/parser/17).