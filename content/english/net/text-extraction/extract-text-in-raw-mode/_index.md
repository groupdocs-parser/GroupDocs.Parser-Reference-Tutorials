---
title: Extract Text in Raw Mode
linktitle: Extract Text in Raw Mode
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 19
url: /net/text-extraction/extract-text-in-raw-mode/
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
    using System.IO;
    using System.Text;
    using GroupDocs.Parser.Options;

    /// <summary>
    /// This example shows how to extract a raw text from a document.
    /// </summary>
    static class ExtractTextInRawMode
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract a raw text into the reader
                using (TextReader reader = parser.GetText(new TextOptions(true)))
                {
                    // Print a text from the document
                    // If text extraction isn't supported, a reader is null
                    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
                }
            }
        }
    }
}

```
