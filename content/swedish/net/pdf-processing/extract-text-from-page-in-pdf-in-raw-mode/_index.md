---
title: Extrahera text från sidan i PDF i råläge
linktitle: Extrahera text från sidan i PDF i råläge
second_title: GroupDocs.Parser .NET API
description: Extrahera text från PDF-filer med GroupDocs.Parser i C#. Lär dig effektiv PDF-textextraktion med detta kraftfulla .NET-bibliotek.
weight: 16
url: /sv/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
type: docs
---
# Extrahera text från sidan i PDF i råläge

## Introduktion
I den här handledningen kommer vi att undersöka hur du använder GroupDocs.Parser för .NET för att extrahera text från sidor i PDF-dokument med råläge. GroupDocs.Parser är ett kraftfullt verktyg som gör det möjligt för utvecklare att arbeta med olika dokumentformat programmatiskt.
## Förutsättningar
Innan du börjar den här handledningen, se till att du har följande:
- Visual Studio installerat på din dator.
- Grundläggande kunskaper i C#-programmering.
- GroupDocs.Parser för .NET-bibliotek, vilket du kan[ladda ner här](https://releases.groupdocs.com/parser/net/).
- Ett exempel på PDF-fil för teständamål.

## Importera namnområden
Se först till att importera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Till att börja, instansiera`Parser`klass genom att ange sökvägen till din exempel-PDF-fil.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Din kod kommer hit
}
```
## Steg 2: Få dokumentinformation och iterera över sidor
Hämta sedan dokumentinformationen och iterera över varje sida för att extrahera text.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Din kod för textextraktion kommer här
}
```
## Steg 3: Extrahera text från varje sida
 Inom slingan använder du`GetText` metod för att extrahera text från varje sida och skriva ut den.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Slutsats
 I den här handledningen har vi lärt oss hur man extraherar text från PDF-sidor i råläge med GroupDocs.Parser för .NET. Denna process innebär att skapa en`Parser` t.ex. hämta dokumentinformation, iterera över varje sida och extrahera text med hjälp av`GetText` metod.

## FAQ's
### Vad är GroupDocs.Parser för .NET?
GroupDocs.Parser för .NET är ett API för dokumenttolkning som tillåter utvecklare att extrahera text, metadata och annan information från olika filformat programmatiskt.
### Hur laddar jag ner GroupDocs.Parser för .NET?
 Du kan ladda ner biblioteket från[GroupDocs webbplats](https://releases.groupdocs.com/parser/net/).
### Finns det en gratis provperiod?
 Ja, du kan få tillgång till en gratis provversion av GroupDocs.Parser för .NET från[här](https://releases.groupdocs.com/).
### Var kan jag hitta support för GroupDocs.Parser för .NET?
 För teknisk assistans och gemenskapsstöd, besök[GroupDocs forum](https://forum.groupdocs.com/c/parser/17).
### Hur kan jag köpa en licens för GroupDocs.Parser för .NET?
 Du kan köpa en licens från[köpsidan](https://purchase.groupdocs.com/buy) eller skaffa en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).