---
title: Extract Formatted Text from Document Page
linktitle: Extract Formatted Text from Document Page
second_title: GroupDocs.Parser .NET API
description: Extract formatted text from document pages using GroupDocs.Parser for .NET. Efficient and reliable text extraction solution.
weight: 11
url: /net/formatted-text-extraction/extract-formatted-text-from-document-page/
---

# Extract Formatted Text from Document Page

## Introduction
In this tutorial, we will guide you through the process of extracting formatted text from document pages using GroupDocs.Parser for .NET. This library allows you to efficiently parse and extract text from various document formats like PDF, Word, Excel, and more.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio installed on your system.
- Basic knowledge of C# programming.
- GroupDocs.Parser for .NET library. You can download it [here](https://releases.groupdocs.com/parser/net/).

## Import Namespaces
First, start by importing the necessary namespaces into your C# project.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Begin by creating an instance of the `Parser` class by providing the path to your sample file.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code will go here
}
```
## Step 2: Check if Formatted Text Extraction is Supported
Before proceeding with text extraction, verify if the document supports formatted text extraction.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Step 3: Get Document Information
Retrieve information about the document, such as the number of pages.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Step 4: Iterate Over Document Pages and Extract Formatted Text
Iterate through each page of the document and extract formatted text using specified options (e.g., Markdown format).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusion
Now you know how to extract formatted text from document pages using GroupDocs.Parser for .NET. This library provides a powerful and easy-to-use solution for text extraction from various file formats.

## FAQ's
### Can GroupDocs.Parser handle different file formats?
Yes, GroupDocs.Parser supports a wide range of document formats, including PDF, DOCX, XLSX, PPTX, and more.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser supports .NET Core and .NET Framework.
### Does GroupDocs.Parser preserve text formatting during extraction?
Yes, GroupDocs.Parser can retain formatting such as styles and fonts when extracting text.
### Can I extract images and metadata using GroupDocs.Parser?
Yes, GroupDocs.Parser allows extraction of images, metadata, and text from documents.
### How can I get support for GroupDocs.Parser?
You can get support from the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17).
