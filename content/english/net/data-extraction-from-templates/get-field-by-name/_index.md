---
title: Get Field by Name
linktitle: Get Field by Name
second_title: GroupDocs.Parser .NET API
description: Learn how to extract specific data fields from documents using GroupDocs.Parser for .NET. Step-by-step guide with code examples.
weight: 10
url: /net/data-extraction-from-templates/get-field-by-name/
---

# Get Field by Name

## Introduction
In this tutorial, we will explore how to leverage GroupDocs.Parser for .NET to extract specific data fields like prices and emails from documents. This powerful library simplifies document parsing tasks, making it ideal for various data extraction needs.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites:
- Visual Studio installed on your system.
- Basic knowledge of C# programming.
- Download and install GroupDocs.Parser for .NET from [this link](https://releases.groupdocs.com/parser/net/).

## Import Namespaces
Begin by importing the necessary namespaces into your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Step 1: Define Template Fields
First, we'll define the template fields for extracting data. In this example, we'll create fields to capture prices and emails.
```csharp
// Define a "price" field
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Define an "email" field
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Create a template
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
## Step 2: Parse Document Using Template
Next, we'll parse a document using the defined template.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parse the document by the template
    DocumentData data = parser.ParseByTemplate(template);
    // Print prices
    Console.WriteLine("Prices:");
    foreach (FieldData field in data.GetFieldsByName("Price"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
    // Print emails
    Console.WriteLine("Emails:");
    foreach (FieldData field in data.GetFieldsByName("Email"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusion
In this tutorial, we learned how to use GroupDocs.Parser for .NET to extract specific data fields from documents. By defining templates and utilizing the parsing capabilities of the library, developers can efficiently retrieve structured data like prices and emails from various document formats.

## FAQ's
### Can I parse different types of documents with GroupDocs.Parser for .NET?
Yes, GroupDocs.Parser supports parsing various document formats such as PDF, DOCX, PPTX, and more.
### Is GroupDocs.Parser suitable for large-scale document processing?
Absolutely, GroupDocs.Parser is optimized for performance and can handle large volumes of documents efficiently.
### How can I integrate GroupDocs.Parser into my .NET application?
You can easily integrate GroupDocs.Parser by referencing the library in your Visual Studio project and importing the required namespaces.
### Does GroupDocs.Parser provide support for extracting images or metadata?
Yes, GroupDocs.Parser offers APIs to extract images, text, and metadata from documents.
### Is there a community forum for GroupDocs.Parser users?
Yes, you can seek help and engage with other users on the GroupDocs.Parser forum [here](https://forum.groupdocs.com/c/parser/17).
