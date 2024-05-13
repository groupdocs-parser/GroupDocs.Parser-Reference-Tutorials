---
title: Extract Text in Accurate Mode
linktitle: Extract Text in Accurate Mode
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 18
url: /net/text-extraction/extract-text-in-accurate-mode/
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

    /// <summary>
    /// This example shows how to extract a text from a document.
    /// </summary>
    static class ExtractTextInAccurateMode
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract a text into the reader
                using (TextReader reader = parser.GetText())
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
