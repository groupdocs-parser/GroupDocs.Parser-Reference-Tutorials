---
title: Extract Text from Excel Document as HTML
linktitle: Extract Text from Excel Document as HTML
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from Excel documents and convert it into HTML using GroupDocs.Parser for .NET.
weight: 13
url: /net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## Introduction
In this tutorial, we'll explore how to use the GroupDocs.Parser for .NET to extract text from an Excel document and convert it into HTML format. GroupDocs.Parser is a powerful library that allows developers to work with various document formats, extracting text and metadata efficiently.
## Prerequisites
Before we begin, ensure you have the following set up:
- Visual Studio installed on your system.
- Basic understanding of C# programming.
- GroupDocs.Parser library for .NET. You can download it from [here](https://releases.groupdocs.com/parser/net/).
## Import Namespaces
Start by including the necessary namespaces in your C# project to access the GroupDocs.Parser functionalities.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Step 1: Create an Instance of Parser Class
First, instantiate the `Parser` class by providing the path to your Excel document.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Further code will go here
}
```
Replace `"YourSampleFile.xlsx"` with the path to your Excel file.
## Step 2: Extract Text as HTML
Within the `using` block of the `Parser` instance, use the `GetFormattedText` method to extract formatted text in HTML mode.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Further code will go here
    }
}
```
## Step 3: Read and Print Extracted HTML Text
Next, read the extracted HTML text from the `TextReader` and print it to the console.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Once executed, this code will extract the text from the Excel document and display it as HTML format in the console.
## Conclusion
In this tutorial, we learned how to use GroupDocs.Parser for .NET to extract text from an Excel document and convert it into HTML format. This library provides a straightforward way to work with various document formats, enabling developers to efficiently handle text extraction tasks in their applications.

## FAQ's
### Can GroupDocs.Parser handle other document formats besides Excel?
Yes, GroupDocs.Parser supports a wide range of file formats including PDF, Word, PowerPoint, and more.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser is compatible with both .NET Framework and .NET Core.
### Does GroupDocs.Parser preserve formatting during text extraction?
Yes, GroupDocs.Parser can preserve formatting such as fonts, styles, and layout during text extraction.
### Can I extract metadata from documents using GroupDocs.Parser?
Yes, GroupDocs.Parser allows extracting metadata like author, creation date, and more from supported document types.
### Is there a free trial available for GroupDocs.Parser?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/).
