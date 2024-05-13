---
title: Working with Barcodes in Templates
linktitle: Working with Barcodes in Templates
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 10
url: /net/document-template-processing/working-with-barcodes-in-templates/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>
namespace GroupDocs.Parser.Examples.CSharp.AdvancedUsage.WorkingWithTemplates.TemplateBarcodes
{
    using GroupDocs.Parser.Data;
    using GroupDocs.Parser.Templates;
    using System;

    /// <summary>
    /// This example shows how to define a template barcode field.
    /// </summary>
    static class WorkingWithBarcodes
    {
        public static void Run()
        {
            // Define a barcode field
            TemplateBarcode barcode = new TemplateBarcode(
                new Rectangle(new Point(590, 80), new Size(150, 150)),
                "QR");

            // Create a template
            Template template = new Template(new TemplateItem[] { barcode });

            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Parse the document by the template
                DocumentData data = parser.ParseByTemplate(template);

                // Print all extracted data
                for (int i = 0; i < data.Count; i++)
                {
                    Console.Write(data[i].Name + ": ");
                    PageBarcodeArea area = data[i].PageArea as PageBarcodeArea;
                    Console.WriteLine(area == null ? "Not a template barcode field" : area.Value);
                }
            }
        }
    }
}

```
