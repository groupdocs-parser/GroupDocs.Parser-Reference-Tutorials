---
title: Extract Tables from Document
linktitle: Extract Tables from Document
second_title: GroupDocs.Parser .NET API
description: Learn how to extract tables from documents using Groupdocs.Parser for .NET. Follow along for a detailed guide on integrating this functionality.
weight: 10
url: /net/table-extraction/extract-tables-from-document/
---
## Introduction
Groupdocs.Parser for .NET is a comprehensive library that facilitates document parsing, allowing you to extract valuable information such as tables, text, metadata, and more from documents. In this tutorial, we focus specifically on extracting tables from documents using the Groupdocs.Parser API.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio installed on your system.
- .NET Framework or .NET Core installed.
- Basic knowledge of C# programming.

## Import Namespaces
First, you need to import the necessary namespaces to access the Groupdocs.Parser classes and methods.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Step 1: Create an Instance of Parser Class
Initialize a new instance of the `Parser` class by providing the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Your code goes here
}
```
## Step 2: Check Table Extraction Support
Verify if the document supports table extraction using the `Features` property of the `Parser` class.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Step 3: Define Table Layout
Define the layout of the tables you want to extract using `TemplateTableLayout`. Specify column widths and row heights based on your document's structure.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Step 4: Set Table Extraction Options
Create `PageTableAreaOptions` with the defined layout to specify how tables should be extracted.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Step 5: Extract Tables
Utilize the `GetTables` method of the `Parser` class to extract tables from the document based on the specified options.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Step 6: Iterate and Access Table Data
Iterate through the extracted tables and their respective rows and columns to access cell data.
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
## Conclusion
In this tutorial, we've covered how to use Groupdocs.Parser for .NET to extract tables from documents efficiently. Leveraging the capabilities of this library, you can integrate table extraction into your .NET applications seamlessly.

## FAQ's
### Can Groupdocs.Parser handle different document formats?
Yes, Groupdocs.Parser supports a wide range of document formats including DOCX, PDF, XLSX, and more.
### Is there a trial version available for Groupdocs.Parser for .NET?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/).
### How can I get support for Groupdocs.Parser related queries?
You can visit the [Groupdocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for assistance.
### Where can I purchase a license for Groupdocs.Parser?
You can buy a license from [here](https://purchase.groupdocs.com/buy).
### How can I obtain a temporary license for evaluation purposes?
You can obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
