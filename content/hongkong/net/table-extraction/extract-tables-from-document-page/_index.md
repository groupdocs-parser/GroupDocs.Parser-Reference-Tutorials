---
title: 從文件頁面中提取表格
linktitle: 從文件頁面中提取表格
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 以程式設計方式從文件中擷取表格。這個綜合教程提供了逐步指導。
weight: 11
url: /zh-hant/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# 從文件頁面中提取表格

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從文件頁面中擷取表格。 GroupDocs.Parser 是一個功能強大的程式庫，可讓開發人員處理各種文件格式，例如 PDF、DOCX、XLSX 等。透過利用其功能，我們可以有效地從這些文件中提取結構化資料（例如表格），從而使我們能夠以程式設計方式操作和分析資訊。
## 先決條件
在開始之前，請確保您具備以下條件：
- Visual Studio 安裝在您的電腦上。
- 對 C# 和 .NET 開發有基本了解。
- 用於 .NET 函式庫的 GroupDocs.Parser。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/parser/net/).
- 存取包含要擷取的表格的範例文件（PDF、DOCX 等）。

## 導入命名空間
首先，首先在 C# 專案中導入必要的命名空間：
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
實例化`Parser`類別透過提供範例文件的路徑：
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //您的程式碼在這裡繼續...
}
```
## 步驟 2：檢查文件表擷取支持
在繼續之前，請先驗證文件是否支援表提取：
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## 第 3 步：定義表格佈局
定義要從文件中提取的表格的佈局。根據文件的結構指定列寬和行高：
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  //列寬
    new double[] { 325, 340, 365, 395 });         //行高
```
## 步驟 4：設定表提取選項
使用指定佈局建立表格擷取選項：
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## 第5步：檢索文件資訊
取得有關文件的信息，包括頁數：
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 第 6 步：迭代文件頁面
迭代文件的每一頁以提取表格：
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    //從目前頁面提取表格
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    //迭代提取的表
    foreach (PageTableArea table in tables)
    {
        //迭代表的行
        for (int row = 0; row < table.RowCount; row++)
        {
            //迭代表的列
            for (int column = 0; column < table.ColumnCount; column++)
            {
                //取得表格單元格
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    //列印表格單元格的文字
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## 結論
在本教學中，我們介紹了使用 GroupDocs.Parser for .NET 從文件頁面中提取表格的過程。透過遵循提供的步驟，您可以將表提取功能無縫整合到 .NET 應用程式中，從而實現文件中結構化資料的高效處理和操作。

## 常見問題解答
### GroupDocs.Parser 可以從所有類型的文件中提取表格嗎？
GroupDocs.Parser 支援各種文件格式，例如 PDF、DOCX、XLSX 等，因此能夠從相容的文件類型中提取表格。
### GroupDocs.Parser for .NET 適合大規模文件處理嗎？
是的，GroupDocs.Parser 旨在高效處理大型文檔，使其適合處理大量資料集。
### GroupDocs.Parser 在表格擷取期間是否保留格式？
是的，GroupDocs.Parser 會在表格提取期間保留格式詳細信息，例如單元格邊框、文字樣式和對齊方式。
### 我可以根據內容標準提取特定表格嗎？
GroupDocs.Parser 提供了靈活的選項，可根據佈局範本或擷取的內容條件來定位特定的表格。
### GroupDocs.Parser 與 .NET Core 相容嗎？
是的，GroupDocs.Parser 與 .NET Framework 和 .NET Core 環境相容。