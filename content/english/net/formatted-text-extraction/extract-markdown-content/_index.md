---
title: Extract Markdown Content
linktitle: Extract Markdown Content
second_title: GroupDocs.Parser .NET API
description: Learn how to extract Markdown content from documents using GroupDocs.Parser for .NET. This tutorial provides step-by-step instructions for seamless text extraction.
weight: 13
url: /net/formatted-text-extraction/extract-markdown-content/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to extract Markdown content from documents. GroupDocs.Parser is a powerful library that allows developers to parse and extract text from various file formats seamlessly.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
- Visual Studio: Install Visual Studio on your system.
- GroupDocs.Parser for .NET: Download and install GroupDocs.Parser from [here](https://releases.groupdocs.com/parser/net/).
- Basic understanding of C#: Familiarity with C# programming language.

## Import Namespaces
First, you need to import the necessary namespaces into your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Instantiate the `Parser` class with the path to your sample file:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code goes here...
}
```
## Step 2: Extract Markdown Formatted Text
Inside the `using` block, use `GetFormattedText` method to extract formatted text as Markdown:
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Markdown)))
{
    // Code goes here...
}
```
## Step 3: Read and Output Extracted Content
Read the extracted Markdown content from the `TextReader`:
```csharp
string markdownContent = reader == null ? "Formatted text extraction isn't supported" : reader.ReadToEnd();
Console.WriteLine(markdownContent);
```

## Conclusion
In this tutorial, we've learned how to extract Markdown content from documents using GroupDocs.Parser for .NET. This powerful library simplifies the process of parsing and extracting text, enabling developers to work efficiently with various file formats.
## FAQ's
### Can GroupDocs.Parser handle different file formats?
Yes, GroupDocs.Parser supports a wide range of file formats including DOCX, PDF, PPTX, XLSX, and more.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser supports both .NET Framework and .NET Core.
### How can I get a temporary license for GroupDocs.Parser?
You can obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### Does GroupDocs.Parser provide support for developers?
Yes, you can get developer support on the [GroupDocs Forum](https://forum.groupdocs.com/c/parser/17).
### Where can I purchase a license for GroupDocs.Parser?
You can purchase a license [here](https://purchase.groupdocs.com/buy).