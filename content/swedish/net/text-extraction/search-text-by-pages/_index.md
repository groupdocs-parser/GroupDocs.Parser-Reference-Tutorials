---
title: Sök text efter sidor
linktitle: Sök text efter sidor
second_title: GroupDocs.Parser .NET API
description: Lär dig att söka text på sidor med GroupDocs.Parser för .NET. Extrahera specifikt innehåll effektivt från dokument i dina .NET-applikationer.
type: docs
weight: 22
url: /sv/net/text-extraction/search-text-by-pages/
---
## Introduktion
I en värld av .NET-utveckling är det en avgörande uppgift att effektivt analysera och extrahera text från dokument. GroupDocs.Parser för .NET erbjuder kraftfulla funktioner för att arbeta med olika dokumentformat, vilket gör att utvecklare kan söka och extrahera specifikt innehåll sömlöst. Den här handledningen guidar dig genom processen att använda GroupDocs.Parser för att söka text efter sidor i dina .NET-applikationer.
## Förutsättningar
Innan du dyker in i den här handledningen, se till att du har följande förutsättningar:
- Grundläggande förståelse för C# och .NET framework
- Visual Studio installerat på ditt system
-  GroupDocs.Parser för .NET-biblioteket installerat (Ladda ner från[här](https://releases.groupdocs.com/parser/net/))
- Exempelfil(er) för att testa sökfunktionen
## Importera namnområden
Inkludera först de nödvändiga namnområdena i ditt projekt för att få tillgång till GroupDocs.Parser-funktioner:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Börja med att instansiera`Parser` klass med sökvägen till din exempelfil:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Din kod kommer hit
}
```
## Steg 2: Sök text med sidnummer
 Använd`Search` metod för att leta efter specifika nyckelord i dokumentet tillsammans med sidnummer:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## Steg 3: Kontrollera söksupport
Kontrollera om sökoperationen stöds för dokumenttypen:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## Steg 4: Iterera över sökresultat
Iterera genom sökresultaten för att hämta indexerade positioner, sidnummer och den hittade texten:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## Slutsats
I den här handledningen har vi utforskat hur man implementerar textsökning efter sidor med GroupDocs.Parser för .NET. Genom att följa dessa steg kan du effektivt integrera dokumentanalys och sökfunktioner i dina .NET-applikationer.

## FAQ's
### Är GroupDocs.Parser kompatibel med olika dokumentformat?
Ja, GroupDocs.Parser stöder ett brett utbud av dokumentformat inklusive DOCX, PDF, XLSX, PPTX och mer.
### Kan jag extrahera bilder och metadata från dokument med GroupDocs.Parser?
Absolut, GroupDocs.Parser tillåter extrahering av bilder, metadata och text från dokument.
### Var kan jag hitta detaljerad dokumentation för GroupDocs.Parser?
 Du kan komma åt dokumentationen[här](https://reference.groupdocs.com/parser/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan begära en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag få support eller hjälp med GroupDocs.Parser?
 För support och diskussioner, besök GroupDocs.Parser-forumet[här](https://forum.groupdocs.com/c/parser/17).