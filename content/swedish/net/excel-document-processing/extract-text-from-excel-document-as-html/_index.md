---
title: Extrahera text från Excel-dokument som HTML
linktitle: Extrahera text från Excel-dokument som HTML
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar text från Excel-dokument och konverterar den till HTML med GroupDocs.Parser för .NET.
weight: 13
url: /sv/net/excel-document-processing/extract-text-from-excel-document-as-html/
---

# Extrahera text från Excel-dokument som HTML

## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att extrahera text från ett Excel-dokument och konvertera det till HTML-format. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare arbeta med olika dokumentformat, extrahera text och metadata effektivt.
## Förutsättningar
Innan vi börjar, se till att du har följande inställning:
- Visual Studio installerat på ditt system.
- Grundläggande förståelse för C#-programmering.
-  GroupDocs.Parser-bibliotek för .NET. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
## Importera namnområden
Börja med att inkludera de nödvändiga namnrymden i ditt C#-projekt för att komma åt GroupDocs.Parser-funktionerna.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Först, instansiera`Parser` klass genom att ange sökvägen till ditt Excel-dokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Ytterligare kod kommer här
}
```
 Byta ut`"YourSampleFile.xlsx"` med sökvägen till din Excel-fil.
## Steg 2: Extrahera text som HTML
 Inom`using` block av`Parser` använd till exempel`GetFormattedText` metod för att extrahera formaterad text i HTML-läge.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Ytterligare kod kommer här
    }
}
```
## Steg 3: Läs och skriv ut extraherad HTML-text
 Läs sedan den extraherade HTML-texten från`TextReader` och skriv ut den på konsolen.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
När den har körts extraherar den här koden texten från Excel-dokumentet och visar den som HTML-format i konsolen.
## Slutsats
I den här handledningen lärde vi oss hur man använder GroupDocs.Parser för .NET för att extrahera text från ett Excel-dokument och konvertera det till HTML-format. Detta bibliotek ger ett enkelt sätt att arbeta med olika dokumentformat, vilket gör det möjligt för utvecklare att effektivt hantera textextraktionsuppgifter i sina applikationer.

## FAQ's
### Kan GroupDocs.Parser hantera andra dokumentformat än Excel?
Ja, GroupDocs.Parser stöder ett brett utbud av filformat inklusive PDF, Word, PowerPoint och mer.
### Är GroupDocs.Parser kompatibel med .NET Core?
Ja, GroupDocs.Parser är kompatibel med både .NET Framework och .NET Core.
### Behåller GroupDocs.Parser formateringen under textextraktion?
Ja, GroupDocs.Parser kan bevara formatering som typsnitt, stilar och layout under textextraktion.
### Kan jag extrahera metadata från dokument med GroupDocs.Parser?
Ja, GroupDocs.Parser tillåter extrahering av metadata som författare, skapelsedatum och mer från dokumenttyper som stöds.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).