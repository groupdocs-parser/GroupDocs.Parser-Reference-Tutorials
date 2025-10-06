---
title: Extrahera streckkoder från dokument med alternativ
linktitle: Extrahera streckkoder från dokument med alternativ
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar streckkoder från dokument med GroupDocs.Parser för .NET. Omfattande handledning med kodexempel och vanliga frågor.
weight: 14
url: /sv/net/barcode-extraction/extract-barcodes-from-document-with-options/
type: docs
---
# Extrahera streckkoder från dokument med alternativ

## Introduktion
I den här handledningen går vi igenom processen att extrahera streckkoder från ett dokument med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt bibliotek som låter dig extrahera text, metadata och streckkoder från olika dokumentformat som PDF, Microsoft Word, Excel och mer.
## Förutsättningar
Innan du börjar, se till att du har följande förutsättningar på plats:
1. Utvecklingsmiljö: Se till att du har Visual Studio installerat på din dator.
2.  GroupDocs.Parser Library: Ladda ner och installera GroupDocs.Parser för .NET-biblioteket från[här](https://releases.groupdocs.com/parser/net/).
3. Exempeldokument: Förbered ett exempeldokument (t.ex. PDF, DOCX) som innehåller streckkoder för extrahering.

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till ditt C#-projekt för att använda GroupDocs.Parser-funktionerna.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Steg 1: Skapa en instans av Parser Class
 För att komma igång, skapa en instans av`Parser` klass genom att skicka sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Kod som ska läggas till i nästa steg
}
```
## Steg 2: Kontrollera Barcode Extraction Support
 Kontrollera sedan om dokumentet stöder streckkodsextraktion med hjälp av`Features` egendom av`Parser` exempel.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Steg 3: Definiera streckkodsextraktionsalternativ
 Ange nu alternativen för streckkodsextraktion med`BarcodeOptions`. Du kan ställa in parametrar som kvalitetslägen och streckkodstyper.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Steg 4: Extrahera streckkoder från dokumentet
 Använd`GetBarcodes` metod för`Parser` klass för att extrahera streckkoder baserat på de definierade alternativen.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Steg 5: Iterera och visa extraherade streckkoder
Slutligen, iterera genom de extraherade streckkoderna och visa deras sidindex och värden.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Slutsats
 I den här handledningen har vi lärt oss hur man extraherar streckkoder från ett dokument med GroupDocs.Parser för .NET. Denna process innebär att skapa en`Parser` t.ex. definiera extraktionsalternativ och iterera genom de extraherade streckkoderna. GroupDocs.Parser förenklar uppgiften att extrahera streckkoder från olika dokumentformat, vilket möjliggör effektiv dokumentbehandling i dina .NET-applikationer.

## FAQ's
### Kan GroupDocs.Parser extrahera streckkoder från PDF-dokument?
Ja, GroupDocs.Parser stöder extrahering av streckkoder från PDF-dokument tillsammans med andra format som DOCX, XLSX, etc.
### Vilka streckkodstyper stöder GroupDocs.Parser?
GroupDocs.Parser stöder olika streckkodstyper inklusive QR-koder, kod 39, kod 128 och mer.
### Kräver GroupDocs.Parser en licens för kommersiellt bruk?
 Ja, en giltig licens krävs för kommersiellt bruk. Du kan få en licens från[här](https://purchase.groupdocs.com/buy).
### Är GroupDocs.Parser lämplig för batchbehandling av dokument?
Ja, GroupDocs.Parser kan effektivt hantera batchbearbetning av dokument för textextraktion, metadatahämtning och streckkodsextraktion.
### Var kan jag hitta teknisk support för GroupDocs.Parser?
 Du kan få teknisk support eller ställa frågor om[GroupDocs forum](https://forum.groupdocs.com/c/parser/17).