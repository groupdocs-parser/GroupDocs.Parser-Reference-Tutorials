---
title: Extract Metadata from PDF
linktitle: Extract Metadata from PDF
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 13
url: /net/pdf-processing/extract-metadata-from-pdf/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>
namespace GroupDocs.Parser.Examples.CSharp.AdvancedUsage.ExtractDataFromVariousFormats.Email
{
    using System;
    using System.Collections.Generic;
    using System.Text;
    using GroupDocs.Parser.Data;

    /// <summary>
    /// This example shows how to extract metadata from an email.
    /// </summary>
    static class ExtractMetadata
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract metadata from the email
                IEnumerable<MetadataItem> metadata = parser.GetMetadata();

                // Iterate over metadata items
                foreach (MetadataItem item in metadata)
                {
                    // Print the item name and value
                    Console.WriteLine(string.Format("{0}: {1}", item.Name, item.Value));
                }
            }
        }
    }
}

```
