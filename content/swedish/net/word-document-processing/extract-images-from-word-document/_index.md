---
title: Extrahera bilder från Word-dokument
linktitle: Extrahera bilder från Word-dokument
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar bilder från ett Word-dokument med GroupDocs.Parser för .NET. Den här handledningen ger steg-för-steg-vägledning för att integrera bild i ditt .NET.
type: docs
weight: 11
url: /sv/net/word-document-processing/extract-images-from-word-document/
---
## Introduktion
I den här handledningen kommer du att lära dig hur du extraherar bilder från ett Word-dokument med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt .NET-bibliotek som låter dig analysera och extrahera text, metadata, bilder och mer från olika dokumentformat inklusive Word (DOCX).
## Förutsättningar
Innan du börjar, se till att du har ställt in följande förutsättningar:
- Visual Studio installerat på din dator.
- Grundläggande kunskaper i C#-programmering.
- GroupDocs.Parser för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
## Importera namnområden
Först måste du importera de nödvändiga namnrymden i ditt C#-projekt för att använda GroupDocs.Parser-funktioner:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Låt oss nu dela upp processen att extrahera bilder från ett Word-dokument i enkla steg:
## Steg 1: Skapa en instans av Parser Class
 Du börjar med att skapa en instans av`Parser`klass, vilket ger sökvägen till ditt Word-dokument som indata.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Koden för bildextraktion går här
}
```
## Steg 2: Extrahera bilder från Word-dokumentet
 Använd sedan`GetImages()` metod för`Parser` objekt för att extrahera bilder från dokumentet.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Steg 3: Definiera bildsparalternativ
Ange alternativen för att spara de extraherade bilderna. Du kan till exempel välja bildformat (t.ex. PNG) och konfigurera andra inställningar.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Steg 4: Iterera över extraherade bilder och spara
Iterera genom varje extraherad bild och spara den i en fil med de angivna alternativen.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Spara bilden i en PNG-fil
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Slutsats
I den här handledningen har du lärt dig hur du extraherar bilder från ett Word-dokument med GroupDocs.Parser för .NET. Genom att följa dessa steg kan du enkelt integrera funktioner för dokumentanalys och bildextrahering i dina .NET-applikationer.

## FAQ's
### Kan GroupDocs.Parser extrahera bilder från andra dokumentformat än Word?
Ja, GroupDocs.Parser stöder olika dokumentformat inklusive PDF, PowerPoint, Excel och mer.
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan få en tillfällig licens för teständamål från[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta mer dokumentation om GroupDocs.Parser för .NET?
 Du kan hänvisa till den fullständiga dokumentationen[här](https://reference.groupdocs.com/parser/net/).
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan utforska funktionerna i GroupDocs.Parser med en gratis provperiod tillgänglig[här](https://releases.groupdocs.com/).
### Hur kan jag få support eller ställa frågor relaterade till GroupDocs.Parser?
 Du kan skicka dina frågor på[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).