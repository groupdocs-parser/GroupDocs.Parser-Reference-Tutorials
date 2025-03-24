---
title: Load Document from URL
linktitle: Load Document from URL
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from documents using GroupDocs.Parser for .NET. This tutorial covers loading a document from a URL and extracting text step by step.
weight: 13
url: /net/document-loading/load-document-from-url/
---

# Load Document from URL

## Introduction
In this tutorial, we'll explore how to utilize GroupDocs.Parser for .NET to extract text from documents. GroupDocs.Parser is a powerful tool for extracting text, metadata, and other information from various document formats, such as PDF, Word, Excel, and more. We'll cover the process of loading a document from a URL and extracting its text content step by step.
## Prerequisites
Before we begin, ensure you have the following prerequisites set up:
1. Visual Studio: Install Visual Studio on your system.
2. GroupDocs.Parser for .NET: Download and install GroupDocs.Parser for .NET from the [download page](https://releases.groupdocs.com/parser/net/).
3. Basic Understanding of C#: Familiarity with C# programming language.

## Import Namespaces
Start by including the necessary namespaces in your C# code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

First, we'll demonstrate how to load a document from a URL and extract its text content.
## Step 1: Specify the Document URL
Specify the URL of the document you want to extract text from:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Step 2: Create a Parser Instance
Instantiate the `Parser` class with the document URL:
```csharp
using (Parser parser = new Parser(uri))
{
    // Your code goes here
}
```
## Step 3: Extract Text from the Document
Inside the `using` block, use `parser.GetText()` to extract text from the document:
```csharp
using (TextReader reader = parser.GetText())
{
    // Your code goes here
}
```
## Step 4: Display the Extracted Text
Read and print the extracted text from the document:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Conclusion
In this tutorial, we've covered the basics of extracting text from a document using GroupDocs.Parser for .NET. By following these steps, you can easily integrate document text extraction capabilities into your C# applications.

## FAQ's
### Is GroupDocs.Parser compatible with various document formats?
Yes, GroupDocs.Parser supports a wide range of document formats, including PDF, Word, Excel, PowerPoint, and more.
### Can I extract metadata along with text using GroupDocs.Parser?
Yes, GroupDocs.Parser allows you to extract metadata, text, and other information from documents.
### Is there a trial version available for GroupDocs.Parser?
Yes, you can get a free trial version of GroupDocs.Parser from [here](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Parser?
Detailed documentation for GroupDocs.Parser is available [here](https://tutorials.groupdocs.com/parser/net/).
### How can I get technical support for GroupDocs.Parser?
You can seek technical support and ask questions on the GroupDocs.Parser forum [here](https://forum.groupdocs.com/c/parser/17).
