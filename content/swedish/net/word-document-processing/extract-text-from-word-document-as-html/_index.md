---
title: Extrahera text från Word-dokument som HTML
linktitle: Extrahera text från Word-dokument som HTML
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du använder GroupDocs.Parser för .NET för att extrahera text från Word-dokument och spara den som HTML. Steg-för-steg handledning med kodexempel.
type: docs
weight: 16
url: /sv/net/word-document-processing/extract-text-from-word-document-as-html/
---
## Introduktion
GroupDocs.Parser för .NET är ett kraftfullt dokumentanalysbibliotek som gör det möjligt för utvecklare att extrahera text och metadata från olika filformat sömlöst. I den här handledningen kommer vi att fokusera på att utnyttja GroupDocs.Parser för att extrahera text från Word-dokument och spara den som HTML. Denna process är viktig för uppgifter som innehållsanalys, indexering eller konvertering av dokument till webbvänliga format. I slutet av den här guiden har du en klar förståelse för hur du använder GroupDocs.Parser effektivt i dina .NET-applikationer.
## Förutsättningar
Innan du dyker in i den här handledningen, se till att du har följande förutsättningar:
- Grundläggande kunskaper i C#-programmering.
- Visual Studio installerat på din utvecklingsmaskin.
-  GroupDocs.Parser för .NET-bibliotek. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
- Tillgång till ett exempel på Word-dokument för teständamål.
## Importera namnområden
Till att börja med måste du importera de nödvändiga namnrymden till ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Följ dessa detaljerade steg för att extrahera text från ett Word-dokument och spara den som HTML med GroupDocs.Parser for .NET:
## Steg 1: Skapa en instans av Parser Class
 Skapa först en instans av`Parser` klass genom att ange sökvägen till ditt exempel på Word-dokument:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Fortsätt till steg 2...
}
```
 Byta ut`"YourSampleFile.docx"`med sökvägen till ditt Word-dokument.
## Steg 2: Extrahera formaterad text som HTML
 Använd sedan`GetFormattedText` metod tillsammans med`FormattedTextOptions`för att extrahera texten i HTML-format:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahera en formaterad text i läsaren
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Fortsätt till steg 3...
    }
}
```
## Steg 3: Läs och mata ut den extraherade HTML-koden
 Läs slutligen det extraherade HTML-innehållet från`TextReader` och skriv ut det till konsolen:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extrahera en formaterad text i läsaren
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Skriv ut den formaterade texten som HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Slutsats
I den här handledningen har vi utforskat hur man använder GroupDocs.Parser för .NET för att extrahera text från ett Word-dokument och spara den som HTML. Detta bibliotek erbjuder ett enkelt och effektivt sätt att analysera dokumentinnehåll, vilket gör det till ett ovärderligt verktyg för dokumentbearbetningsuppgifter i .NET-applikationer.

## FAQ's
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan begära en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta mer dokumentation för GroupDocs.Parser?
 Detaljerad dokumentation finns tillgänglig[här](https://reference.groupdocs.com/parser/net/).
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan komma åt den kostnadsfria testversionen[här](https://releases.groupdocs.com/).
### Hur får jag support för GroupDocs.Parser?
 Besök supportforumet[här](https://forum.groupdocs.com/c/parser/17).
### Vilka typer av dokument stöder GroupDocs.Parser?
GroupDocs.Parser stöder olika dokumentformat inklusive Word, PDF, Excel, PowerPoint och mer.