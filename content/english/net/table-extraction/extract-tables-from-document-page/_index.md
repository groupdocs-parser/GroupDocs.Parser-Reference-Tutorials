---
title: Extract Tables from Document Page
linktitle: Extract Tables from Document Page
second_title: GroupDocs.Parser .NET API
description: Learn how to extract tables from documents programmatically using GroupDocs.Parser for .NET. This comprehensive tutorial provides step-by-step guidance.
weight: 11
url: /net/table-extraction/extract-tables-from-document-page/
type: docs
---
# Extract Tables from Document Page

## Introduction
In this tutorial, we will explore how to extract tables from a document page using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful library that allows developers to work with various document formats such as PDF, DOCX, XLSX, and more. By leveraging its features, we can efficiently extract structured data like tables from these documents, enabling us to manipulate and analyze the information programmatically.
## Prerequisites
Before getting started, ensure you have the following:
- Visual Studio installed on your machine.
- Basic understanding of C# and .NET development.
- GroupDocs.Parser for .NET library. You can download it from [here](https://releases.groupdocs.com/parser/net/).
- Access to a sample document (PDF, DOCX, etc.) containing tables for extraction.

## Import Namespaces
First, begin by importing the necessary namespaces in your C# project:
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
Instantiate the `Parser` class by providing the path to your sample document:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code continues here...
}
```
## Step 2: Check Document Table Extraction Support
Before proceeding, verify if the document supports table extraction:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Step 3: Define Table Layout
Define the layout of tables to be extracted from the document. Specify column widths and row heights as per your document's structure:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Column widths
    new double[] { 325, 340, 365, 395 });         // Row heights
```
## Step 4: Configure Table Extraction Options
Create options for table extraction using the specified layout:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Step 5: Retrieve Document Information
Fetch information about the document, including the number of pages:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Step 6: Iterate Over Document Pages
Iterate through each page of the document to extract tables:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extract tables from the current page
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Iterate over extracted tables
    foreach (PageTableArea table in tables)
    {
        // Iterate over rows of the table
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iterate over columns of the table
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Get the table cell
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Print the text of the table cell
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

## Conclusion
In this tutorial, we covered the process of extracting tables from document pages using GroupDocs.Parser for .NET. By following the provided steps, you can seamlessly integrate table extraction functionality into your .NET applications, enabling efficient handling and manipulation of structured data within documents.

## FAQ's
### Can GroupDocs.Parser extract tables from all types of documents?
GroupDocs.Parser supports various document formats like PDF, DOCX, XLSX, and more, enabling table extraction from compatible file types.
### Is GroupDocs.Parser for .NET suitable for large-scale document processing?
Yes, GroupDocs.Parser is designed to handle large documents efficiently, making it suitable for processing extensive datasets.
### Does GroupDocs.Parser preserve formatting during table extraction?
Yes, GroupDocs.Parser retains formatting details such as cell borders, text styles, and alignments during table extraction.
### Can I extract specific tables based on content criteria?
GroupDocs.Parser offers flexible options to target specific tables based on layout templates or content conditions for extraction.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser is compatible with both .NET Framework and .NET Core environments.
