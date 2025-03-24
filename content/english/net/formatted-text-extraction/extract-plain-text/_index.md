---
title: Extract Plain Text
linktitle: Extract Plain Text
second_title: GroupDocs.Parser .NET API
description: Learn how to extract plain text from documents using GroupDocs.Parser for .NET. Easy steps for integrating text extraction in your applications.
weight: 14
url: /net/formatted-text-extraction/extract-plain-text/
---

# Extract Plain Text

## Introduction
In this tutorial, we will explore how to extract plain text from various document formats using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful library that allows developers to work with documents seamlessly, extracting text and metadata efficiently. This guide will walk you through the necessary steps to integrate and utilize this library within your .NET applications.
## Prerequisites
Before we begin, ensure you have the following prerequisites in place:
1. Visual Studio: Install Visual Studio on your development machine.
2. GroupDocs.Parser Library: Download and install GroupDocs.Parser for .NET from the [download page](https://releases.groupdocs.com/parser/net/).
3. Sample Documents: Prepare sample documents (e.g., DOCX, PDF, TXT) for text extraction.

## Import Namespaces
First, include the necessary namespaces in your C# project to access the functionalities of GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Initialize Parser
Create an instance of the `Parser` class by specifying the path to your sample document.
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // Code for text extraction goes here
}
```
## Step 2: Extract Formatted Text
Within the `using` block of the `Parser`, extract the formatted text using the `GetFormattedText` method with `PlainText` mode.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // Code to read and process the extracted text
}
```
## Step 3: Read Extracted Text
Use the `TextReader` instance to read and output the extracted plain text.
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## Conclusion
In this tutorial, we've covered the basics of extracting plain text from documents using GroupDocs.Parser for .NET. By following these steps, you can seamlessly integrate text extraction capabilities into your .NET applications.

## FAQ's
### Is GroupDocs.Parser compatible with multiple document formats?
Yes, GroupDocs.Parser supports a wide range of document formats including DOCX, PDF, TXT, and more.
### Can I extract metadata along with text using GroupDocs.Parser?
Absolutely, GroupDocs.Parser allows extraction of both text content and metadata like author, creation date, etc.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can access the free trial of GroupDocs.Parser [here](https://releases.groupdocs.com/).
### Where can I find technical support for GroupDocs.Parser?
For technical assistance, visit the GroupDocs.Parser [forum](https://forum.groupdocs.com/c/parser/17).
### How can I obtain a temporary license for GroupDocs.Parser?
To acquire a temporary license, visit the GroupDocs.Parser [temporary license page](https://purchase.groupdocs.com/temporary-license/).
