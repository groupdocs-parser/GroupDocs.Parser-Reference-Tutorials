---
title: Search Text by Pages
linktitle: Search Text by Pages
second_title: GroupDocs.Parser .NET API
description: Learn to search text by pages using GroupDocs.Parser for .NET. Extract specific content efficiently from documents in your .NET applications.
type: docs
weight: 22
url: /net/text-extraction/search-text-by-pages/
---
## Introduction
In the world of .NET development, efficiently parsing and extracting text from documents is a crucial task. GroupDocs.Parser for .NET offers powerful capabilities to work with various document formats, allowing developers to search and extract specific content seamlessly. This tutorial will guide you through the process of leveraging GroupDocs.Parser to search text by pages in your .NET applications.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites:
- Basic understanding of C# and .NET framework
- Visual Studio installed on your system
- GroupDocs.Parser for .NET library installed (Download from [here](https://releases.groupdocs.com/parser/net/))
- Sample file(s) for testing the search functionality
## Import Namespaces
Firstly, include the necessary namespaces in your project to access GroupDocs.Parser functionalities:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Begin by instantiating the `Parser` class with the path to your sample file:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Your code goes here
}
```
## Step 2: Search Text with Page Numbers
Utilize the `Search` method to look for specific keywords within the document along with page numbers:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## Step 3: Check Search Support
Verify if the search operation is supported for the document type:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## Step 4: Iterate Over Search Results
Iterate through the search results to retrieve indexed positions, page numbers, and the found text:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## Conclusion
In this tutorial, we've explored how to implement text search by pages using GroupDocs.Parser for .NET. By following these steps, you can efficiently integrate document parsing and searching functionalities into your .NET applications.

## FAQ's
### Is GroupDocs.Parser compatible with various document formats?
Yes, GroupDocs.Parser supports a wide range of document formats including DOCX, PDF, XLSX, PPTX, and more.
### Can I extract images and metadata from documents using GroupDocs.Parser?
Absolutely, GroupDocs.Parser allows extraction of images, metadata, and text from documents.
### Where can I find detailed documentation for GroupDocs.Parser?
You can access the documentation [here](https://reference.groupdocs.com/parser/net/).
### How can I obtain a temporary license for GroupDocs.Parser?
You can request a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I get support or assistance with GroupDocs.Parser?
For support and discussions, visit the GroupDocs.Parser forum [here](https://forum.groupdocs.com/c/parser/17).
