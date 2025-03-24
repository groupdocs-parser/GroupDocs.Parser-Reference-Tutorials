---
title: 使用模板中連結位置處的字段
linktitle: 使用模板中連結位置處的字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中有效擷取資料。帶有程式碼範例的分步教程。
weight: 12
url: /zh-hant/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---

# 使用模板中連結位置處的字段

## 介紹
GroupDocs.Parser for .NET 是一個強大的程式庫，旨在促進文件解析和資料擷取任務。它支援多種文件格式，包括 PDF、DOCX、XLSX 等。其主要功能之一是基於模板的資料提取，它允許您定義文件中的欄位並根據這些預先定義的模板提取特定資料。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- 對 C# 程式設計有基本了解
- 您的系統上安裝了 Visual Studio
-  GroupDocs.Parser for .NET 函式庫（從下載[這裡](https://releases.groupdocs.com/parser/net/）)
- 要使用的範例文件文件

## 導入命名空間
首先在您的 C# 專案中包含必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 第 1 步：定義模板字段
首先，使用正規表示式和連結位置定義範本欄位：
```csharp
//使用正規表示式定義字段
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
//定義具有特定位置設定的連結字段
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## 第 2 步：建立模板
接下來，建立一個包含已定義欄位的範本：
```csharp
//使用定義的欄位建立模板
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## 第三步：用模板解析文檔
現在，初始化`Parser`使用模板類別並解析文件：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //透過模板解析文檔
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的數據並列印結果
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## 結論
GroupDocs.Parser for .NET 簡化了使用範本從文件中提取結構化資料的過程。透過定義欄位和應用模板，您可以有效地提取相關信息，從而提高文件處理任務的自動化程度和生產力。

## 常見問題解答
### GroupDocs.Parser 可以從加密的 PDF 檔案中提取資料嗎？
是的，GroupDocs.Parser 支援透過在解析過程中提供密碼來解析加密的 PDF 檔案。
### 基於範本的提取支援哪些文件格式？
GroupDocs.Parser 支援多種檔案格式，包括 PDF、DOCX、XLSX、PPTX、TXT 等。
### GroupDocs.Parser 是否有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 我可以使用 GroupDocs.Parser 來批次處理文件嗎？
是的，GroupDocs.Parser 允許批次同時解析多個文件。
### 在哪裡可以獲得 GroupDocs.Parser 的技術支援？
您可以尋求技術支援並與社區互動：[集團文檔論壇](https://forum.groupdocs.com/c/parser/17).