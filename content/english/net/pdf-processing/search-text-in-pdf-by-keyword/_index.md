---
title: Search Text in PDF by Keyword
linktitle: Search Text in PDF by Keyword
second_title: GroupDocs.Parser .NET API
description: Learn how to search for specific text in PDF documents using GroupDocs.Parser for .NET. Integrate powerful text search capabilities into your .NET efficiently.
weight: 18
url: /net/pdf-processing/search-text-in-pdf-by-keyword/
---

# Search Text in PDF by Keyword

## Introduction
In this tutorial, we will explore how to leverage GroupDocs.Parser for .NET to search for specific text within PDF documents using keywords. GroupDocs.Parser is a powerful document parsing API that allows developers to extract text, metadata, images, and more from various document formats in .NET applications. Searching for text within PDFs is a common requirement in document processing applications, and GroupDocs.Parser simplifies this task with its intuitive API.
## Prerequisites
Before we begin, ensure you have the following prerequisites set up:
- GroupDocs.Parser for .NET: Download and install GroupDocs.Parser from [here](https://releases.groupdocs.com/parser/net/).
- Development Environment: Make sure you have a working development environment with .NET installed.
- Sample PDF File: Prepare a sample PDF file that contains the text you want to search within.

## Import Namespaces
First, include the necessary namespaces in your .NET project to use GroupDocs.Parser functionalities:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of `Parser` Class
Initialize an instance of the `Parser` class by providing the path to your sample PDF file:
```csharp
using (Parser parser = new Parser("path_to_your_sample_file.pdf"))
{
    // Your code for searching text will go here
}
```
## Step 2: Search for a Keyword
Inside the `using` block, use the `Search` method of the `Parser` instance to look for a specific keyword within the PDF:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("your_keyword");
```
Replace `"your_keyword"` with the actual text you want to search for within the PDF.
## Step 3: Iterate Over Search Results
Now, iterate over the search results using a `foreach` loop to access each `SearchResult` object:
```csharp
foreach (SearchResult result in searchResults)
{
    // Your code to handle each search result goes here
}
```
Within this loop, you can process each `SearchResult` object to get the position and text where the keyword was found.
## Step 4: Process Search Results
Inside the loop, you can print or process each search result according to your application's requirements:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
    // Or perform any other action with the search result
}
```

## Conclusion
In this tutorial, we've learned how to search for specific text within PDF documents using GroupDocs.Parser for .NET. By following the step-by-step guide, you can integrate text search functionality into your .NET applications efficiently.

## FAQ's
### Can GroupDocs.Parser handle other document formats besides PDF?
Yes, GroupDocs.Parser supports various formats including Microsoft Office documents, EPUB, HTML, and more.
### Is GroupDocs.Parser suitable for large-scale document processing?
Absolutely, GroupDocs.Parser is designed to handle large documents efficiently with minimal memory usage.
### Does GroupDocs.Parser require internet connectivity to function?
No, GroupDocs.Parser works entirely offline within your .NET application.
### Can I extract images along with text using GroupDocs.Parser?
Yes, GroupDocs.Parser allows extraction of images, text, metadata, and more from documents.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can start a free trial [here](https://releases.groupdocs.com/).
