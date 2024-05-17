---
title: Load Document from Stream
linktitle: Load Document from Stream
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from various document formats in .NET using GroupDocs.Parser. Step-by-step guide with code examples.
type: docs
weight: 12
url: /net/document-loading/load-document-from-stream/
---
## Introduction
In the realm of document processing in .NET applications, extracting text from various file formats is a common requirement. GroupDocs.Parser for .NET offers a powerful solution to seamlessly parse and extract text from a diverse range of documents. This tutorial will guide you through the process of utilizing GroupDocs.Parser to extract text from documents step by step.
## Prerequisites
Before diving into using GroupDocs.Parser for .NET, ensure you have the following set up:
- Development Environment: Visual Studio or any other .NET development environment.
- GroupDocs.Parser for .NET Package: Download and install the GroupDocs.Parser for .NET library from [here](https://releases.groupdocs.com/parser/net/).
- Document Samples: Have sample documents ready for text extraction.
## Importing Namespaces
Begin by importing the necessary namespaces into your .NET project to access GroupDocs.Parser functionalities.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

The following steps demonstrate how to extract text from a document using GroupDocs.Parser from a stream.
## Step 1: Load Document from Stream
```csharp
// Create the stream
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Create an instance of Parser class with the stream
    using (Parser parser = new Parser(stream))
    {
        // Extract text into the reader
        using (TextReader reader = parser.GetText())
        {
            // Print text from the document
            // If text extraction isn't supported, the reader will be null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
In this example:
- We open a file stream for the document file (`YourSampleFile.docx`).
- Initialize a `Parser` instance with the stream.
- Use `parser.GetText()` to retrieve a `TextReader` containing the extracted text.
- Print out the extracted text or a message if text extraction isn't supported for the document format.
## Conclusion
GroupDocs.Parser for .NET simplifies text extraction from various document formats, enabling developers to efficiently process and utilize textual content within their applications. By following the steps outlined in this tutorial, you can seamlessly integrate document text extraction capabilities into your .NET projects.

## FAQ's
### What document formats are supported by GroupDocs.Parser for .NET?
GroupDocs.Parser supports a wide range of document formats including DOCX, PDF, XLSX, PPTX, EPUB, and more.
### Can GroupDocs.Parser extract images or metadata from documents?
Yes, GroupDocs.Parser can extract images, metadata, and text from various document types.
### Is GroupDocs.Parser compatible with .NET Core applications?
Yes, GroupDocs.Parser is compatible with both .NET Framework and .NET Core applications.
### How can I obtain a temporary license for GroupDocs.Parser?
You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find more support or documentation for GroupDocs.Parser?
For additional support, visit the [GroupDocs.Parser Forum](https://forum.groupdocs.com/c/parser/17) or refer to the [documentation](https://reference.groupdocs.com/parser/net/).

