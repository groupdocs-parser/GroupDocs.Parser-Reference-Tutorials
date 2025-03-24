---
title: Extrahera streckkoder från skadade dokument
linktitle: Extrahera streckkoder från skadade dokument
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar streckkoder från skadade dokument med GroupDocs.Parser för .NET. Omfattande handledning med steg-för-steg-instruktioner.
weight: 11
url: /sv/net/barcode-extraction/extract-barcodes-from-corrupted-document/
---

# Extrahera streckkoder från skadade dokument

## Introduktion
den här handledningen guidar vi dig genom processen att extrahera streckkoder från skadade dokument med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt API för dokumentanalys som gör det möjligt för utvecklare att extrahera text, metadata, bilder och nu streckkoder från olika filformat. Vi kommer att bryta ner de steg som behövs för att utföra denna uppgift effektivt.
## Förutsättningar
Innan vi börjar, se till att du har följande:
-  GroupDocs.Parser för .NET: Du kan ladda ner biblioteket från[här](https://releases.groupdocs.com/parser/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklings-IDE.
- Exempel på skadat dokument: Förbered ett exempel på skadat dokument (t.ex. PDF, DOCX) för testning.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden för ditt .NET-projekt:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Steg 1: Initiera parsern
 Initiera först`Parser` objekt med din exempelfilsökväg:
```csharp
using (Parser parser = new Parser("YourSampleFilePath"))
{
    // Fortsätt med streckkodsextraktion...
}
```
## Steg 2: Kontrollera Barcode Extraction Support
Innan du fortsätter, se till att dokumentet stöder streckkodsextraktion:
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcodes extraction.");
    return;
}
```
## Steg 3: Ställ in alternativ för streckkodsextraktion
Definiera alternativen för streckkodsextraktion. Du kan ange parametrar som streckkodstyper, kvalitetsläge och andra inställningar:
```csharp
BarcodeOptions options = new BarcodeOptions(
    null,
    QualityMode.Low,
    QualityMode.Low,
    null,
    true,
    "pdf417",
    "QR"
);
```
## Steg 4: Extrahera streckkoder
Extrahera nu streckkoderna från dokumentet med de angivna alternativen:
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Steg 5: Iterera och bearbeta streckkoder
Iterera genom de extraherade streckkoderna och bearbeta var och en:
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
    Console.WriteLine("Confidence: " + barcode.Confidence.ToString());
}
```

## Slutsats
I den här handledningen visade vi hur man använder GroupDocs.Parser för .NET för att extrahera streckkoder från skadade dokument. Genom att följa dessa steg kan du effektivt hämta streckkodsinformation från olika filformat med ett enkelt och effektivt tillvägagångssätt.

## FAQ's
### Kan GroupDocs.Parser hantera flera typer av streckkoder?
Ja, GroupDocs.Parser stöder ett brett utbud av streckkodstyper inklusive QR-koder, PDF417 och mer.
### Vilka filformat stöder GroupDocs.Parser för extrahering av streckkoder?
GroupDocs.Parser kan extrahera streckkoder från populära format som PDF, DOCX, XLSX och andra.
### Finns det en gratis testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan få tillgång till en gratis testversion[här](https://releases.groupdocs.com/).
### Var kan jag få support för GroupDocs.Parser?
 För support och diskussioner, besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan skaffa en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).