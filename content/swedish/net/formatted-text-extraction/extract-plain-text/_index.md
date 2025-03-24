---
title: Extrahera vanlig text
linktitle: Extrahera vanlig text
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar vanlig text från dokument med GroupDocs.Parser för .NET. Enkla steg för att integrera textextraktion i dina applikationer.
weight: 14
url: /sv/net/formatted-text-extraction/extract-plain-text/
---
## Introduktion
den här handledningen kommer vi att utforska hur man extraherar vanlig text från olika dokumentformat med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare arbeta med dokument sömlöst och extrahera text och metadata effektivt. Den här guiden leder dig genom de nödvändiga stegen för att integrera och använda det här biblioteket i dina .NET-applikationer.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1. Visual Studio: Installera Visual Studio på din utvecklingsmaskin.
2.  GroupDocs.Parser Library: Ladda ner och installera GroupDocs.Parser för .NET från[nedladdningssida](https://releases.groupdocs.com/parser/net/).
3. Exempeldokument: Förbered exempeldokument (t.ex. DOCX, PDF, TXT) för textextraktion.

## Importera namnområden
Inkludera först de nödvändiga namnrymden i ditt C#-projekt för att komma åt funktionerna i GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Steg 1: Initiera Parser
 Skapa en instans av`Parser` klass genom att ange sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // Koden för textextraktion går här
}
```
## Steg 2: Extrahera formaterad text
 Inom`using` block av`Parser` extrahera den formaterade texten med hjälp av`GetFormattedText` metod med`PlainText` läge.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // Kod för att läsa och bearbeta den extraherade texten
}
```
## Steg 3: Läs extraherad text
 Använd`TextReader` instans för att läsa och mata ut den extraherade oformaterade texten.
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## Slutsats
I den här handledningen har vi täckt grunderna för att extrahera vanlig text från dokument med GroupDocs.Parser för .NET. Genom att följa dessa steg kan du sömlöst integrera textextraktionsfunktioner i dina .NET-applikationer.

## FAQ's
### Är GroupDocs.Parser kompatibel med flera dokumentformat?
Ja, GroupDocs.Parser stöder ett brett utbud av dokumentformat inklusive DOCX, PDF, TXT och mer.
### Kan jag extrahera metadata tillsammans med text med GroupDocs.Parser?
Absolut, GroupDocs.Parser tillåter extraktion av både textinnehåll och metadata som författare, skapelsedatum, etc.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan komma åt den kostnadsfria testversionen av GroupDocs.Parser[här](https://releases.groupdocs.com/).
### Var kan jag hitta teknisk support för GroupDocs.Parser?
 För teknisk hjälp, besök GroupDocs.Parser[forum](https://forum.groupdocs.com/c/parser/17).
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 För att skaffa en tillfällig licens, besök GroupDocs.Parser[sida för tillfällig licens](https://purchase.groupdocs.com/temporary-license/).