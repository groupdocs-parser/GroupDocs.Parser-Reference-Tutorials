---
title: Extract Images from Document
linktitle: Extract Images from Document
second_title: GroupDocs.Parser .NET API
description: Extract images from documents effortlessly using GroupDocs.Parser for .NET. Your document processing capabilities and streamline image extraction tasks efficiently.
weight: 11
url: /net/image-extraction/extract-images-from-document/
---

# Extract Images from Document

## Introduction
In this tutorial, we will explore how to extract images from documents using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful library that enables developers to extract text, metadata, images, and more from various document formats.
## Prerequisites
Before you begin, ensure you have the following prerequisites set up:
- Visual Studio: Install Visual Studio on your machine.
- GroupDocs.Parser for .NET: Download and install GroupDocs.Parser from the [download page](https://releases.groupdocs.com/parser/net/).
- Sample Document: Prepare a sample document (PDF, DOCX, etc.) from which you want to extract images.

## Import Namespaces
Start by importing the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Step 1: Create an Instance of the Parser Class
First, create an instance of the `Parser` class by providing the path to your sample document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Your code goes here
}
```
Replace `"YourSampleFile.pdf"` with the path to your document file.
## Step 2: Extract Images from the Document
Next, extract images from the document using the `GetImages()` method.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
The `GetImages()` method returns a collection of `PageImageArea` objects representing images found in the document.
## Step 3: Check Images Extraction Support
Before iterating over the images, check if image extraction is supported for the document.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
This step ensures that the document contains extractable images.
## Step 4: Iterate Over Extracted Images
Now, iterate over the extracted images to access detailed information about each image, such as page index, rectangle coordinates, and image type.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
This loop prints out information about each extracted image, including its location and type.

## Conclusion
In this tutorial, we learned how to use GroupDocs.Parser for .NET to extract images from documents programmatically. By following these steps, you can integrate document image extraction functionality into your .NET applications seamlessly.

## FAQ's
### Can GroupDocs.Parser extract images from all document formats?
GroupDocs.Parser supports extracting images from various formats, including PDF, DOCX, XLSX, and more.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can access a free trial of GroupDocs.Parser from the [website](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Parser?
Detailed documentation for GroupDocs.Parser can be found [here](https://tutorials.groupdocs.com/parser/net/).
### How can I obtain a temporary license for GroupDocs.Parser?
You can obtain a temporary license from the [temporary license page](https://purchase.groupdocs.com/temporary-license/).
### Where can I get support for GroupDocs.Parser?
For technical support and assistance, visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17).
