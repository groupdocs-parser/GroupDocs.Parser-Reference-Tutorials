---
title: Extract Images to Files
linktitle: Extract Images to Files
second_title: GroupDocs.Parser .NET API
description: Effortlessly extract images from various document types like PDF and DOCX using GroupDocs.Parser for .NET. Simplify your document parsing tasks.
weight: 13
url: /net/image-extraction/extract-images-to-files/
---
## Introduction
In this tutorial, you will learn how to use GroupDocs.Parser for .NET to extract images from various document formats such as PDF, Word, Excel, and PowerPoint. GroupDocs.Parser is a powerful library that enables developers to parse and extract text, metadata, images, and more from documents in a straightforward manner. This guide will walk you through the process of extracting images and saving them as individual files using C#.
## Prerequisites
Before you begin, ensure you have the following prerequisites in place:
1. Visual Studio: Make sure you have Visual Studio installed on your system.
2. GroupDocs.Parser for .NET: Download and install GroupDocs.Parser for .NET from [here](https://releases.groupdocs.com/parser/net/).
3. Sample Document: Prepare a sample document (e.g., PDF, DOCX, XLSX) from which you want to extract images.

## Import Namespaces
First, include the necessary namespaces in your C# code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create a Parser Instance
Instantiate the `Parser` class by providing the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code goes here
}
```
## Step 2: Extract Images from Document
Use the `GetImages()` method of the `Parser` object to retrieve images from the document.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Step 3: Check Support for Image Extraction
Verify if the document supports image extraction.
```csharp
if (images == null)
{
    Console.WriteLine("Page images extraction isn't supported");
    return;
}
```
## Step 4: Set Image Saving Options
Specify the format (`ImageFormat`) in which you want to save the extracted images (e.g., PNG).
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Step 5: Iterate and Save Images
Loop through the extracted images and save each image to a file.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Save the image to a PNG file
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## Conclusion
In this tutorial, you've learned how to use GroupDocs.Parser for .NET to extract images from documents using C#. This powerful library simplifies the process of parsing and extracting data from various file formats, making it an essential tool for document processing tasks in .NET applications.

## FAQ's
### Can I extract images from password-protected documents?
Yes, GroupDocs.Parser supports extracting images from password-protected documents if you provide the correct password during parsing.
### Which document formats are supported for image extraction?
GroupDocs.Parser supports a wide range of formats including PDF, DOCX, XLSX, PPTX, EPUB, and more.
### How can I handle exceptions during image extraction?
You can implement error handling in your code to catch and manage exceptions that may occur during image extraction.
### Is GroupDocs.Parser suitable for batch processing of documents?
Yes, you can use GroupDocs.Parser to process multiple documents in a batch, extracting images and other data efficiently.
### Does GroupDocs.Parser provide OCR capabilities for scanned documents?
GroupDocs.Parser currently does not support OCR (Optical Character Recognition) but excels in parsing structured data from documents.
