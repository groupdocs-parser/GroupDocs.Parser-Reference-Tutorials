---
title: Search Text in PDF by Regular Expression
linktitle: Search Text in PDF by Regular Expression
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 19
url: /net/pdf-processing/search-text-in-pdf-by-regular-expression/
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
    using GroupDocs.Parser.Options;

    /// <summary>
    /// This example shows how to search with a regular expression in an email.
    /// </summary>
    static class SearchTextByRegularExpression
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Search with a regular expression with case matching
                IEnumerable<SearchResult> sr = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
                // Iterate over search results
                foreach (SearchResult s in sr)
                {
                    // Print an index and found text:
                    Console.WriteLine(string.Format("At {0}: {1}", s.Position, s.Text));
                }
            }
        }
    }
}

```
