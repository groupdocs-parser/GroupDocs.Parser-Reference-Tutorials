---
title: Extract Text from PDF
linktitle: Extract Text from PDF
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from PDF documents using GroupDocs.Parser for .NET. Step-by-step tutorial for developers.
weight: 14
url: /net/pdf-processing/extract-text-from-pdf/
---
## Introduction
In this tutorial, we'll explore how to extract text from PDF documents using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful API that allows developers to extract text, metadata, and structured data from various document formats including PDF, Microsoft Office, and more.
## Prerequisites
Before you begin, make sure you have the following:
- Visual Studio installed on your machine.
- GroupDocs.Parser for .NET installed. You can download it [here](https://releases.groupdocs.com/parser/net/).
- Basic knowledge of C# programming.

## Import Namespaces
First, start by importing the necessary namespaces in your C# code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of Parser Class
Instantiate the `Parser` class by providing the path to your sample PDF file:
```csharp
// Create an instance of Parser class
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code goes here
}
```
## Step 2: Extract Text from PDF
Within the `Parser` instance, use the `GetText()` method to extract text from the PDF:
```csharp
// Extract a text into the reader
using (TextReader reader = parser.GetText())
{
    // Your code goes here
}
```
## Step 3: Read and Print Extracted Text
Now, read the extracted text from the `TextReader` and print it:
```csharp
// Print the extracted text
Console.WriteLine(reader.ReadToEnd());
```

## Conclusion
In this tutorial, we covered the basics of extracting text from PDF documents using GroupDocs.Parser for .NET. You learned how to initialize the `Parser` class, extract text, and print the extracted content. This API provides a straightforward way to handle PDF and other document formats programmatically.

## FAQ's
### Is GroupDocs.Parser compatible with other document formats besides PDF?
Yes, GroupDocs.Parser supports a wide range of formats including DOCX, XLSX, PPTX, and more.
### Can I try GroupDocs.Parser before purchasing a license?
Yes, you can get a free trial version [here](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Parser?
Detailed documentation is available [here](https://tutorials.groupdocs.com/parser/net/).
### How can I get technical support for GroupDocs.Parser?
You can seek help on the support forum [here](https://forum.groupdocs.com/c/parser/17).
### How do I obtain a temporary license for GroupDocs.Parser?
Temporary licenses can be acquired [here](https://purchase.groupdocs.com/temporary-license/).
