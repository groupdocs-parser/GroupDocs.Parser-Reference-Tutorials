---
title: Working with Fields at Fixed Positions in Templates
linktitle: Working with Fields at Fixed Positions in Templates
second_title: GroupDocs.Parser .NET API
description: Learn how to extract data from documents using GroupDocs.Parser for .NET. Comprehensive tutorial with code examples.
type: docs
weight: 11
url: /net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Introduction
In this tutorial, we will explore how to work with fields at fixed positions within templates using GroupDocs.Parser for .NET. GroupDocs.Parser is a powerful document parsing library that enables developers to extract data from various document formats such as PDF, Word, Excel, and more. Specifically, we'll focus on defining and utilizing template fields to extract targeted information based on their fixed positions.
## Prerequisites
Before we begin, ensure you have the following:
- Basic understanding of C# and .NET development.
- Visual Studio installed on your system.
- GroupDocs.Parser for .NET library installed. You can download it from [here](https://releases.groupdocs.com/parser/net/).
- Sample document files for testing.

## Import Namespaces
Start by including the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Step 1: Define a Template Field
First, define a field with a fixed position within a template. This field represents the area from which data will be extracted.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Here:
- `Rectangle` specifies the position and size of the field.
- `Point(35, 135)` represents the top-left corner coordinates.
- `Size(100, 10)` defines the width and height of the field.
- `"FromCompany"` is the name assigned to this field.
## Step 2: Create a Template
Construct a template using the defined field.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
The `Template` object holds the defined fields.
## Step 3: Parse Document Using the Template
Instantiate the `Parser` class with the target document path and then parse the document using the created template.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterate through extracted data
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Here:
- `Parser` is initialized with the sample document file path.
- `ParseByTemplate` method is used to extract data based on the provided template.
- Extracted data is accessed using `DocumentData`, where each item corresponds to a defined field.

## Conclusion
In this tutorial, we covered the process of working with fields at fixed positions in templates using GroupDocs.Parser for .NET. By defining templates with specific field positions, developers can accurately extract targeted data from various document formats.

## FAQ's
### Is GroupDocs.Parser compatible with all document formats?
GroupDocs.Parser supports a wide range of file formats, including PDF, Microsoft Word, Excel, PowerPoint, and more. Refer to the [documentation](https://reference.groupdocs.com/parser/net/) for a detailed list.
### How can I obtain a temporary license for GroupDocs.Parser?
You can get a temporary license for testing purposes from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find support for GroupDocs.Parser?
For technical assistance and discussions, visit the [GroupDocs.Parser forum](https://forum.groupdocs.com/c/parser/17).
### Can I try GroupDocs.Parser before purchasing?
Yes, you can explore the library with a free trial available [here](https://releases.groupdocs.com/).
### How do I purchase a license for GroupDocs.Parser?
To buy a license, visit the [purchase page](https://purchase.groupdocs.com/buy).
