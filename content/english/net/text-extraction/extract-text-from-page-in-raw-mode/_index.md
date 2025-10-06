---
title: Extract Text from Page in Raw Mode
linktitle: Extract Text from Page in Raw Mode
second_title: GroupDocs.Parser .NET API
description: Learn efficient text extraction from document pages using Groupdocs.Parser for .NET in this comprehensive tutorial.
weight: 17
url: /net/text-extraction/extract-text-from-page-in-raw-mode/
type: docs
---
# Extract Text from Page in Raw Mode

## Introduction
In this tutorial, you will learn how to use Groupdocs.Parser for .NET to extract text from document pages in raw mode. This library provides efficient tools to parse and extract content from various file formats, enabling developers to incorporate document text extraction into their .NET applications.
## Prerequisites
Before you begin, ensure you have the following prerequisites:
- Basic knowledge of C# and .NET programming
- Visual Studio installed on your machine
- Access to Groupdocs.Parser for .NET library
- Sample document file for testing

## Import Namespaces
Start by including the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Initialize Parser
First, create an instance of the `Parser` class by providing the path to your sample document file.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code here
}
```
## Step 2: Retrieve Document Info
Retrieve information about the document using `GetDocumentInfo()` method.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Step 3: Iterate Over Pages and Extract Text
Iterate through each page of the document and extract text content.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Extract text from the page
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusion
You've now learned how to use Groupdocs.Parser for .NET to extract text from document pages in raw mode. This can be a powerful feature for applications that need to analyze or process text content from various file formats.

## FAQ's
### Is Groupdocs.Parser for .NET compatible with all file formats?
Groupdocs.Parser supports a wide range of file formats including PDF, DOCX, XLSX, PPTX, EPUB, and more.
### Can I extract metadata along with text using this library?
Yes, Groupdocs.Parser allows you to extract both text and metadata from documents.
### Is there a trial version available for testing?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get technical support for Groupdocs.Parser?
For technical assistance, visit the [Groupdocs.Parser forum](https://forum.groupdocs.com/c/parser/17).
### Where can I purchase a license for Groupdocs.Parser for .NET?
You can purchase a license [here](https://purchase.groupdocs.com/buy).
