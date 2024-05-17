---
title: Extract Images from PDF
linktitle: Extract Images from PDF
second_title: GroupDocs.Parser .NET API
description: Learn how to extract images from PDF documents using GroupDocs.Parser for .NET. Step-by-step guide with code examples.
type: docs
weight: 12
url: /net/pdf-processing/extract-images-from-pdf/
---
## Introduction
In this tutorial, we will explore how to use GroupDocs.Parser for .NET to extract images from PDF documents. GroupDocs.Parser is a powerful library that enables developers to work with various document formats, including PDF, DOCX, PPTX, and more, in a .NET environment. By following these steps, you'll be able to extract images from PDF files effortlessly.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
- Visual Studio installed on your system
- Basic knowledge of C# programming
- GroupDocs.Parser for .NET library (Download [here](https://releases.groupdocs.com/parser/net/))

## Import Namespaces
To start, include the necessary namespaces in your C# code file.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
First, create an instance of the `Parser` class by providing the path to your sample PDF file.
```csharp
// Create an instance of Parser class
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code to extract images will go here
}
```
## Step 2: Extract Images from PDF
Within the `using` block, utilize the `GetImages` method of the `Parser` instance to retrieve a collection of images from the PDF document.
```csharp
// Extract images from the PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Step 3: Configure Image Saving Options
Define the options to specify how the extracted images should be saved. Here, we will save the images in PNG format.
```csharp
// Create options to save images in PNG format
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Step 4: Iterate Over Extracted Images and Save
Iterate through each image in the `images` collection and save them to PNG files sequentially.
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
In this tutorial, we have demonstrated how to extract images from PDF documents using GroupDocs.Parser for .NET. By following these steps, you can seamlessly integrate image extraction functionality into your .NET applications.

## FAQ's
### Is GroupDocs.Parser compatible with other document formats?
Yes, GroupDocs.Parser supports a wide range of document formats, including PDF, DOCX, XLSX, PPTX, and more.
### Can I modify the image extraction options?
Absolutely! GroupDocs.Parser provides various options to customize image extraction, such as image format and quality settings.
### Does GroupDocs.Parser require a license for commercial use?
Yes, a commercial license is required for using GroupDocs.Parser in production environments. Learn more [here](https://purchase.groupdocs.com/buy).
### Where can I find additional support or assistance?
Visit the GroupDocs.Parser [forum](https://forum.groupdocs.com/c/parser/17) for community support and guidance.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can obtain a free trial from [here](https://releases.groupdocs.com/) to explore the features of GroupDocs.Parser.
