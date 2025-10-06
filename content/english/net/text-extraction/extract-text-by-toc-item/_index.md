---
title: Extract Text by Table of Contents (TOC) Item
linktitle: Extract Text by Table of Contents (TOC) Item
second_title: GroupDocs.Parser .NET API
description: Extract text by Table of Contents (TOC) using GroupDocs.Parser for .NET. Learn efficient document parsing techniques for structured data extraction.
weight: 15
url: /net/text-extraction/extract-text-by-toc-item/
type: docs
---
# Extract Text by Table of Contents (TOC) Item

## Introduction
In this tutorial, we will explore how to utilize GroupDocs.Parser for .NET to extract text based on Table of Contents (TOC) items from documents. GroupDocs.Parser is a powerful tool that allows efficient document parsing and extraction.
## Prerequisites
Before proceeding with this tutorial, ensure you have the following prerequisites:
1. Visual Studio: Install Visual Studio IDE on your system.
2. GroupDocs.Parser for .NET: Download and install GroupDocs.Parser for .NET from [here](https://releases.groupdocs.com/parser/net/).
3. A Sample Document with TOC: Prepare a document (e.g., PDF, DOCX) that contains a Table of Contents.

## Importing Namespaces
First, include the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of Parser Class
Instantiate the `Parser` class with the path to your sample document:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // Continue with next steps here...
}
```
## Step 2: Extract Table of Contents (TOC)
Get the Table of Contents (TOC) items from the document:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## Step 3: Iterate Over TOC Items and Extract Text
Iterate through each TOC item and extract the corresponding text:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusion
This tutorial has demonstrated how to extract text from a document based on Table of Contents (TOC) items using GroupDocs.Parser for .NET. By following the outlined steps, you can efficiently parse and extract specific content from your documents programmatically.

## FAQ's
### What file formats does GroupDocs.Parser support?
GroupDocs.Parser supports a wide range of document formats, including PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and more.
### Can I extract structured data like tables or images using GroupDocs.Parser?
Yes, GroupDocs.Parser provides APIs to extract structured data like tables, images, and metadata from various document types.
### Is GroupDocs.Parser suitable for large documents?
GroupDocs.Parser is optimized for handling large documents efficiently, enabling seamless extraction of content from extensive files.
### How can I get technical support for GroupDocs.Parser?
You can seek technical support and interact with the community at [GroupDocs.Parser Forum](https://forum.groupdocs.com/c/parser/17).
### Does GroupDocs offer a free trial for evaluation?
Yes, you can download a free trial version of GroupDocs.Parser from [here](https://releases.groupdocs.com/).
