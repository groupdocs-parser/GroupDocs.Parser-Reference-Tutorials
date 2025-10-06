---
title: 從文件中提取表格
linktitle: 從文件中提取表格
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 Groupdocs.Parser for .NET 從文件中提取表格。請繼續閱讀有關整合此功能的詳細指南。
weight: 10
url: /zh-hant/net/table-extraction/extract-tables-from-document/
type: docs
---
# 從文件中提取表格

## 介紹
Groupdocs.Parser for .NET 是一個綜合性庫，可促進文件解析，使您能夠從文件中提取有價值的信息，例如表格、文字、元資料等。在本教程中，我們特別關注使用 Groupdocs.Parser API 從文件中提取表。
## 先決條件
在我們開始之前，請確保您具備以下條件：
- Visual Studio 安裝在您的系統上。
- 已安裝 .NET Framework 或 .NET Core。
- C# 程式設計基礎知識。

## 導入命名空間
首先，您需要匯入必要的命名空間來存取 Groupdocs.Parser 類別和方法。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## 第 1 步：建立 Parser 類別的實例
初始化一個新的實例`Parser`類，透過提供範例文檔的路徑。
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    //你的程式碼放在這裡
}
```
## 第 2 步：檢查表提取支持
使用以下命令驗證文件是否支援表擷取`Features`的財產`Parser`班級。
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## 第 3 步：定義表格佈局
使用定義要提取的表的佈局`TemplateTableLayout`。根據文件的結構指定列寬和行高。
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## 步驟 4：設定表格擷取選項
創造`PageTableAreaOptions`使用定義的佈局來指定如何提取表格。
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 第 5 步：提取表
利用`GetTables`的方法`Parser`類別根據指定的選項從文件中提取表格。
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## 第 6 步：迭代和存取表數據
迭代提取的表及其各自的行和列以存取單元格資料。
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## 結論
在本教學中，我們介紹如何使用 Groupdocs.Parser for .NET 從文件中有效地提取表格。利用該庫的功能，您可以將表提取無縫整合到您的 .NET 應用程式中。

## 常見問題解答
### Groupdocs.Parser 可以處理不同的文件格式嗎？
是的，Groupdocs.Parser 支援多種文件格式，包括 DOCX、PDF、XLSX 等。
### Groupdocs.Parser for .NET 是否有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得 Groupdocs.Parser 相關查詢的支援？
您可以訪問[Groupdocs.Parser 論壇](https://forum.groupdocs.com/c/parser/17)尋求幫助。
### 在哪裡可以購買 Groupdocs.Parser 的許可證？
您可以從以下位置購買許可證[這裡](https://purchase.groupdocs.com/buy).
### 我如何獲得用於評估目的的臨時許可證？
您可以獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).