---
title: Search Text by Regular Expression (Regex)
linktitle: Search Text by Regular Expression (Regex)
second_title: GroupDocs.Parser .NET API
description: Learn how to search text using regular expressions in documents using GroupDocs.Parser for .NET. Extract specific content effortlessly.
weight: 23
url: /net/text-extraction/search-text-by-regex/
type: docs
---
# Search Text by Regular Expression (Regex)

## Introduction
In this tutorial, we'll delve into using GroupDocs.Parser for .NET to search text by regular expression (Regex) within documents. GroupDocs.Parser is a powerful library that allows developers to extract text and metadata from various file formats such as PDF, DOCX, XLSX, and more. Searching for text using regular expressions is particularly useful for finding patterns or specific content within documents efficiently.
## Prerequisites
Before diving into this tutorial, ensure you have the following:
1. Visual Studio: Install Visual Studio IDE for .NET development.
2. GroupDocs.Parser for .NET: Download and install GroupDocs.Parser for .NET from [here](https://releases.groupdocs.com/parser/net/).
3. Sample File: Prepare a sample document (PDF, DOCX, etc.) for testing the search functionality.

## Import Namespaces
First, start by including the necessary namespaces in your C# code:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Instantiate the `Parser` class by providing the path to your sample file:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code goes here
}
```
Replace `"YourSampleFile.pdf"` with the path to your actual file.
## Step 2: Search Using Regular Expression
Define and execute the search using a regular expression pattern. For instance, to find numeric sequences (e.g., integers) within the document:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
In this example, `[0-9]+` is a regular expression pattern that matches one or more digits.
## Step 3: Check Search Support
Verify if the search operation is supported for the document type:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Step 4: Iterate Over Search Results
Iterate through the search results and process each match:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
This loop will print the position and the matching text found within the document.

## Conclusion
In conclusion, leveraging GroupDocs.Parser for .NET allows efficient text searching using regular expressions across various document formats. By following this guide, developers can seamlessly integrate document parsing and regex-based text extraction into their .NET applications.

## FAQ's
### Can GroupDocs.Parser search within encrypted documents?
No, GroupDocs.Parser cannot search within encrypted or password-protected documents.
### Does GroupDocs.Parser support OCR (Optical Character Recognition)?
No, GroupDocs.Parser does not perform OCR. It relies on text extraction from the document's internal structure.
### Can I search for complex patterns using regular expressions?
Yes, GroupDocs.Parser supports full-fledged regular expressions, enabling complex pattern matching within documents.
### Which document formats are supported for text extraction?
GroupDocs.Parser supports a wide range of formats, including PDF, DOCX, XLSX, PPTX, and more.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser is compatible with .NET Core for cross-platform development.
