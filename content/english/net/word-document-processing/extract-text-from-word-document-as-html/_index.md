---
title: Extract Text from Word Document as HTML
linktitle: Extract Text from Word Document as HTML
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 16
url: /net/word-document-processing/extract-text-from-word-document-as-html/
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
    using GroupDocs.Parser.Options;

    /// <summary>
    /// This example shows how to extract a text from an email as HTML.
    /// </summary>
    static class ExtractTextAsHtml
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Extract a formatted text into the reader
                using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
                {
                    // Print a formatted text from the email
                    Console.WriteLine(reader.ReadToEnd());
                }
            }
        }
    }
}

```
