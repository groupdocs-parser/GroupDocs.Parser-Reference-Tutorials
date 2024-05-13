---
title: Extract Text Structure
linktitle: Extract Text Structure
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 20
url: /net/text-extraction/extract-text-structure/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>
namespace GroupDocs.Parser.Examples.CSharp.AdvancedUsage.WorkingWithText
{
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Xml;

    /// <summary>
    /// This example how to extract all the hyperlinks from a document.
    /// </summary>
    static class ExtractTextStructure
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract text structure to the XML reader
                using (XmlReader reader = parser.GetStructure())
                {
                    // Check if text structure extraction is supported
                    if (reader == null)
                    {
                        Console.WriteLine("Text structure extraction isn't supported.");
                        return;
                    }
                    // Read the XML document to search hyperlinks
                    while (reader.Read())
                    {
                        // Check if this is a start element with "hyperlink" name
                        if (reader.NodeType == XmlNodeType.Element && reader.IsStartElement() && reader.Name.ToLowerInvariant() == "hyperlink")
                        {
                            // Extract "link" attribute
                            string value = reader.GetAttribute("link");
                            if (value != null)
                            {
                                Console.WriteLine(value);
                            }
                        }
                    }
                }
            }
        }
    }
}

```
