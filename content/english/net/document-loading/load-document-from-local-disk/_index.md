---
title: Load Document from Local Disk
linktitle: Load Document from Local Disk
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from various document formats using GroupDocs.Parser for .NET. Easy and efficient text extraction with C#.
weight: 11
url: /net/document-loading/load-document-from-local-disk/
---

# Load Document from Local Disk

## Introduction
In this tutorial, we will explore how to use GroupDocs.Parser for .NET to extract text from documents. GroupDocs.Parser is a powerful library that allows developers to parse various document formats and extract text content programmatically. We'll cover the necessary steps to get started with text extraction using this library.
## Prerequisites
Before we begin, ensure you have the following prerequisites installed:
- Visual Studio installed on your system.
- Basic knowledge of C# programming language.
- GroupDocs.Parser for .NET library installed (download [here](https://releases.groupdocs.com/parser/net/)).

## Import Namespaces
First, you need to import the necessary namespaces to your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Step 1: Load Document from Local Disk
Begin by loading a document from your local disk. Replace `"Your Sample File"` with the path to your target document.
```csharp
// Set the filePath
string filePath = "Your Sample File";
// Create an instance of Parser class with the filePath
using (Parser parser = new Parser(filePath))
{
    // Extract text into the reader
    using (TextReader reader = parser.GetText())
    {
        // Print the extracted text from the document
        // If text extraction isn't supported, the reader will be null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Explanation of Steps
1. Setting File Path: Begin by specifying the path to the document you want to extract text from (`filePath` variable).
2. Creating Parser Instance: Instantiate the `Parser` class by passing the `filePath`.
3. Extracting Text: Use the `GetText()` method of the `Parser` instance to obtain a `TextReader` object containing the extracted text from the document.
4. Reading Extracted Text: Utilize the `ReadToEnd()` method of the `TextReader` to retrieve the entire text content extracted from the document.
5. Handling Unsupported Formats: If the document format does not support text extraction, the `reader` object will be `null`, and you can handle this scenario accordingly.

## Conclusion
In this tutorial, we've covered the initial steps to extract text from a document using GroupDocs.Parser for .NET. This library offers extensive features for document parsing, enabling developers to efficiently work with various file formats within their applications.

## FAQ's
### Is GroupDocs.Parser compatible with all document formats?
GroupDocs.Parser supports a wide range of formats including PDF, Microsoft Office documents (Word, Excel, PowerPoint), and more.
### Can I extract metadata along with text using GroupDocs.Parser?
Yes, GroupDocs.Parser allows extraction of both text content and metadata from supported document formats.
### Where can I find more resources and support for GroupDocs.Parser?
Visit the [GroupDocs.Parser Documentation](https://tutorials.groupdocs.com/parser/net/) for detailed API tutorials and explore the [GroupDocs Forum](https://forum.groupdocs.com/c/parser/17) for community support.
### How can I obtain a temporary license for GroupDocs.Parser?
You can request a [temporary license](https://purchase.groupdocs.com/temporary-license/) for evaluation and testing purposes.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can download a [free trial](https://releases.groupdocs.com/) version of GroupDocs.Parser.
