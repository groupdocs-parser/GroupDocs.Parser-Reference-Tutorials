---
title: 使用模板中固定位置的字段
linktitle: 使用模板中固定位置的字段
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中擷取資料。帶有程式碼範例的綜合教程。
weight: 11
url: /zh-hant/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
type: docs
---
# 使用模板中固定位置的字段

## 介紹
在本教學中，我們將探索如何使用 GroupDocs.Parser for .NET 處理範本內固定位置的欄位。 GroupDocs.Parser 是一個功能強大的文件解析庫，使開發人員能夠從 PDF、Word、Excel 等各種文件格式中提取資料。具體來說，我們將重點放在定義和利用模板欄位來根據其固定位置提取目標資訊。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- 對 C# 和 .NET 開發有基本了解。
- Visual Studio 安裝在您的系統上。
- 安裝了 .NET 函式庫的 GroupDocs.Parser。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
- 用於測試的範例文件文件。

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
首先，在模板中定義一個具有固定位置的欄位。此欄位表示將從中提取資料的區域。
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
這裡：
- `Rectangle`指定欄位的位置和大小。
- `Point(35, 135)`代表左上角座標。
- `Size(100, 10)`定義欄位的寬度和高度。
- `"FromCompany"`是分配給該欄位的名稱。
## 第 2 步：建立模板
使用定義的欄位建立模板。
```csharp
Template template = new Template(new TemplateItem[] { field });
```
這`Template`物件保存定義的欄位。
## 步驟 3：使用範本解析文檔
實例化`Parser`類別與目標文件路徑，然後使用建立的範本解析文件。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的數據
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
這裡：
- `Parser`使用範例文檔文件路徑進行初始化。
- `ParseByTemplate`方法用於根據提供的模板提取資料。
- 使用以下方式存取提取的數據`DocumentData`，其中每個項目對應一個定義的欄位。

## 結論
在本教學中，我們介紹了使用 GroupDocs.Parser for .NET 處理範本中固定位置的欄位的過程。透過定義具有特定欄位位置的模板，開發人員可以從各種文件格式中準確提取目標資料。

## 常見問題解答
### GroupDocs.Parser 是否與所有文件格式相容？
 GroupDocs.Parser 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。請參閱[文件](https://tutorials.groupdocs.com/parser/net/)取得詳細清單。
### 如何獲得 GroupDocs.Parser 的臨時許可證？
您可以從以下位置取得用於測試目的的臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到對 GroupDocs.Parser 的支援？
如需技術協助和討論，請訪問[GroupDocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17).
### 我可以在購買前試用 GroupDocs.Parser 嗎？
是的，您可以透過免費試用來探索該庫[這裡](https://releases.groupdocs.com/).
### 如何購買 GroupDocs.Parser 的許可證？
要購買許可證，請訪問[購買頁面](https://purchase.groupdocs.com/buy).