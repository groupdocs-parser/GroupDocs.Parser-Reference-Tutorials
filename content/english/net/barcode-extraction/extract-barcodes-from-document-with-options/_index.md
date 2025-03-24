---
title: Extract Barcodes from Document with Options
linktitle: Extract Barcodes from Document with Options
second_title: GroupDocs.Parser .NET API
description: Learn how to extract barcodes from documents using GroupDocs.Parser for .NET. Comprehensive tutorial with code examples and FAQs.
weight: 14
url: /net/barcode-extraction/extract-barcodes-from-document-with-options/
---

# Extract Barcodes from Document with Options

## Introduction
In this tutorial, we'll walk through the process of extracting barcodes from a document using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful library that allows you to extract text, metadata, and barcodes from various document formats such as PDF, Microsoft Word, Excel, and more.
## Prerequisites
Before you begin, make sure you have the following prerequisites in place:
1. Development Environment: Ensure you have Visual Studio installed on your machine.
2. GroupDocs.Parser Library: Download and install the GroupDocs.Parser for .NET library from [here](https://releases.groupdocs.com/parser/net/).
3. Sample Document: Prepare a sample document (e.g., PDF, DOCX) containing barcodes for extraction.

## Import Namespaces
First, you need to import the necessary namespaces into your C# project to utilize the GroupDocs.Parser functionalities.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Step 1: Create an Instance of Parser Class
To get started, create an instance of the `Parser` class by passing the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code to be added in the next steps
}
```
## Step 2: Check Barcode Extraction Support
Next, check if the document supports barcode extraction using the `Features` property of the `Parser` instance.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Step 3: Define Barcode Extraction Options
Now, specify the options for barcode extraction using `BarcodeOptions`. You can set parameters such as quality modes and barcode types.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Step 4: Extract Barcodes from the Document
Use the `GetBarcodes` method of the `Parser` class to extract barcodes based on the defined options.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Step 5: Iterate and Display Extracted Barcodes
Finally, iterate through the extracted barcodes and display their page index and values.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusion
In this tutorial, we've learned how to extract barcodes from a document using GroupDocs.Parser for .NET. This process involves creating a `Parser` instance, defining extraction options, and iterating through the extracted barcodes. GroupDocs.Parser simplifies the task of barcode extraction from various document formats, enabling efficient document processing within your .NET applications.

## FAQ's
### Can GroupDocs.Parser extract barcodes from PDF documents?
Yes, GroupDocs.Parser supports barcode extraction from PDF documents along with other formats like DOCX, XLSX, etc.
### What barcode types does GroupDocs.Parser support?
GroupDocs.Parser supports various barcode types including QR codes, Code 39, Code 128, and more.
### Does GroupDocs.Parser require a license for commercial use?
Yes, a valid license is required for commercial use. You can obtain a license from [here](https://purchase.groupdocs.com/buy).
### Is GroupDocs.Parser suitable for batch processing of documents?
Yes, GroupDocs.Parser can efficiently handle batch processing of documents for text extraction, metadata retrieval, and barcode extraction.
### Where can I find technical support for GroupDocs.Parser?
You can get technical support or ask questions on the [GroupDocs forum](https://forum.groupdocs.com/c/parser/17).
