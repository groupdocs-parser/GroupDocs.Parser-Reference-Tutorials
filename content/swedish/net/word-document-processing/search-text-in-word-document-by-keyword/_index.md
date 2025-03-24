---
title: Sök text i Word-dokument efter nyckelord
linktitle: Sök text i Word-dokument efter nyckelord
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du söker efter text i Word-dokument med GroupDocs.Parser för .NET. Extrahera specifika sökord effektivt.
weight: 18
url: /sv/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att söka efter specifik text i ett Word-dokument med C#. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare extrahera text och metadata från olika dokumentformat, inklusive Word-dokument.
## Förutsättningar
Innan du börjar, se till att du har följande förutsättningar:
1. Utvecklingsmiljö: Installera Visual Studio eller annan kompatibel IDE.
2.  GroupDocs.Parser Library: Ladda ner och installera GroupDocs.Parser för .NET-biblioteket från[hemsida](https://releases.groupdocs.com/parser/net/).
3. Exempel på Word-dokument: Förbered ett exempel på Word-dokument att använda för textsökning.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Steg 1: Skapa en instans av Parser Class
 Skapa först en instans av`Parser` klass genom att skicka sökvägen till ditt exempel på Word-dokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Koden går här
}
```
## Steg 2: Sök efter ett nyckelord
 Använd sedan`Search` metod för`Parser` klass för att söka efter ett specifikt nyckelord i dokumentet.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Byta ut`"keyword"` med texten du vill söka efter i dokumentet.
## Steg 3: Iterera över sökresultat
 Iterera över sökresultaten med hjälp av en`foreach` loop för att komma åt var och en`SearchResult` objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    //Kod för att hantera varje sökresultat
}
```
## Steg 4: Få åtkomst till information om sökresultat
 Inom slingan kan du komma åt positionen och texten för varje sökresultat med hjälp av`Position` och`Text` egenskaper hos`SearchResult` objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Detta kodavsnitt skriver ut indexet (`Position`) och den hittade texten (`Text`) för varje sökresultat till konsolen.

## Slutsats
I den här självstudien har du lärt dig hur du använder GroupDocs.Parser för .NET för att söka efter specifik text i ett Word-dokument. Detta bibliotek ger ett bekvämt sätt att extrahera och manipulera innehåll från olika dokumentformat programmatiskt.

## FAQ's
### Kan GroupDocs.Parser hantera andra dokumentformat än Word?
Ja, GroupDocs.Parser stöder ett brett utbud av format, inklusive PDF, Excel, PowerPoint och mer.
### Är GroupDocs.Parser kompatibel med .NET Core?
Ja, GroupDocs.Parser är kompatibel med både .NET Framework och .NET Core.
### Hur får jag en tillfällig licens för GroupDocs.Parser?
 Du kan begära en tillfällig licens från[GroupDocs köpsida](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta ytterligare support eller ställa frågor om GroupDocs.Parser?
 Besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) för samhällsstöd och diskussioner.
### Kan jag prova GroupDocs.Parser gratis innan jag köper?
 Ja, du kan ladda ner en gratis testversion från[GroupDocs releasesida](https://releases.groupdocs.com/).