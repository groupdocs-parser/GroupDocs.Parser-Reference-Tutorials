---
title: Extract Text from Word Document
linktitle: Extract Text from Word Document
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from Word documents using GroupDocs.Parser for .NET. Step-by-step guide with code examples.
weight: 15
url: /net/word-document-processing/extract-text-from-word-document/
---
## Introduction
In this tutorial, we'll explore how to extract text from Word documents using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful .NET library that allows developers to work with various document formats, including Word documents, PDFs, and more. By the end of this guide, you'll be able to efficiently extract text from Word files using simple C# code.
## Prerequisites
Before we begin, ensure you have the following prerequisites in place:
- Visual Studio (or any preferred C# development environment)
- GroupDocs.Parser for .NET library installed (Download [here](https://releases.groupdocs.com/parser/net/))
- Basic knowledge of C# programming

## Import Namespaces
First, you need to import the necessary namespaces in your C# project to access the GroupDocs.Parser functionality.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of Parser Class
Begin by creating an instance of the `Parser` class, providing the path to your Word document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Your code for text extraction will go here
}
```
Replace `"YourSampleFile.docx"` with the path to your actual Word document.
## Step 2: Extract Text into a TextReader
Within the `using` block of the `Parser` instance, use the `GetText()` method to extract the text content into a `TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    // Your text processing code will go here
}
```
## Step 3: Read and Display Extracted Text
Now, inside the `TextReader` block, you can read and print the extracted text from the Word document.
```csharp
using (TextReader reader = parser.GetText())
{
    // Read the extracted text and print it
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusion
Congratulations! You've learned how to extract text from Word documents using GroupDocs.Parser for .NET. This simple yet powerful library allows you to integrate text extraction capabilities into your .NET applications efficiently.

## FAQ's
### Is GroupDocs.Parser compatible with all versions of .NET?
Yes, GroupDocs.Parser for .NET is compatible with .NET Framework 4.6.1 and later versions.
### Can I extract text from encrypted or password-protected Word documents?
GroupDocs.Parser supports extracting text from password-protected Word documents.
### Does GroupDocs.Parser support other document formats besides Word documents?
Yes, GroupDocs.Parser supports a wide range of document formats, including PDF, Excel, PowerPoint, and more.
### How can I obtain a temporary license for GroupDocs.Parser?
You can request a temporary license for GroupDocs.Parser [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find additional support or ask questions about GroupDocs.Parser?
You can visit the GroupDocs.Parser forum [here](https://forum.groupdocs.com/c/parser/17) for support and discussions.
