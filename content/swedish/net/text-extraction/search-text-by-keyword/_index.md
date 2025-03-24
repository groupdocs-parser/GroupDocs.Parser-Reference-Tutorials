---
title: Sök text efter nyckelord
linktitle: Sök text efter nyckelord
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du söker efter text med nyckelord i dokument med GroupDocs.Parser för .NET. Extrahera effektivt relevant innehåll med lätthet.
weight: 21
url: /sv/net/text-extraction/search-text-by-keyword/
---
## Introduktion
I den här handledningen kommer vi att fördjupa oss i att använda GroupDocs.Parser för .NET för att söka text med nyckelord i dokument. GroupDocs.Parser är ett kraftfullt bibliotek som gör det möjligt för utvecklare att extrahera text, metadata och annan information från olika filformat, såsom PDF-filer, Microsoft Office-dokument och mer. Att söka efter specifika nyckelord i dessa dokument kan vara avgörande för applikationer som hanterar stora mängder textdata.
## Förutsättningar
Innan vi börjar, se till att du har följande inställning:
1. Utvecklingsmiljö: Visual Studio eller någon föredragen .NET IDE.
2.  GroupDocs.Parser för .NET: Ladda ner biblioteket från[här](https://releases.groupdocs.com/parser/net/).
3. Tillgång till exempelfiler: Förbered en exempelfil (t.ex. PDF, DOCX) för att testa nyckelordssökningsfunktionen.

## Importera namnområden
Först måste du inkludera de nödvändiga namnrymden i ditt projekt.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Steg 1: Instantiera Parser-klassen
 Börja med att skapa en instans av`Parser` klass och ange sökvägen till din exempelfil.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Sök efter ett nyckelord
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Iterera över sökresultat
    foreach (SearchResult result in searchResults)
    {
        //Skriv ut indexet och hittad text
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Steg 2: Sök efter ett nyckelord
 Inom`using` blockera, ring`Search` metod på`parser` objekt och skickar det önskade nyckelordet som ett argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Byta ut`"test"` med nyckelordet du vill söka efter i dokumentet.
## Steg 3: Iterera över sökresultat
 Iterera sedan över sökresultaten som erhållits från`Search` metod med hjälp av en`foreach` slinga.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 För varje`SearchResult` objekt`result` , kan du komma åt dess`Position` (index) och`Text` (den hittade texten).

## Slutsats
 I den här handledningen undersökte vi hur man använder GroupDocs.Parser för .NET för att enkelt söka text med nyckelord i dokument. Utnyttja`Search` metod för`Parser` klass möjliggör effektiv hämtning av relevanta textavsnitt baserat på specifika söktermer.

## FAQ's
### Är GroupDocs.Parser kompatibel med olika dokumentformat?
Ja, GroupDocs.Parser stöder ett brett utbud av filformat, inklusive PDF, DOCX, XLSX, PPTX och mer.
### Kan jag utföra avancerade textextraktionsoperationer med GroupDocs.Parser?
Absolut! Förutom textsökning, möjliggör GroupDocs.Parser extrahering av metadata, strukturerad textextraktion och mer.
### Var kan jag hitta detaljerad dokumentation för GroupDocs.Parser?
Utforska hela dokumentationen[här](https://tutorials.groupdocs.com/parser/net/).
### Hur kan jag få support eller hjälp med GroupDocs.Parser-relaterade frågor?
 Besök GroupDocs forum för support och diskussioner[här](https://forum.groupdocs.com/c/parser/17).
### Finns det en testversion tillgänglig för att utvärdera GroupDocs.Parser innan du köper?
 Ja, du kan komma åt den kostnadsfria provperioden[här](https://releases.groupdocs.com/).