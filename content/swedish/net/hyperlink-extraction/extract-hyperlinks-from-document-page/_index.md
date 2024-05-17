---
title: Extrahera hyperlänkar från dokumentsidan
linktitle: Extrahera hyperlänkar från dokumentsidan
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar hyperlänkar från dokument med GroupDocs.Parser för .NET. Steg-för-steg-guide för hyperlänkextraktion i C#.
type: docs
weight: 11
url: /sv/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att extrahera hyperlänkar från dokument steg för steg. GroupDocs.Parser är ett kraftfullt bibliotek som gör det möjligt för utvecklare att analysera olika dokumentformat och extrahera text, metadata och andra element.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio: Installera Visual Studio på din utvecklingsmaskin.
-  GroupDocs.Parser Library: Ladda ner och referera till GroupDocs.Parser-biblioteket. Du kan få det från[här](https://releases.groupdocs.com/parser/net/).
- Exempeldokument: Förbered ett exempeldokument (t.ex. DOCX, PDF) som innehåller hyperlänkar för testning.

## Importera namnområden
Inkludera först de nödvändiga namnrymden för att använda GroupDocs.Parser-funktioner:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa Parser-instans
 Instantiera`Parser` klass med sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Koden kommer här...
}
```
## Steg 2: Kontrollera Hyperlink Extraction Support
Se till att dokumentet stöder extraktion av hyperlänkar innan du fortsätter.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Steg 3: Hämta dokumentinformation
Få grundläggande information om dokumentet och kontrollera om det innehåller sidor.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Steg 4: Iterera över dokumentsidor
Iterera genom varje sida i dokumentet.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extrahera hyperlänkar från den aktuella sidan
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iterera över extraherade hyperlänkar
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Tom rad för läsbarhet
    }
}
```

## Slutsats
I den här handledningen har vi täckt grunderna för att använda GroupDocs.Parser för .NET för att extrahera hyperlänkar från dokument. Du lärde dig hur du initierar tolken, söker efter stöd för hyperlänkar, hämtar dokumentinformation och itererar genom dokumentsidor för att extrahera hyperlänkar effektivt.

## FAQ's
### Kan jag extrahera hyperlänkar från olika dokumentformat?
Ja, GroupDocs.Parser stöder olika format som DOCX, PDF, PPTX, etc., för extraktion av hyperlänkar.
### Är GroupDocs.Parser lätt att integrera i befintliga .NET-applikationer?
Absolut, GroupDocs.Parser är designad för att vara enkel och kan enkelt integreras i dina .NET-projekt.
### Kan jag extrahera annan metadata tillsammans med hyperlänkar med GroupDocs.Parser?
Ja, förutom hyperlänkar kan du extrahera text, bilder och metadata från dokument med detta bibliotek.
### Hanterar GroupDocs.Parser krypterade eller lösenordsskyddade dokument?
GroupDocs.Parser kan analysera lösenordsskyddade dokument om lösenordet tillhandahålls.
### Finns det en testversion att testa innan du köper?
 Ja, du kan ladda ner en gratis testversion[här](https://releases.groupdocs.com/).