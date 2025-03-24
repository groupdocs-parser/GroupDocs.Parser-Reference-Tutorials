---
title: Extract Hyperlinks from Document Page
linktitle: Extract Hyperlinks from Document Page
second_title: GroupDocs.Parser .NET API
description: Learn how to extract hyperlinks from documents using GroupDocs.Parser for .NET. Step-by-step guide for hyperlink extraction in C#.
weight: 11
url: /net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to extract hyperlinks from documents step-by-step. GroupDocs.Parser is a powerful library that enables developers to parse various document formats and extract text, metadata, and other elements.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio: Install Visual Studio on your development machine.
- GroupDocs.Parser Library: Download and tutorials the GroupDocs.Parser library. You can get it from [here](https://releases.groupdocs.com/parser/net/).
- Sample Document: Prepare a sample document (e.g., DOCX, PDF) containing hyperlinks for testing.

## Import Namespaces
First, include the necessary namespaces to use GroupDocs.Parser functionalities:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create Parser Instance
Instantiate the `Parser` class with the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code goes here...
}
```
## Step 2: Check Hyperlink Extraction Support
Ensure that the document supports hyperlink extraction before proceeding.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Step 3: Retrieve Document Information
Get basic information about the document and check if it contains pages.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Step 4: Iterate Over Document Pages
Iterate through each page of the document.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extract hyperlinks from the current page
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iterate over extracted hyperlinks
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Blank line for readability
    }
}
```

## Conclusion
In this tutorial, we've covered the basics of using GroupDocs.Parser for .NET to extract hyperlinks from documents. You learned how to initialize the parser, check for hyperlink support, retrieve document information, and iterate through document pages to extract hyperlinks efficiently.

## FAQ's
### Can I extract hyperlinks from different document formats?
Yes, GroupDocs.Parser supports various formats like DOCX, PDF, PPTX, etc., for hyperlink extraction.
### Is GroupDocs.Parser easy to integrate into existing .NET applications?
Absolutely, GroupDocs.Parser is designed to be straightforward and can be easily integrated into your .NET projects.
### Can I extract other metadata along with hyperlinks using GroupDocs.Parser?
Yes, besides hyperlinks, you can extract text, images, and metadata from documents using this library.
### Does GroupDocs.Parser handle encrypted or password-protected documents?
GroupDocs.Parser can parse password-protected documents if the password is provided.
### Is there a trial version available to test before purchasing?
Yes, you can download a free trial version [here](https://releases.groupdocs.com/).
