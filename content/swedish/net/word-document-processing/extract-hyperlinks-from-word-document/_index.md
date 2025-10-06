---
title: Extrahera hyperlänkar från Word-dokument
linktitle: Extrahera hyperlänkar från Word-dokument
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar hyperlänkar från Word-dokument med GroupDocs.Parser för .NET. Steg-för-steg guide med kodexempel.
weight: 10
url: /sv/net/word-document-processing/extract-hyperlinks-from-word-document/
type: docs
---
# Extrahera hyperlänkar från Word-dokument

## Introduktion
GroupDocs.Parser för .NET är ett kraftfullt verktyg som låter utvecklare extrahera strukturerad text och metadata från olika dokumentformat som Word, Excel, PowerPoint, PDF och mer. Ett vanligt krav vid dokumentbehandling är att extrahera hyperlänkar från Word-dokument programmatiskt. Denna handledning guidar dig genom processen att använda GroupDocs.Parser för att extrahera hyperlänkar från ett Word-dokument steg för steg.
## Förutsättningar
Innan du börjar, se till att du har följande förutsättningar:
- Grundläggande kunskaper i C# och .NET framework.
- Visual Studio installerat på din dator.
-  GroupDocs.Parser för .NET-bibliotek. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
## Importera namnområden
Börja med att importera de nödvändiga namnrymden i ditt C#-projekt för att använda GroupDocs.Parser-biblioteket.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Xml;
using GroupDocs.Parser.Data;
```
Följ dessa steg för att extrahera hyperlänkar från ett Word-dokument med GroupDocs.Parser för .NET:
## Steg 1: Skapa en instans av Parser Class
 Initiera en instans av`Parser` klass med sökvägen till ditt Word-dokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Koden för att extrahera hyperlänkar kommer hit
}
```
## Steg 2: Hämta Reader Object för dokument XML-representation
 Inuti`using` blockera, skaffa`XmlReader` objekt från parsern för att komma åt den strukturerade XML-representationen av dokumentet.
```csharp
using (XmlReader reader = parser.GetStructure())
{
    // Koden för att extrahera hyperlänkar kommer hit
}
```
## Steg 3: Iterera över dokumentets XML
Använd en loop för att iterera genom dokumentets XML-struktur med hjälp av`XmlReader`.
```csharp
while (reader.Read())
{
    // Koden för att extrahera hyperlänkar kommer hit
}
```
## Steg 4: Identifiera och extrahera hyperlänkar
Inom slingan, leta efter startelement som representerar hyperlänkar och extrahera länkattributet.
```csharp
if (reader.IsStartElement() && reader.Name == "hyperlink")
{
    string hyperlinkUrl = reader.GetAttribute("link");
    Console.WriteLine(hyperlinkUrl);
}
```
## Steg 5: Kompilera och kör koden
Kompilera och kör din C#-kod för att extrahera och skriva ut alla hyperlänkar som finns i det angivna Word-dokumentet.
## Slutsats
I den här handledningen har du lärt dig hur du använder GroupDocs.Parser för .NET för att extrahera hyperlänkar från ett Word-dokument programmatiskt. Genom att följa dessa steg kan du integrera den här funktionen i dina C#-applikationer sömlöst.

## FAQ's
### Kan jag använda GroupDocs.Parser för andra dokumentformat än Word?
Ja, GroupDocs.Parser stöder olika dokumentformat som Excel, PowerPoint, PDF och mer.
### Är GroupDocs.Parser lämplig för behandling av stora dokument?
Ja, GroupDocs.Parser är optimerad för att hantera stora dokument effektivt.
### Kan jag extrahera bilder eller text tillsammans med hyperlänkar med GroupDocs.Parser?
Ja, GroupDocs.Parser tillåter extrahering av bilder, text, metadata och hyperlänkar från dokument.
### Erbjuder GroupDocs.Parser stöd eller hjälp för utvecklare?
 Ja, du kan få support och hjälp från GroupDocs community forum[här](https://forum.groupdocs.com/c/parser/17).
### Finns det en testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan få tillgång till en gratis testversion[här](https://releases.groupdocs.com/).