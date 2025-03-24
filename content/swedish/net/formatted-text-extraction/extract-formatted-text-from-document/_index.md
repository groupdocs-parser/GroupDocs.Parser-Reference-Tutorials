---
title: Extrahera formaterad text från dokument
linktitle: Extrahera formaterad text från dokument
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar formaterad text från dokument med GroupDocs.Parser för .NET. Enkel och effektiv textextraktion för dina applikationer.
weight: 10
url: /sv/net/formatted-text-extraction/extract-formatted-text-from-document/
---

# Extrahera formaterad text från dokument

## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att extrahera formaterad text från olika typer av dokument. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare arbeta med dokument på ett förenklat och effektivt sätt. I slutet av den här guiden kommer du att sömlöst kunna integrera textextraktionsfunktioner i dina .NET-applikationer.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio: Se till att du har Visual Studio installerat på ditt system.
-  GroupDocs.Parser för .NET: Ladda ner och installera GroupDocs.Parser-biblioteket från[här](https://releases.groupdocs.com/parser/net/).
- Dokumentexempel: Förbered exempeldokument (t.ex. PDF, DOCX) för textextraktion.
## Importera namnområden
Inkludera först de nödvändiga namnrymden i din C#-kod:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Börja med att initiera a`Parser` objekt med sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Textextraktionskoden går här
}
```
 Byta ut`"YourSampleFile.pdf"` med sökvägen till din dokumentfil.

## Steg 2: Extrahera formaterad text
 Inom`using` blockera, använd`GetFormattedText` metod för att extrahera formaterad text från dokumentet. Ange önskat utdataformat (t.ex. HTML) med`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extrahera formaterad text i läsaren
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Kontrollera om extraktion stöds
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Läs och visa den extraherade texten
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Slutsats
Grattis! Du har lärt dig hur du extraherar formaterad text från dokument med GroupDocs.Parser för .NET. Detta mångsidiga bibliotek öppnar möjligheter för textbearbetning och analys inom dina applikationer.

## FAQ's
### F: Kan GroupDocs.Parser extrahera text från lösenordsskyddade dokument?
S: Ja, GroupDocs.Parser stöder extrahering av text från lösenordsskyddade dokument.
### F: Vilka dokumentformat stöds av GroupDocs.Parser?
S: GroupDocs.Parser stöder ett brett utbud av format inklusive PDF, DOCX, XLSX, PPTX och mer.
### F: Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 S: Du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).
### F: Ger GroupDocs.Parser stöd för att extrahera bilder från dokument?
S: Ja, GroupDocs.Parser stöder bildextraktion tillsammans med textextraktion.
### F: Var kan jag hitta ytterligare support eller ställa frågor om GroupDocs.Parser?
 A: Besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17)för stöd och diskussioner.