---
title: Extrahera bilder från dokument
linktitle: Extrahera bilder från dokument
second_title: GroupDocs.Parser .NET API
description: Extrahera bilder från dokument utan ansträngning med GroupDocs.Parser för .NET. Dina dokumentbearbetningsmöjligheter och effektivisera bildextraheringsuppgifterna effektivt.
weight: 11
url: /sv/net/image-extraction/extract-images-from-document/
type: docs
---
# Extrahera bilder från dokument

## Introduktion
I den här handledningen kommer vi att utforska hur man extraherar bilder från dokument med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt bibliotek som gör det möjligt för utvecklare att extrahera text, metadata, bilder och mer från olika dokumentformat.
## Förutsättningar
Innan du börjar, se till att du har ställt in följande förutsättningar:
- Visual Studio: Installera Visual Studio på din dator.
-  GroupDocs.Parser för .NET: Ladda ner och installera GroupDocs.Parser från[nedladdningssida](https://releases.groupdocs.com/parser/net/).
- Exempeldokument: Förbered ett exempeldokument (PDF, DOCX, etc.) från vilket du vill extrahera bilder.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Steg 1: Skapa en instans av Parser-klassen
 Skapa först en instans av`Parser` klass genom att ange sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Din kod kommer hit
}
```
 Byta ut`"YourSampleFile.pdf"` med sökvägen till din dokumentfil.
## Steg 2: Extrahera bilder från dokumentet
 Extrahera sedan bilder från dokumentet med hjälp av`GetImages()` metod.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 De`GetImages()` metod returnerar en samling av`PageImageArea` objekt som representerar bilder som finns i dokumentet.
## Steg 3: Kontrollera stöd för bildextraktion
Innan du itererar över bilderna, kontrollera om bildextrahering stöds för dokumentet.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Detta steg säkerställer att dokumentet innehåller extraherbara bilder.
## Steg 4: Iterera över extraherade bilder
Iterera nu över de extraherade bilderna för att få tillgång till detaljerad information om varje bild, såsom sidindex, rektangelkoordinater och bildtyp.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Denna loop skriver ut information om varje extraherad bild, inklusive dess plats och typ.

## Slutsats
I den här handledningen lärde vi oss hur man använder GroupDocs.Parser för .NET för att extrahera bilder från dokument programmatiskt. Genom att följa dessa steg kan du integrera funktioner för extrahering av dokumentbilder i dina .NET-applikationer sömlöst.

## FAQ's
### Kan GroupDocs.Parser extrahera bilder från alla dokumentformat?
GroupDocs.Parser stöder extrahering av bilder från olika format, inklusive PDF, DOCX, XLSX och mer.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan få tillgång till en gratis provversion av GroupDocs.Parser från[hemsida](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Parser?
 Detaljerad dokumentation för GroupDocs.Parser finns[här](https://tutorials.groupdocs.com/parser/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan få en tillfällig licens från[sida för tillfällig licens](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag få support för GroupDocs.Parser?
 För teknisk support och hjälp, besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).