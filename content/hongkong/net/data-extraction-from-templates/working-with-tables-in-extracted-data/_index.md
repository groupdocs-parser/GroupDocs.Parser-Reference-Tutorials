---
title: 使用提取資料中的表
linktitle: 使用提取資料中的表
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 從文件中擷取表格資料。使用預定義模板有效解析結構化內容。
weight: 12
url: /zh-hant/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
type: docs
---
# 使用提取資料中的表

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Parser for .NET 從文件中的表格中擷取資料。 GroupDocs.Parser 是一款功能強大的工具，可讓開發人員從 PDF、DOCX、XLSX 等各種文件格式中解析和提取文字、元資料和結構化內容。具體來說，我們將重點放在使用預定義模板有效地提取表資料。
## 先決條件
在開始之前，請確保您已具備以下條件：
- Visual Studio 安裝在您的電腦上。
- 對 C# 和 .NET 架構有基本了解。
- GroupDocs.Parser 函式庫透過 NuGet 套件管理器安裝。

## 導入命名空間
首先匯入使用 GroupDocs.Parser 和相關功能所需的命名空間。
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 第 1 步：建立表格模板
要從表中提取數據，首先定義一個模板來表示要提取的表的結構。指定表格在文件中的位置和尺寸。
```csharp
//定義表參數（位置和大小）
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
//建立帶有參數的表模板
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## 第 2 步：定義模板
建立一個包含您定義的表格範本的範本。此範本將指導解析器在提取表格資料時要查找的內容。
```csharp
//使用表格建立模板
Template template = new Template(new TemplateItem[] { table });
```
## 第三步：解析文件並提取表數據
利用 GroupDocs.Parser 中的 Parser 類，使用您定義的範本來解析特定文件。
```csharp
//指定範例檔案的路徑
string filePath = "YourSampleFile.pdf";
//建立 Parser 類別的實例
using (Parser parser = new Parser(filePath))
{
    //透過模板解析文檔
    DocumentData data = parser.ParseByTemplate(template);
    //迭代所有提取的數據
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        //檢查提取的欄位是否為表
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        //迭代表行
        for (int row = 0; row < area.RowCount; row++)
        {
            //迭代表列
            for (int column = 0; column < area.ColumnCount; column++)
            {
                //取得儲存格值
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                //列印儲存格值（如果為空則列印空字串）
                Console.Write(cellValue == null ? "" : cellValue.Text);
                //列印列之間的製表符空格
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            //列印每一行後移至下一行
            Console.WriteLine();
        }
    }
}
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Parser for .NET 從文件中擷取表格資料。透過定義模板並利用解析方法，開發人員可以有效地從各種文件格式中提取結構化數據，例如表格。

## 常見問題解答
### GroupDocs.Parser 是否與所有文件格式相容？
是的，GroupDocs.Parser 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以從文件中的特定區域提取資料嗎？
當然，您可以定義針對文件中特定區域（例如表格）進行提取的範本。
### GroupDocs.Parser 適合大型文件嗎？
是的，GroupDocs.Parser 經過最佳化，可有效處理大型文檔，使開發人員能夠無縫提取資料。
### GroupDocs.Parser 是否支援文字擷取以及結構化資料？
是的，除了結構化資料提取（如表格）之外，GroupDocs.Parser 還可以從文件中提取純文字和元資料。
### 如何獲得有關 GroupDocs.Parser 整合的支援或協助？
如需支援和討論，請造訪 GroupDocs 社群論壇[這裡](https://forum.groupdocs.com/c/parser/17).