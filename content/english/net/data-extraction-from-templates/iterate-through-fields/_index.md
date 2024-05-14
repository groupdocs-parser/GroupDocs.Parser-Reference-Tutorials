---
title: Iterate Through Fields
linktitle: Iterate Through Fields
second_title: GroupDocs.Parser .NET API
description: Learn how to extract structured data from documents using GroupDocs.Parser for .NET. Enhance your .NET applications with document data extraction capabilities.
type: docs
weight: 11
url: /net/data-extraction-from-templates/iterate-through-fields/
---
## Introduction
GroupDocs.Parser for .NET is a powerful library that allows developers to extract data from various document formats like PDF, Microsoft Word, Excel, and PowerPoint. This tutorial will guide you through the process of using GroupDocs.Parser to iterate through document fields and extract specific data using templates. By the end of this tutorial, you will be able to efficiently extract structured data from documents in your .NET applications.
## Prerequisites
Before we begin, ensure you have the following prerequisites set up:
- Basic knowledge of C# programming.
- Visual Studio installed on your machine.
- GroupDocs.Parser for .NET library installed and referenced in your project.

## Import Namespaces
To get started, add the necessary namespaces to your C# file:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Let's break down the process into step-by-step instructions.
## Step 1: Define Template Fields
First, define the fields you want to extract from the document using regular expressions.
```csharp
// Define a "price" field
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Define an "email" field
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Create a template with defined fields
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
In this step, we've defined two fields: one for extracting prices (identified by the dollar sign and digits) and another for extracting email addresses.
## Step 2: Parse the Document
Next, use the `Parser` class to parse the document using the defined template.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parse the document by the template
    DocumentData data = parser.ParseByTemplate(template);
    // Iterate through extracted data
    for (int i = 0; i < data.Count; i++)
    {
        // Print field name
        Console.Write(data[i].Name + ": ");
        // Check if the extracted area is text
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Here, we initialize the `Parser` with the path to your sample document and then parse the document using the defined template. We then iterate through the extracted data and print the field names along with the extracted text.
## Conclusion
In this tutorial, we've explored how to use GroupDocs.Parser for .NET to extract specific data from documents using templates. By leveraging regular expressions and templates, you can efficiently extract structured information from various document formats. Experiment with different templates and document types to suit your specific extraction needs.

## FAQ's
### Can GroupDocs.Parser extract data from scanned documents?
Yes, GroupDocs.Parser can extract text and metadata from both scanned and searchable PDF documents.
### Is GroupDocs.Parser compatible with .NET Core applications?
Yes, GroupDocs.Parser supports .NET Core along with .NET Framework.
### What document formats does GroupDocs.Parser support?
GroupDocs.Parser supports a wide range of formats including PDF, Microsoft Word, Excel, PowerPoint, and more.
### How can I handle large documents with GroupDocs.Parser?
GroupDocs.Parser provides options to extract data from specific pages or sections of large documents, ensuring efficient processing.
### Can I use GroupDocs.Parser for text extraction only?
Yes, you can extract plain text content from documents using GroupDocs.Parser without the need for complex formatting.
