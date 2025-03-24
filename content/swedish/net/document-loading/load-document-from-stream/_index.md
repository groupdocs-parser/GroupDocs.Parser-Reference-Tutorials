---
title: Ladda dokument från Stream
linktitle: Ladda dokument från Stream
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar text från olika dokumentformat i .NET med GroupDocs.Parser. Steg-för-steg guide med kodexempel.
weight: 12
url: /sv/net/document-loading/load-document-from-stream/
---

# Ladda dokument från Stream

## Introduktion
När det gäller dokumentbehandling i .NET-applikationer är det ett vanligt krav att extrahera text från olika filformat. GroupDocs.Parser för .NET erbjuder en kraftfull lösning för att sömlöst analysera och extrahera text från en mängd olika dokument. Denna handledning guidar dig genom processen att använda GroupDocs.Parser för att extrahera text från dokument steg för steg.
## Förutsättningar
Innan du börjar använda GroupDocs.Parser för .NET, se till att du har följande inställningar:
- Utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklingsmiljö.
-  GroupDocs.Parser for .NET-paket: Ladda ner och installera GroupDocs.Parser for .NET-biblioteket från[här](https://releases.groupdocs.com/parser/net/).
- Dokumentexempel: Ha exempeldokument redo för textextraktion.
## Importera namnområden
Börja med att importera de nödvändiga namnområdena till ditt .NET-projekt för att komma åt GroupDocs.Parser-funktioner.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Följande steg visar hur man extraherar text från ett dokument med GroupDocs.Parser från en ström.
## Steg 1: Ladda dokument från Stream
```csharp
// Skapa strömmen
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Skapa en instans av Parser-klassen med strömmen
    using (Parser parser = new Parser(stream))
    {
        // Extrahera text i läsaren
        using (TextReader reader = parser.GetText())
        {
            // Skriv ut text från dokumentet
            // Om textextraktion inte stöds blir läsaren null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
I det här exemplet:
- Vi öppnar en filström för dokumentfilen (`YourSampleFile.docx`).
-  Initiera a`Parser` instans med strömmen.
-  Använda sig av`parser.GetText()` att hämta en`TextReader` som innehåller den extraherade texten.
- Skriv ut den extraherade texten eller ett meddelande om textextraktion inte stöds för dokumentformatet.
## Slutsats
GroupDocs.Parser för .NET förenklar textextraktion från olika dokumentformat, vilket gör det möjligt för utvecklare att effektivt bearbeta och använda textinnehåll i sina applikationer. Genom att följa stegen som beskrivs i den här handledningen kan du sömlöst integrera funktioner för extrahering av dokumenttext i dina .NET-projekt.

## FAQ's
### Vilka dokumentformat stöds av GroupDocs.Parser för .NET?
GroupDocs.Parser stöder ett brett utbud av dokumentformat inklusive DOCX, PDF, XLSX, PPTX, EPUB och mer.
### Kan GroupDocs.Parser extrahera bilder eller metadata från dokument?
Ja, GroupDocs.Parser kan extrahera bilder, metadata och text från olika dokumenttyper.
### Är GroupDocs.Parser kompatibel med .NET Core-applikationer?
Ja, GroupDocs.Parser är kompatibel med både .NET Framework och .NET Core-applikationer.
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta mer support eller dokumentation för GroupDocs.Parser?
 För ytterligare support, besök[GroupDocs.Parser Forum](https://forum.groupdocs.com/c/parser/17) eller hänvisa till[dokumentation](https://tutorials.groupdocs.com/parser/net/).
