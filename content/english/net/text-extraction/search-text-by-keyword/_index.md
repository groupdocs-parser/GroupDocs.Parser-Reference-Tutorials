---
title: Search Text by Keyword
linktitle: Search Text by Keyword
second_title: GroupDocs.Parser .NET API
description: Learn how to search text by keyword in documents using GroupDocs.Parser for .NET. Efficiently extract relevant content with ease.
type: docs
weight: 21
url: /net/text-extraction/search-text-by-keyword/
---
## Introduction
In this tutorial, we will delve into using GroupDocs.Parser for .NET to search text by keyword within documents. GroupDocs.Parser is a powerful library that enables developers to extract text, metadata, and other information from various file formats, such as PDFs, Microsoft Office documents, and more. Searching for specific keywords within these documents can be essential for applications dealing with large volumes of textual data.
## Prerequisites
Before we begin, ensure you have the following set up:
1. Development Environment: Visual Studio or any preferred .NET IDE.
2. GroupDocs.Parser for .NET: Download the library from [here](https://releases.groupdocs.com/parser/net/).
3. Access to Sample Files: Prepare a sample file (e.g., PDF, DOCX) to test the keyword search functionality.

## Import Namespaces
First, you need to include the necessary namespaces in your project.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Instantiate the Parser Class
Begin by creating an instance of the `Parser` class and provide the path to your sample file.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Search a keyword
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Iterate over search results
    foreach (SearchResult result in searchResults)
    {
        // Print the index and found text
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Step 2: Search for a Keyword
Within the `using` block, call the `Search` method on the `parser` object, passing the desired keyword as an argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
Replace `"test"` with the keyword you wish to search for within the document.
## Step 3: Iterate over Search Results
Next, iterate over the search results obtained from the `Search` method using a `foreach` loop.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
For each `SearchResult` object `result`, you can access its `Position` (index) and `Text` (the found text).

## Conclusion
In this tutorial, we explored how to use GroupDocs.Parser for .NET to search text by keyword within documents effortlessly. Leveraging the `Search` method of the `Parser` class allows for efficient retrieval of relevant text snippets based on specific search terms.

## FAQ's
### Is GroupDocs.Parser compatible with various document formats?
Yes, GroupDocs.Parser supports a wide range of file formats, including PDF, DOCX, XLSX, PPTX, and more.
### Can I perform advanced text extraction operations using GroupDocs.Parser?
Absolutely! Apart from text search, GroupDocs.Parser enables metadata extraction, structured text extraction, and more.
### Where can I find detailed documentation for GroupDocs.Parser?
Explore the complete documentation [here](https://reference.groupdocs.com/parser/net/).
### How can I get support or assistance with GroupDocs.Parser-related queries?
Visit the GroupDocs forum for support and discussions [here](https://forum.groupdocs.com/c/parser/17).
### Is there a trial version available to evaluate GroupDocs.Parser before purchasing?
Yes, you can access the free trial [here](https://releases.groupdocs.com/).
