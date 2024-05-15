---
title: Extract Text from Page in PDF in Raw Mode
linktitle: Extract Text from Page in PDF in Raw Mode
second_title: GroupDocs.Parser .NET API
description: Extract text from PDFs using GroupDocs.Parser in C#. Learn efficient PDF text extraction with this powerful .NET library.
type: docs
weight: 16
url: /net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to extract text from pages in PDF documents using raw mode. GroupDocs.Parser is a powerful tool that enables developers to work with various document formats programmatically.
## Prerequisites
Before starting this tutorial, ensure you have the following:
- Visual Studio installed on your machine.
- Basic knowledge of C# programming.
- GroupDocs.Parser for .NET library, which you can [download here](https://releases.groupdocs.com/parser/net/).
- A sample PDF file for testing purposes.

## Import Namespaces
First, make sure to import the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
To begin, instantiate the `Parser` class by providing the path to your sample PDF file.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code goes here
}
```
## Step 2: Get Document Info and Iterate Over Pages
Next, retrieve the document information and iterate over each page to extract text.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Your code for text extraction goes here
}
```
## Step 3: Extract Text from Each Page
Within the loop, use the `GetText` method to extract text from each page and print it.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusion
In this tutorial, we've learned how to extract text from PDF pages in raw mode using GroupDocs.Parser for .NET. This process involves creating a `Parser` instance, obtaining document information, iterating over each page, and extracting text using the `GetText` method.

## FAQ's
### What is GroupDocs.Parser for .NET?
GroupDocs.Parser for .NET is a document parsing API that allows developers to extract text, metadata, and other information from various file formats programmatically.
### How do I download GroupDocs.Parser for .NET?
You can download the library from the [GroupDocs website](https://releases.groupdocs.com/parser/net/).
### Is there a free trial available?
Yes, you can access a free trial of GroupDocs.Parser for .NET from [here](https://releases.groupdocs.com/).
### Where can I find support for GroupDocs.Parser for .NET?
For technical assistance and community support, visit the [GroupDocs forum](https://forum.groupdocs.com/c/parser/17).
### How can I purchase a license for GroupDocs.Parser for .NET?
You can purchase a license from the [purchase page](https://purchase.groupdocs.com/buy) or acquire a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
