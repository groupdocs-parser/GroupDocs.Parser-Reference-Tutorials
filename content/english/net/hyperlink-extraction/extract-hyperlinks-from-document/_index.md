---
title: Extract Hyperlinks from Document
linktitle: Extract Hyperlinks from Document
second_title: GroupDocs.Parser .NET API
description: Learn how to extract hyperlinks from documents using GroupDocs.Parser for .NET. Enhance your C# applications with this straightforward guide.
weight: 10
url: /net/hyperlink-extraction/extract-hyperlinks-from-document/
type: docs
---
# Extract Hyperlinks from Document

## Introduction
In this tutorial, we will delve into the powerful capabilities of GroupDocs.Parser for .NET, a versatile library that allows developers to extract hyperlinks from documents with ease. Hyperlink extraction is a common requirement in document processing, especially when dealing with text-based files such as PDFs or Word documents. By using GroupDocs.Parser, you can efficiently identify and extract hyperlinks along with their associated URLs from various document formats.
## Prerequisites
Before proceeding with this tutorial, ensure you have the following prerequisites:
- Basic knowledge of C# programming
- Visual Studio installed on your system
- GroupDocs.Parser for .NET library, which can be downloaded [here](https://releases.groupdocs.com/parser/net/)
## Import Namespaces
To begin, import the necessary namespaces into your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

Now, let's break down each example into multiple steps to guide you through the process of hyperlink extraction using GroupDocs.Parser for .NET:
## Step 1: Create an Instance of the Parser Class
First, instantiate the `Parser` class by providing the path to your sample document:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Your code for hyperlink extraction will go here
}
```
Replace `"YourSampleFile.docx"` with the path to your target document.
## Step 2: Check Hyperlink Extraction Support
Before extracting hyperlinks, it's important to verify if the document format supports hyperlink extraction:
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
This step ensures that hyperlink extraction is feasible for the given document.
## Step 3: Extract Hyperlinks
Proceed to extract hyperlinks from the document using the `GetHyperlinks()` method:
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
This line retrieves a collection of `PageHyperlinkArea` objects containing hyperlink information.
## Step 4: Iterate Over Extracted Hyperlinks
Iterate through the collection of extracted hyperlinks and retrieve their text and URL:
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    // Print the hyperlink text
    Console.WriteLine(hyperlink.Text);
    
    // Print the hyperlink URL
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); // Adds a blank line for readability
}
```
By iterating over the `hyperlinks` collection, you can access and print the text and URL of each hyperlink.
## Conclusion
In this tutorial, we explored how to extract hyperlinks from documents using GroupDocs.Parser for .NET. Leveraging the functionalities provided by this library, developers can effortlessly integrate hyperlink extraction capabilities into their C# applications.

## FAQ's
### Can GroupDocs.Parser handle hyperlink extraction from various document formats?
Yes, GroupDocs.Parser supports hyperlink extraction from a wide range of file formats including PDF, Word, Excel, PowerPoint, and more.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can access a free trial of GroupDocs.Parser [here](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Parser?
Detailed documentation for GroupDocs.Parser can be found [here](https://tutorials.groupdocs.com/parser/net/).
### How can I obtain a temporary license for GroupDocs.Parser?
You can obtain a temporary license for GroupDocs.Parser [here](https://purchase.groupdocs.com/temporary-license/).
### Does GroupDocs offer support for troubleshooting?
Yes, you can seek support and troubleshooting assistance at the GroupDocs [forum](https://forum.groupdocs.com/c/parser/17).
