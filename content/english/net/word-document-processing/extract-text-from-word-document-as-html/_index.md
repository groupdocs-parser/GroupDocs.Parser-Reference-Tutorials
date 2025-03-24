---
title: Extract Text from Word Document as HTML
linktitle: Extract Text from Word Document as HTML
second_title: GroupDocs.Parser .NET API
description: Learn how to use GroupDocs.Parser for .NET to extract text from Word documents and save it as HTML. Step-by-step tutorial with code examples.
weight: 16
url: /net/word-document-processing/extract-text-from-word-document-as-html/
---

# Extract Text from Word Document as HTML

## Introduction
GroupDocs.Parser for .NET is a powerful document parsing library that enables developers to extract text and metadata from various file formats seamlessly. In this tutorial, we'll focus on leveraging GroupDocs.Parser to extract text from Word documents and save it as HTML. This process is essential for tasks like content analysis, indexing, or converting documents into web-friendly formats. By the end of this guide, you'll have a clear understanding of how to use GroupDocs.Parser efficiently in your .NET applications.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites:
- Basic knowledge of C# programming.
- Visual Studio installed on your development machine.
- GroupDocs.Parser for .NET library. You can download it from [here](https://releases.groupdocs.com/parser/net/).
- Access to a sample Word document for testing purposes.
## Import Namespaces
To begin, you need to import the necessary namespaces into your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Follow these detailed steps to extract text from a Word document and save it as HTML using GroupDocs.Parser for .NET:
## Step 1: Create an Instance of Parser Class
First, create an instance of the `Parser` class by providing the path to your sample Word document:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Continue to Step 2...
}
```
Replace `"YourSampleFile.docx"` with the path to your Word document.
## Step 2: Extract Formatted Text as HTML
Next, use the `GetFormattedText` method along with `FormattedTextOptions` to extract the text in HTML format:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extract a formatted text into the reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Continue to Step 3...
    }
}
```
## Step 3: Read and Output the Extracted HTML
Finally, read the extracted HTML content from the `TextReader` and print it to the console:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extract a formatted text into the reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Print the formatted text as HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusion
In this tutorial, we've explored how to use GroupDocs.Parser for .NET to extract text from a Word document and save it as HTML. This library offers a straightforward and efficient way to parse document content, making it an invaluable tool for document processing tasks in .NET applications.

## FAQ's
### How can I obtain a temporary license for GroupDocs.Parser?
You can request a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find more documentation for GroupDocs.Parser?
Detailed documentation is available [here](https://tutorials.groupdocs.com/parser/net/).
### Is there a free trial available for GroupDocs.Parser?
Yes, you can access the free trial version [here](https://releases.groupdocs.com/).
### How do I get support for GroupDocs.Parser?
Visit the support forum [here](https://forum.groupdocs.com/c/parser/17).
### What types of documents does GroupDocs.Parser support?
GroupDocs.Parser supports various document formats including Word, PDF, Excel, PowerPoint, and more.
