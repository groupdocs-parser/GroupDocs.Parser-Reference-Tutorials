---
title: Working with Fields at Linked Positions in Templates
linktitle: Working with Fields at Linked Positions in Templates
second_title: GroupDocs.Parser .NET API
description: Learn how to extract data efficiently from documents using GroupDocs.Parser for .NET. Step-by-step tutorial with code examples.
weight: 12
url: /net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## Introduction
GroupDocs.Parser for .NET is a robust library designed to facilitate document parsing and data extraction tasks. It supports a wide range of file formats, including PDF, DOCX, XLSX, and more. One of its key features is template-based data extraction, which allows you to define fields within a document and extract specific data based on these predefined templates.
## Prerequisites
Before we begin, ensure you have the following:
- Basic understanding of C# programming
- Visual Studio installed on your system
- GroupDocs.Parser for .NET library (download from [here](https://releases.groupdocs.com/parser/net/))
- Sample document files to work with

## Importing Namespaces
Start by including the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Step 1: Define Template Fields
First, define the template fields using regular expressions and linked positions:
```csharp
// Define a field with a regular expression
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Define a linked field with specific position settings
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Step 2: Create a Template
Next, create a template containing the defined fields:
```csharp
// Create a template with the defined fields
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Step 3: Parse Document with Template
Now, initialize the `Parser` class and parse the document using the template:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parse the document by the template
    DocumentData data = parser.ParseByTemplate(template);
    // Iterate through extracted data and print results
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusion
GroupDocs.Parser for .NET simplifies the process of extracting structured data from documents using templates. By defining fields and applying templates, you can efficiently extract relevant information, enhancing automation and productivity in document processing tasks.

## FAQ's
### Can GroupDocs.Parser extract data from encrypted PDF files?
Yes, GroupDocs.Parser supports parsing encrypted PDF files by providing the password during parsing.
### Which file formats are supported for template-based extraction?
GroupDocs.Parser supports a wide range of file formats including PDF, DOCX, XLSX, PPTX, TXT, and more.
### Is there a trial version available for GroupDocs.Parser?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### Can I use GroupDocs.Parser for batch processing of documents?
Yes, GroupDocs.Parser allows batch processing to parse multiple documents concurrently.
### Where can I get technical support for GroupDocs.Parser?
You can seek technical support and engage with the community at [GroupDocs forum](https://forum.groupdocs.com/c/parser/17).
