---
title: 使用範本中的表格佈局
linktitle: 使用範本中的表格佈局
second_title: GroupDocs.Parser .NET API
description: 了解如何使用 GroupDocs.Parser for .NET 在範本中處理表格佈局。從文件中高效提取結構化資料。
weight: 14
url: /zh-hant/net/document-template-processing/working-with-table-layout-in-templates/
---
## 介紹
在本教學中，我們將探索如何使用 GroupDocs.Parser for .NET 在範本中處理表格版面配置。 GroupDocs.Parser 是一個功能強大的文件解析 API，可讓開發人員從各種文件格式（包括 PDF、Microsoft Office 等）中提取文字和元資料。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
- C# 和 .NET 開發的基礎知識。
- Visual Studio 安裝在您的電腦上。
- 安裝了適用於 .NET 的 GroupDocs.Parser。你可以下載它[這裡](https://releases.groupdocs.com/parser/net/).

## 導入命名空間
首先，確保將必要的命名空間匯入到您的專案中：
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 第 1 步：建立帶有佈局的表格模板
要在範本中使用表格佈局，您需要使用以下命令定義表格的結構`TemplateTableLayout`。此佈局指定列的寬度和行的高度。
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 30, 100, 320, 400, 480, 550 },   //列寬
    new double[] { 320, 345, 375 }                  //行高
);
//建立模板表
TemplateTable table = new TemplateTable(layout, "Details", null);
```
## 第 2 步：建立模板
現在，使用定義的表格建立一個範本。
```csharp
Template template = new Template(new TemplateItem[] { table });
```
## 步驟 3：使用範本解析文檔
接下來，實例化`Parser`類別並使用建立的模板解析文件。
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //透過模板解析文檔
    DocumentData data = parser.ParseByTemplate(template);
    //迭代提取的數據
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        //檢查欄位是否為表
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        //遍歷表行
        for (int row = 0; row < area.RowCount; row++)
        {
            //遍歷表列
            for (int column = 0; column < area.ColumnCount; column++)
            {
                //取得儲存格值
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                //列印儲存格值
                Console.Write(cellValue == null ? "" : cellValue.Text);
                //列印列之間的空間
                Console.Write("\t");
            }
            //每行後移動到下一行
            Console.WriteLine();
        }
    }
}
```

## 結論
在本教學中，我們學習如何利用 GroupDocs.Parser for .NET 來處理文件範本中的表格佈局。透過遵循概述的步驟，您可以有效地從文件中解析和提取結構化數據，從而促進應用程式中的各種數據處理任務。

## 常見問題解答
### 我可以使用 GroupDocs.Parser for .NET 解析 PDF 文件中的表格嗎？
是的，GroupDocs.Parser 支援從 PDF 文件以及其他流行格式解析表格。
### GroupDocs.Parser適合從文件中提取特定資料欄位嗎？
當然，GroupDocs.Parser 提供了基於預定義模板提取目標資料欄位的強大功能。
### 如何處理文件中的不同表格佈局？
GroupDocs.Parser 允許定義自訂範本以有效處理不同的表格佈局。
### GroupDocs.Parser是否支援處理大文件？
是的，GroupDocs.Parser 針對處理不同大小的文件進行了最佳化，確保了效能和可靠性。
### 我可以將 GroupDocs.Parser 與其他 .NET 程式庫整合嗎？
當然，GroupDocs.Parser 與其他 .NET 程式庫無縫集成，實現全面的文件處理工作流程。