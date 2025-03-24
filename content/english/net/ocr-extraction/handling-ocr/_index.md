---
title: Handling OCR
linktitle: Handling OCR
second_title: GroupDocs.Parser .NET API
description: Learn how to handle OCR using GroupDocs.Parser for .NET. Extract text from images and scanned documents efficiently.
weight: 11
url: /net/ocr-extraction/handling-ocr/
---

# Handling OCR

## Introduction
In this tutorial, we will explore how to use GroupDocs.Parser for .NET to handle Optical Character Recognition (OCR) tasks efficiently. This library provides powerful tools to extract text from documents, and with OCR, you can extract text even from images or scanned documents. Let's dive into the process step by step.
## Prerequisites
Before we begin, make sure you have the following set up:
- GroupDocs.Parser for .NET Library: Download the library from [here](https://releases.groupdocs.com/parser/net/).
- Your Sample File: Prepare a sample file (document or image) from which you want to extract text.
- Basic knowledge of C# and .NET environment.

## Import Namespaces
First, you need to import the necessary namespaces to use GroupDocs.Parser functionalities in your .NET application.
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
## Step 1: Create Parser Settings with OCR Connector
Initialize the `ParserSettings` class with the OCR connector. For instance, using Aspose OCR on-premise.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Step 2: Configure OCR Options
Set up an `OcrEventHandler` to handle warnings during OCR processing.
```csharp
OcrEventHandler handler = new OcrEventHandler();
OcrOptions ocrOptions = new OcrOptions(handler);
```
## Step 3: Configure Text Extraction Options
Create `TextOptions` to enable OCR-based text extraction.
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Step 4: Extract Text using OCR
Instantiate the `Parser` class with the settings and extract text using OCR.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    using (TextReader reader = parser.GetText(options))
    {
        if (reader == null)
        {
            Console.WriteLine("Text extraction isn't supported.");
        }
        else
        {
            Console.WriteLine(reader.ReadToEnd());
        }
    }
    if (handler.HasWarnings)
    {
        Console.WriteLine("The following warnings occurred during text recognition:");
        foreach (string w in handler.Warnings)
        {
            Console.WriteLine("\t* " + w);
        }
    }
    else
    {
        Console.WriteLine("Text recognition was performed without any warnings.");
    }
}
```

## Conclusion
By following these steps, you can leverage GroupDocs.Parser for .NET to handle OCR tasks effectively within your applications. Extracting text from images or scanned documents becomes seamless with the powerful capabilities offered by this library.

## FAQ's
### Is GroupDocs.Parser for .NET compatible with different file formats?
Yes, GroupDocs.Parser supports a wide range of file formats including PDF, DOCX, PPTX, XLSX, images (JPEG, PNG, TIFF), and more.
### Can I use GroupDocs.Parser for .NET in my commercial projects?
Yes, you can integrate GroupDocs.Parser for .NET into your commercial applications after purchasing a license.
### Does GroupDocs.Parser handle encrypted or password-protected files?
GroupDocs.Parser can parse and extract text from password-protected PDF documents.
### Is there a trial version available for GroupDocs.Parser for .NET?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### Where can I find support or ask questions related to GroupDocs.Parser for .NET?
You can visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17) for any support queries or discussions.
