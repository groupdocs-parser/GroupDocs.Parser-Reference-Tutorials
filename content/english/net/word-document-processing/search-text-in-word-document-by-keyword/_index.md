---
title: Search Text in Word Document by Keyword
linktitle: Search Text in Word Document by Keyword
second_title: GroupDocs.Parser .NET API
description: Learn how to search for text in Word documents using GroupDocs.Parser for .NET. Extract specific keywords efficiently.
weight: 18
url: /net/word-document-processing/search-text-in-word-document-by-keyword/
---

# Search Text in Word Document by Keyword

## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to search for specific text within a Word document using C#. GroupDocs.Parser is a powerful library that allows developers to extract text and metadata from various document formats, including Word documents.
## Prerequisites
Before getting started, ensure you have the following prerequisites:
1. Development Environment: Install Visual Studio or another compatible IDE.
2. GroupDocs.Parser Library: Download and install the GroupDocs.Parser for .NET library from the [website](https://releases.groupdocs.com/parser/net/).
3. Sample Word Document: Prepare a sample Word document to use for text searching.

## Import Namespaces
Begin by importing the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of Parser Class
First, create an instance of the `Parser` class by passing the path to your sample Word document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code goes here
}
```
## Step 2: Search for a Keyword
Next, use the `Search` method of the `Parser` class to search for a specific keyword within the document.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
Replace `"keyword"` with the text you want to search for within the document.
## Step 3: Iterate Over Search Results
Iterate over the search results using a `foreach` loop to access each `SearchResult` object.
```csharp
foreach (SearchResult result in searchResults)
{
    // Code to handle each search result
}
```
## Step 4: Access Search Result Details
Within the loop, you can access the position and text of each search result using the `Position` and `Text` properties of the `SearchResult` object.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
This code snippet prints the index (`Position`) and the found text (`Text`) for each search result to the console.

## Conclusion
In this tutorial, you've learned how to use GroupDocs.Parser for .NET to search for specific text within a Word document. This library provides a convenient way to extract and manipulate content from various document formats programmatically.

## FAQ's
### Can GroupDocs.Parser handle other document formats besides Word?
Yes, GroupDocs.Parser supports a wide range of formats, including PDF, Excel, PowerPoint, and more.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser is compatible with both .NET Framework and .NET Core.
### How do I obtain a temporary license for GroupDocs.Parser?
You can request a temporary license from the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/).
### Where can I find additional support or ask questions about GroupDocs.Parser?
Visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for community support and discussions.
### Can I try GroupDocs.Parser for free before purchasing?
Yes, you can download a free trial version from the [GroupDocs releases page](https://releases.groupdocs.com/).
