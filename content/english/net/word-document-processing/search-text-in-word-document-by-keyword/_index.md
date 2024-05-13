---
title: Search Text in Word Document by Keyword
linktitle: Search Text in Word Document by Keyword
second_title: GroupDocs.Parser .NET API
description: 
type: docs
weight: 18
url: /net/word-document-processing/search-text-in-word-document-by-keyword/
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
    /// This example shows how to find a keyword in an email.
    /// </summary>
    static class SearchTextByKeyword
    {
        public static void Run()
        {
            // Create an instance of Parser class
            using (Parser parser = new Parser("Your Sample File"))
            {
                // Search a keyword:
                IEnumerable<SearchResult> sr = parser.Search("test");

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
