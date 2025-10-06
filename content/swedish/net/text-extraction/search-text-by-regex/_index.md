---
title: Sök text med reguljärt uttryck (regex)
linktitle: Sök text med reguljärt uttryck (regex)
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du söker efter text med reguljära uttryck i dokument med GroupDocs.Parser för .NET. Extrahera specifikt innehåll utan ansträngning.
weight: 23
url: /sv/net/text-extraction/search-text-by-regex/
type: docs
---
# Sök text med reguljärt uttryck (regex)

## Introduktion
I den här handledningen kommer vi att fördjupa oss i att använda GroupDocs.Parser för .NET för att söka text med reguljärt uttryck (Regex) i dokument. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare extrahera text och metadata från olika filformat som PDF, DOCX, XLSX och mer. Att söka efter text med reguljära uttryck är särskilt användbart för att effektivt hitta mönster eller specifikt innehåll i dokument.
## Förutsättningar
Innan du dyker in i den här handledningen, se till att du har följande:
1. Visual Studio: Installera Visual Studio IDE för .NET-utveckling.
2.  GroupDocs.Parser för .NET: Ladda ner och installera GroupDocs.Parser för .NET från[här](https://releases.groupdocs.com/parser/net/).
3. Exempelfil: Förbered ett exempeldokument (PDF, DOCX, etc.) för att testa sökfunktionen.

## Importera namnområden
Börja först med att inkludera de nödvändiga namnrymden i din C#-kod:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Instantiera`Parser` klass genom att ange sökvägen till din exempelfil:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Koden går här
}
```
 Byta ut`"YourSampleFile.pdf"` med sökvägen till din faktiska fil.
## Steg 2: Sök med reguljära uttryck
Definiera och utför sökningen med ett reguljärt uttrycksmönster. För att till exempel hitta numeriska sekvenser (t.ex. heltal) i dokumentet:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 I det här exemplet,`[0-9]+` är ett reguljärt uttrycksmönster som matchar en eller flera siffror.
## Steg 3: Kontrollera söksupport
Kontrollera om sökoperationen stöds för dokumenttypen:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Steg 4: Iterera över sökresultat
Gå igenom sökresultaten och bearbeta varje matchning:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Denna loop kommer att skriva ut positionen och den matchande texten som finns i dokumentet.

## Slutsats
Sammanfattningsvis, att utnyttja GroupDocs.Parser för .NET möjliggör effektiv textsökning med hjälp av reguljära uttryck i olika dokumentformat. Genom att följa den här guiden kan utvecklare sömlöst integrera dokumentanalys och regex-baserad textextraktion i sina .NET-applikationer.

## FAQ's
### Kan GroupDocs.Parser söka i krypterade dokument?
Nej, GroupDocs.Parser kan inte söka i krypterade eller lösenordsskyddade dokument.
### Stöder GroupDocs.Parser OCR (Optical Character Recognition)?
Nej, GroupDocs.Parser utför inte OCR. Den förlitar sig på textextraktion från dokumentets interna struktur.
### Kan jag söka efter komplexa mönster med reguljära uttryck?
Ja, GroupDocs.Parser stöder fullfjädrade reguljära uttryck, vilket möjliggör komplex mönstermatchning i dokument.
### Vilka dokumentformat stöds för textextraktion?
GroupDocs.Parser stöder ett brett utbud av format, inklusive PDF, DOCX, XLSX, PPTX och mer.
### Är GroupDocs.Parser kompatibel med .NET Core?
Ja, GroupDocs.Parser är kompatibel med .NET Core för plattformsoberoende utveckling.