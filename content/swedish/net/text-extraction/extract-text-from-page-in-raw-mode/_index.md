---
title: Extrahera text från sidan i råläge
linktitle: Extrahera text från sidan i råläge
second_title: GroupDocs.Parser .NET API
description: Lär dig effektiv textextraktion från dokumentsidor med Groupdocs.Parser för .NET i den här omfattande självstudien.
weight: 17
url: /sv/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## Introduktion
I den här handledningen kommer du att lära dig hur du använder Groupdocs.Parser för .NET för att extrahera text från dokumentsidor i råläge. Detta bibliotek tillhandahåller effektiva verktyg för att analysera och extrahera innehåll från olika filformat, vilket gör det möjligt för utvecklare att införliva dokumenttextextraktion i sina .NET-applikationer.
## Förutsättningar
Innan du börjar, se till att du har följande förutsättningar:
- Grundläggande kunskaper i C# och .NET programmering
- Visual Studio installerat på din dator
- Tillgång till Groupdocs.Parser för .NET-bibliotek
- Exempel på dokumentfil för testning

## Importera namnområden
Börja med att inkludera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Initiera Parser
 Skapa först en instans av`Parser` klass genom att ange sökvägen till din exempeldokumentfil.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Din kod här
}
```
## Steg 2: Hämta dokumentinformation
 Hämta information om dokumentet med hjälp av`GetDocumentInfo()` metod.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Steg 3: Iterera över sidor och extrahera text
Iterera genom varje sida i dokumentet och extrahera textinnehåll.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Extrahera text från sidan
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Slutsats
Du har nu lärt dig hur du använder Groupdocs.Parser för .NET för att extrahera text från dokumentsidor i råläge. Detta kan vara en kraftfull funktion för applikationer som behöver analysera eller bearbeta textinnehåll från olika filformat.

## FAQ's
### Är Groupdocs.Parser för .NET kompatibel med alla filformat?
Groupdocs.Parser stöder ett brett utbud av filformat inklusive PDF, DOCX, XLSX, PPTX, EPUB och mer.
### Kan jag extrahera metadata tillsammans med text med det här biblioteket?
Ja, Groupdocs.Parser låter dig extrahera både text och metadata från dokument.
### Finns det en testversion tillgänglig för testning?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för Groupdocs.Parser?
 För teknisk hjälp, besök[Groupdocs.Parser forum](https://forum.groupdocs.com/c/parser/17).
### Var kan jag köpa en licens för Groupdocs.Parser för .NET?
 Du kan köpa en licens[här](https://purchase.groupdocs.com/buy).