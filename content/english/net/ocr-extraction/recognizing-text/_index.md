---
title: Recognizing Text
linktitle: Recognizing Text
second_title: GroupDocs.Parser .NET API
description: Extract text from various document formats efficiently with GroupDocs.Parser for .NET. Easy integration and powerful OCR capabilities.
weight: 12
url: /net/ocr-extraction/recognizing-text/
---

# Recognizing Text

## Introduction
In the realm of .NET development, efficient text extraction from various document formats is paramount. GroupDocs.Parser for .NET provides a robust solution to extract text seamlessly. In this tutorial, we will delve into using GroupDocs.Parser step-by-step to recognize and extract text from documents.
## Prerequisites
Before we dive into using GroupDocs.Parser, ensure you have the following prerequisites:
- Basic understanding of C# programming
- Visual Studio installed on your machine
- Access to the internet for package downloads and documentation tutorialss

## Import Namespaces
Begin by importing the necessary namespaces to leverage GroupDocs.Parser functionalities:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Install GroupDocs.Parser
Firstly, download and install the GroupDocs.Parser library. You can acquire it from the [download link](https://releases.groupdocs.com/parser/net/).
## Step 2: Get a Temporary License
To use GroupDocs.Parser, obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
## Step 3: Initializing ParserSettings
Create an instance of `ParserSettings` class to configure text extraction settings, including OCR connectors if needed.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Step 4: Using Parser to Extract Text
Now, create an instance of `Parser` class with the configured settings.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx", settings))
{
    // Configure TextOptions for OCR usage
    TextOptions options = new TextOptions(false, true);
    // Extract text using OCR
    using (TextReader reader = parser.GetText(options))
    {
        // Display extracted text or a 'not supported' message
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
In this snippet:
- Replace `"YourSampleFile.docx"` with the path to your target document.
- `TextOptions` is configured to enable OCR and optimize text extraction.

## Conclusion
Congratulations! You've learned how to integrate GroupDocs.Parser for .NET into your projects to extract text efficiently. Explore the extensive [documentation](https://tutorials.groupdocs.com/parser/net/) for advanced features and optimizations.

## FAQ's
### Is GroupDocs.Parser suitable for extracting text from PDF files?
Yes, GroupDocs.Parser supports text extraction from various formats, including PDF.
### Can I integrate GroupDocs.Parser into my ASP.NET application?
Absolutely, GroupDocs.Parser can be seamlessly integrated into ASP.NET applications.
### Does GroupDocs.Parser require a license for commercial use?
Yes, a license is required for commercial usage. Get a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### What document formats are supported by GroupDocs.Parser?
GroupDocs.Parser supports a wide range of formats, including DOCX, PDF, XLSX, and more.
### How can I seek support or ask questions related to GroupDocs.Parser?
Visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for support and discussions.
