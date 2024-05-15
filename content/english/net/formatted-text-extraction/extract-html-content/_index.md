---
title: Extract HTML Content
linktitle: Extract HTML Content
second_title: GroupDocs.Parser .NET API
description: Learn how to extract HTML content from documents using GroupDocs.Parser for .NET. Easy-to-follow tutorial with code examples and step-by-step guidance.
type: docs
weight: 12
url: /net/formatted-text-extraction/extract-html-content/
---
## Introduction
In this tutorial, we'll explore how to use the GroupDocs.Parser for .NET to extract HTML content from various document formats. GroupDocs.Parser is a powerful library that allows developers to parse and extract text from documents seamlessly. Whether you're working with Word documents, PDFs, or other formats, GroupDocs.Parser simplifies the process of extracting structured content.
## Prerequisites
Before diving into the code examples, ensure you have the following prerequisites:
- Visual Studio: Make sure you have Visual Studio installed on your system.
- GroupDocs.Parser for .NET: Download and install the GroupDocs.Parser library from [here](https://releases.groupdocs.com/parser/net/).
- Sample Document: Prepare a sample document (e.g., a Word document or PDF) that you'll use for extracting HTML content.

## Import Namespaces
First, import the necessary namespaces to access the GroupDocs.Parser functionality in your .NET project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Initialize a `Parser` object by providing the path to your sample document:
```csharp
// Create an instance of Parser class
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code to extract content will go here
}
```
## Step 2: Extract HTML Content
Now, within the `using` block, utilize the `GetFormattedText` method to extract formatted text as HTML:
```csharp
// Extract a formatted text into the reader
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
{
    // Print a formatted text from the document
    // If formatted text extraction isn't supported, a reader is null
    Console.WriteLine(reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd());
}
```

## Conclusion
By following these steps, you can effectively use GroupDocs.Parser for .NET to extract HTML content from various document formats, empowering your applications with advanced text extraction capabilities.

## FAQ's
### Can GroupDocs.Parser extract HTML from scanned documents?
GroupDocs.Parser is primarily designed for extracting text from digital documents. For scanned documents, consider using OCR (Optical Character Recognition) solutions.
### Does GroupDocs.Parser support extracting tables and images?
Yes, GroupDocs.Parser can extract tables, images, and other structured content from supported document formats.
### How can I handle exceptions during document parsing?
You can implement error handling around the parsing code using standard try-catch blocks to manage exceptions gracefully.
### Is GroupDocs.Parser compatible with .NET Core applications?
Yes, GroupDocs.Parser supports .NET Core, allowing you to integrate text extraction capabilities into modern cross-platform applications.
### Can I customize the text extraction options?
Yes, GroupDocs.Parser provides various options for customizing text extraction, including formatting modes and specific content extraction settings.
