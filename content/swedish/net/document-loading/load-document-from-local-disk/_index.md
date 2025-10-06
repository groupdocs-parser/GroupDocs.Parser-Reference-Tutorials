---
title: Ladda dokument från lokal disk
linktitle: Ladda dokument från lokal disk
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar text från olika dokumentformat med GroupDocs.Parser för .NET. Enkel och effektiv textextrahering med C#.
weight: 11
url: /sv/net/document-loading/load-document-from-local-disk/
type: docs
---
# Ladda dokument från lokal disk

## Introduktion
I den här handledningen kommer vi att utforska hur man använder GroupDocs.Parser för .NET för att extrahera text från dokument. GroupDocs.Parser är ett kraftfullt bibliotek som tillåter utvecklare att analysera olika dokumentformat och extrahera textinnehåll programmatiskt. Vi kommer att täcka de nödvändiga stegen för att komma igång med textextraktion med det här biblioteket.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar installerade:
- Visual Studio installerat på ditt system.
- Grundläggande kunskaper i programmeringsspråket C#.
-  GroupDocs.Parser för .NET-biblioteket installerat (nedladdning[här](https://releases.groupdocs.com/parser/net/)).

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Steg 1: Ladda dokument från lokal disk
 Börja med att ladda ett dokument från din lokala disk. Byta ut`"Your Sample File"` med sökvägen till ditt måldokument.
```csharp
// Ställ in filsökvägen
string filePath = "Your Sample File";
// Skapa en instans av Parser-klassen med filsökvägen
using (Parser parser = new Parser(filePath))
{
    // Extrahera text i läsaren
    using (TextReader reader = parser.GetText())
    {
        //Skriv ut den extraherade texten från dokumentet
        // Om textextraktion inte stöds blir läsaren null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Förklaring av steg
1. Ställa in filsökväg: Börja med att ange sökvägen till dokumentet du vill extrahera text från (`filePath` variabel).
2.  Skapa parserinstans: Instantiera`Parser` klass genom att passera`filePath`.
3.  Extrahera text: Använd`GetText()` metod för`Parser` exempel för att få en`TextReader` objekt som innehåller den extraherade texten från dokumentet.
4.  Läsa extraherad text: Använd`ReadToEnd()` metod för`TextReader` för att hämta hela textinnehållet som extraherats från dokumentet.
5.  Hantera format som inte stöds: Om dokumentformatet inte stöder textextraktion,`reader` objektet kommer att vara`null`, och du kan hantera det här scenariot därefter.

## Slutsats
den här handledningen har vi täckt de första stegen för att extrahera text från ett dokument med GroupDocs.Parser för .NET. Detta bibliotek erbjuder omfattande funktioner för dokumentanalys, vilket gör det möjligt för utvecklare att effektivt arbeta med olika filformat i sina applikationer.

## FAQ's
### Är GroupDocs.Parser kompatibel med alla dokumentformat?
GroupDocs.Parser stöder ett brett utbud av format inklusive PDF, Microsoft Office-dokument (Word, Excel, PowerPoint) och mer.
### Kan jag extrahera metadata tillsammans med text med GroupDocs.Parser?
Ja, GroupDocs.Parser tillåter extrahering av både textinnehåll och metadata från dokumentformat som stöds.
### Var kan jag hitta fler resurser och support för GroupDocs.Parser?
 Besök[GroupDocs.Parser-dokumentation](https://tutorials.groupdocs.com/parser/net/) för detaljerad API-referens och utforska[GroupDocs forum](https://forum.groupdocs.com/c/parser/17) för samhällsstöd.
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan begära en[tillfällig licens](https://purchase.groupdocs.com/temporary-license/) för utvärdering och testning.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan ladda ner en[gratis provperiod](https://releases.groupdocs.com/) version av GroupDocs.Parser.