---
title: Loading Specific File Formats
linktitle: Loading Specific File Formats
second_title: GroupDocs.Parser .NET API
description: Learn how to extract text from various file formats in .NET using GroupDocs.Parser. Step-by-step tutorial for efficient document processing.
type: docs
weight: 14
url: /net/document-loading/loading-specific-file-formats/
---
## Introduction
In the world of .NET development, parsing and extracting text from various file formats is a common requirement. GroupDocs.Parser for .NET offers powerful tools to simplify this task. This tutorial will guide you through using GroupDocs.Parser to load and extract text from specific file formats step by step.
## Prerequisites
Before diving into this tutorial, ensure you have the following:
- Basic knowledge of C# and .NET development.
- Visual Studio or another IDE for .NET development installed.
- GroupDocs.Parser for .NET library. You can download it from [here](https://releases.groupdocs.com/parser/net/).
- A sample file in one of the supported formats (e.g., Word, PDF, Markdown).

## Import Namespaces
Start by adding the necessary namespaces to your C# file:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```

Follow these steps to load and extract text from a specific file format:
## Step 1: Open a File Stream
First, open a stream to your sample file:
```csharp
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Proceed to next step
}
```
Replace `"YourSampleFile.docx"` with the path to your sample file.
## Step 2: Create a Parser Instance
Instantiate the `Parser` class with the opened stream and specify the file format:
```csharp
using (Parser parser = new Parser(stream, new LoadOptions(FileFormat.Docx)))
{
    // Proceed to next step
}
```
Replace `FileFormat.Docx` with the appropriate file format enumeration based on your sample file (e.g., `FileFormat.Pdf`, `FileFormat.Markup` for Markdown).
## Step 3: Check Text Extraction Support
Verify if text extraction is supported for the loaded file format:
```csharp
if (!parser.Features.Text)
{
    Console.WriteLine("Text extraction isn't supported.");
    return;
}
```
## Step 4: Extract Text from Document
Use `parser.GetText()` to obtain a `TextReader` instance and read the extracted text:
```csharp
using (TextReader reader = parser.GetText())
{
    string extractedText = reader.ReadToEnd();
    Console.WriteLine(extractedText);
}
```

## Conclusion
GroupDocs.Parser for .NET simplifies text extraction from various file formats, enabling efficient document processing in C# applications. By following this tutorial, you've learned how to load specific file formats and extract text using GroupDocs.Parser.

## FAQ's
### Is GroupDocs.Parser for .NET free to use?
GroupDocs.Parser for .NET offers both free and paid licensing options. You can explore them [here](https://purchase.groupdocs.com/buy).
### Which file formats are supported by GroupDocs.Parser for .NET?
GroupDocs.Parser supports a wide range of file formats, including Word, PDF, Excel, PowerPoint, Markdown, and more. Refer to the documentation [here](https://reference.groupdocs.com/parser/net/) for the full list.
### Can I try GroupDocs.Parser for .NET before purchasing?
Yes, you can access a free trial version [here](https://releases.groupdocs.com/).
### Where can I find support or ask questions about GroupDocs.Parser for .NET?
Visit the GroupDocs.Parser forum [here](https://forum.groupdocs.com/c/parser/17) for any queries or support needs.
### How can I obtain a temporary license for GroupDocs.Parser for .NET?
You can obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
