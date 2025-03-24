---
title: Sök text med höjdpunkter
linktitle: Sök text med höjdpunkter
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du söker och markerar text i dokument med GroupDocs.Parser för .NET. Extrahera värdefulla insikter effektivt.
weight: 24
url: /sv/net/text-extraction/search-text-with-highlights/
---
## Introduktion
den här självstudien kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att söka efter text i ett dokument och markera sökresultaten. GroupDocs.Parser är ett kraftfullt bibliotek som låter dig arbeta med olika dokumentformat och extrahera text, metadata och mer.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  GroupDocs.Parser för .NET: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/parser/net/).
2. IDE: Använd Visual Studio eller någon föredragen IDE för .NET-utveckling.
3. Exempelfil: Förbered ett exempeldokument (t.ex. PDF, DOCX) för textsökning.

## Importera namnområden
Börja först med att importera de nödvändiga namnrymden i ditt .NET-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa Parser-instans
 Börja med att instansiera`Parser` klass med sökvägen till din exempelfil:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Din kod här
}
```
## Steg 2: Definiera höjdpunkter
 Specificera`HighlightOptions` för att konfigurera hur sökresultat ska markeras. Till exempel, ställa in ett sammanhangsfönster med 15 tecken:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Steg 3: Sök text
Gör nu en textsökning i dokumentet. Ange nyckelordet du vill söka efter (t.ex. "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Steg 4: Bearbeta sökresultat
Gå igenom sökresultaten och visa den hittade texten tillsammans med höjdpunkterna:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Slutsats
den här handledningen lärde du dig hur du använder GroupDocs.Parser för .NET för att söka efter text i dokument och markera sökresultaten. Denna funktion kan vara oerhört användbar för textextraktion och analys i dina .NET-applikationer.

## FAQ's
### Är GroupDocs.Parser lämplig för bearbetning av olika dokumentformat?
Ja, GroupDocs.Parser stöder ett brett utbud av dokumentformat inklusive PDF, DOCX, XLSX, PPTX och mer.
### Kan jag använda GroupDocs.Parser för att extrahera metadata från dokument?
Absolut! GroupDocs.Parser låter dig extrahera metadata, text och strukturerad data från dokument.
### Var kan jag hitta support eller ställa frågor om GroupDocs.Parser?
 Du kan besöka[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) för alla supportrelaterade frågor.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan komma åt en[gratis provperiod](https://releases.groupdocs.com/) av GroupDocs.Parser för att utvärdera dess funktioner.
### Hur kan jag köpa en licens för GroupDocs.Parser?
 Du kan köpa en licens från[här](https://purchase.groupdocs.com/buy) och även få tillfälliga licenser[här](https://purchase.groupdocs.com/temporary-license/).