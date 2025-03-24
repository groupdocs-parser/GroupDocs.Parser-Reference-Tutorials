---
title: Extract Text in Raw Mode
linktitle: Extract Text in Raw Mode
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from documents using GroupDocs.Parser for .NET. Easy, efficient, and seamless text extraction within your .NET applications.
weight: 19
url: /net/text-extraction/extract-text-in-raw-mode/
---
## Introduction
In this tutorial, we will explore how to utilize GroupDocs.Parser for .NET to extract text from various document formats efficiently. GroupDocs.Parser is a powerful library that enables developers to extract text and metadata from documents like PDF, Word, Excel, PowerPoint, and more, simplifying text extraction tasks within .NET applications.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites set up:
- Visual Studio or any other .NET development environment installed on your machine.
- Basic knowledge of C# programming language.
- Access to GroupDocs.Parser for .NET library.

## Import Namespaces
First, make sure to import the required namespaces for GroupDocs.Parser in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Step 1: Initialize GroupDocs.Parser
To begin text extraction, create an instance of the `Parser` class, passing the path to your sample document:
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    // Continue with text extraction here
}
```
## Step 2: Extract Raw Text
Within the `using` block, use the `GetText` method with `TextOptions` to extract raw text from the document:
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    // Continue to read text from the document
}
```
## Step 3: Read Text from Document
Now, utilize the `TextReader` object to read the extracted text from the document:
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## Conclusion
By following these steps, you can effectively extract raw text from documents using GroupDocs.Parser for .NET. This tutorial provides a foundational guide to leveraging this library within your .NET applications for seamless text extraction.

## FAQ's
### What file formats does GroupDocs.Parser support?
GroupDocs.Parser supports a wide range of file formats, including PDF, Microsoft Word, Excel, PowerPoint, and more.
### Can I extract metadata along with text using GroupDocs.Parser?
Yes, GroupDocs.Parser allows extraction of both text and metadata from supported document formats.
### Is GroupDocs.Parser compatible with .NET Core?
Yes, GroupDocs.Parser is compatible with .NET Core along with the traditional .NET Framework.
### Does GroupDocs.Parser handle password-protected documents?
Yes, GroupDocs.Parser can process password-protected documents if the correct password is provided.
### Can I integrate GroupDocs.Parser into my web applications?
Certainly, GroupDocs.Parser can be seamlessly integrated into web applications developed using .NET technologies.
