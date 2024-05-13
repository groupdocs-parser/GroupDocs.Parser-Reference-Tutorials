---
title: Extract Text from PDF
linktitle: Extract Text from PDF
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 14
url: /net/pdf-processing/extract-text-from-pdf/
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
    using System.IO;
    using System.Text;
    using GroupDocs.Parser.Data;

    /// <summary>
    /// This example shows how to extract a text from an email.
    /// </summary>
    static class ExtractText
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract a text into the reader
                using (TextReader reader = parser.GetText())
                {
                    // Print a text from the email
                    Console.WriteLine(reader.ReadToEnd());
                }
            }
        }
    }
}

```
