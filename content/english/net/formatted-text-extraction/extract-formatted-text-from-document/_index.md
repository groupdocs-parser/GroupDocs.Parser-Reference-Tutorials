---
title: Extract Formatted Text from Document
linktitle: Extract Formatted Text from Document
second_title: GroupDocs.Parser .NET API
description: Learn how to extract formatted text from documents using GroupDocs.Parser for .NET. Simple and efficient text extraction for your applications.
type: docs
weight: 10
url: /net/formatted-text-extraction/extract-formatted-text-from-document/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Parser for .NET to extract formatted text from various types of documents. GroupDocs.Parser is a powerful library that allows developers to work with documents in a simplified and efficient manner. By the end of this guide, you'll be able to seamlessly integrate text extraction capabilities into your .NET applications.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio: Make sure you have Visual Studio installed on your system.
- GroupDocs.Parser for .NET: Download and install the GroupDocs.Parser library from [here](https://releases.groupdocs.com/parser/net/).
- Document Samples: Prepare sample documents (e.g., PDF, DOCX) for text extraction.
## Import Namespaces
First, include the necessary namespaces in your C# code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
Begin by initializing a `Parser` object with the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Text extraction code goes here
}
```
Replace `"YourSampleFile.pdf"` with the path to your document file.

## Step 2: Extract Formatted Text
Within the `using` block, use the `GetFormattedText` method to extract formatted text from the document. Specify the desired output format (e.g., HTML) using `FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extract formatted text into the reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Check if extraction is supported
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Read and display the extracted text
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusion
Congratulations! You've learned how to extract formatted text from documents using GroupDocs.Parser for .NET. This versatile library opens up possibilities for text processing and analysis within your applications.

## FAQ's
### Q: Can GroupDocs.Parser extract text from password-protected documents?
A: Yes, GroupDocs.Parser supports extracting text from password-protected documents.
### Q: Which document formats are supported by GroupDocs.Parser?
A: GroupDocs.Parser supports a wide range of formats including PDF, DOCX, XLSX, PPTX, and more.
### Q: How can I get a temporary license for GroupDocs.Parser?
A: You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Q: Does GroupDocs.Parser provide support for image extraction from documents?
A: Yes, GroupDocs.Parser supports image extraction alongside text extraction.
### Q: Where can I find additional support or ask questions about GroupDocs.Parser?
A: Visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for support and discussions.
