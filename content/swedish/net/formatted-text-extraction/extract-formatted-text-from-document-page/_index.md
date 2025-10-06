---
title: Extrahera formaterad text från dokumentsidan
linktitle: Extrahera formaterad text från dokumentsidan
second_title: GroupDocs.Parser .NET API
description: Extrahera formaterad text från dokumentsidor med GroupDocs.Parser för .NET. Effektiv och pålitlig textextraktionslösning.
weight: 11
url: /sv/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# Extrahera formaterad text från dokumentsidan

## Introduktion
I den här handledningen guidar vi dig genom processen att extrahera formaterad text från dokumentsidor med GroupDocs.Parser för .NET. Detta bibliotek låter dig analysera och extrahera text från olika dokumentformat som PDF, Word, Excel och mer.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio installerat på ditt system.
- Grundläggande kunskaper i C#-programmering.
-  GroupDocs.Parser för .NET-bibliotek. Du kan ladda ner den[här](https://releases.groupdocs.com/parser/net/).

## Importera namnområden
Börja först med att importera de nödvändiga namnrymden till ditt C#-projekt.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Börja med att skapa en instans av`Parser` klass genom att ange sökvägen till din exempelfil.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Koden kommer hit
}
```
## Steg 2: Kontrollera om formaterad textextraktion stöds
Innan du fortsätter med textextrahering, kontrollera om dokumentet stöder formaterad textextraktion.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Steg 3: Få dokumentinformation
Hämta information om dokumentet, till exempel antalet sidor.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Steg 4: Iterera över dokumentsidor och extrahera formaterad text
Iterera genom varje sida i dokumentet och extrahera formaterad text med angivna alternativ (t.ex. Markdown-format).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Slutsats
Nu vet du hur du extraherar formaterad text från dokumentsidor med GroupDocs.Parser för .NET. Detta bibliotek tillhandahåller en kraftfull och lättanvänd lösning för textextraktion från olika filformat.

## FAQ's
### Kan GroupDocs.Parser hantera olika filformat?
Ja, GroupDocs.Parser stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, XLSX, PPTX och mer.
### Är GroupDocs.Parser kompatibel med .NET Core?
Ja, GroupDocs.Parser stöder .NET Core och .NET Framework.
### Behåller GroupDocs.Parser textformatering under extrahering?
Ja, GroupDocs.Parser kan behålla formatering som stilar och teckensnitt när text extraheras.
### Kan jag extrahera bilder och metadata med GroupDocs.Parser?
Ja, GroupDocs.Parser tillåter extrahering av bilder, metadata och text från dokument.
### Hur kan jag få support för GroupDocs.Parser?
 Du kan få stöd från[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).