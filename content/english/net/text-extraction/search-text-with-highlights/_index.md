---
title: Search Text with Highlights
linktitle: Search Text with Highlights
second_title: GroupDocs.Parser .NET API
description: Learn how to search and highlight text in documents using GroupDocs.Parser for .NET. Extract valuable insights efficiently.
weight: 24
url: /net/text-extraction/search-text-with-highlights/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to search for text within a document and highlight the search results. GroupDocs.Parser is a powerful library that allows you to work with various document formats and extract text, metadata, and more.
## Prerequisites
Before we begin, ensure you have the following:
1. GroupDocs.Parser for .NET: Download and install the library from [here](https://releases.groupdocs.com/parser/net/).
2. IDE: Use Visual Studio or any preferred IDE for .NET development.
3. Sample File: Prepare a sample document (e.g., PDF, DOCX) for text searching.

## Import Namespaces
First, start by importing the necessary namespaces in your .NET project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create Parser Instance
Begin by instantiating the `Parser` class with the path to your sample file:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code here
}
```
## Step 2: Define Highlight Options
Specify the `HighlightOptions` to configure how search results should be highlighted. For example, setting a context window of 15 characters:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Step 3: Search Text
Now, perform a text search within the document. Provide the keyword you want to search (e.g., "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Step 4: Process Search Results
Iterate through the search results and display the found text along with the highlights:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusion
In this tutorial, you learned how to use GroupDocs.Parser for .NET to search for text within documents and highlight the search results. This functionality can be immensely useful for text extraction and analysis in your .NET applications.

## FAQ's
### Is GroupDocs.Parser suitable for processing various document formats?
Yes, GroupDocs.Parser supports a wide range of document formats including PDF, DOCX, XLSX, PPTX, and more.
### Can I use GroupDocs.Parser to extract metadata from documents?
Absolutely! GroupDocs.Parser allows you to extract metadata, text, and structured data from documents.
### Where can I find support or ask questions about GroupDocs.Parser?
You can visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for any support-related queries.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can access a [free trial](https://releases.groupdocs.com/) of GroupDocs.Parser to evaluate its features.
### How can I purchase a license for GroupDocs.Parser?
You can purchase a license from [here](https://purchase.groupdocs.com/buy) and also obtain temporary licenses [here](https://purchase.groupdocs.com/temporary-license/).
