---
title: Extraheer streepjescodes uit een beschadigd document
linktitle: Extraheer streepjescodes uit een beschadigd document
second_title: GroupDocs.Parser .NET API
description: Leer hoe u streepjescodes uit beschadigde documenten kunt extraheren met GroupDocs.Parser voor .NET. Uitgebreide tutorial met stapsgewijze instructies.
weight: 11
url: /nl/net/barcode-extraction/extract-barcodes-from-corrupted-document/
---
## Invoering
In deze zelfstudie begeleiden we u bij het extraheren van streepjescodes uit beschadigde documenten met GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige API voor het parseren van documenten waarmee ontwikkelaars tekst, metagegevens, afbeeldingen en nu ook streepjescodes uit verschillende bestandsindelingen kunnen extraheren. We zullen de stappen uiteenzetten die nodig zijn om deze taak effectief te volbrengen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
-  GroupDocs.Parser voor .NET: U kunt de bibliotheek downloaden van[hier](https://releases.groupdocs.com/parser/net/).
- Ontwikkelomgeving: Visual Studio of een andere .NET-ontwikkelings-IDE.
- Voorbeeld van een beschadigd document: Maak een voorbeeld van een beschadigd document (bijvoorbeeld PDF, DOCX) klaar om te testen.

## Naamruimten importeren
Begin met het importeren van de benodigde naamruimten voor uw .NET-project:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Stap 1: Initialiseer de parser
 Initialiseer eerst de`Parser` object met uw voorbeeldbestandspad:
```csharp
using (Parser parser = new Parser("YourSampleFilePath"))
{
    // Ga door met het extraheren van streepjescodes...
}
```
## Stap 2: Controleer ondersteuning voor streepjescode-extractie
Voordat u doorgaat, moet u ervoor zorgen dat het document streepjescode-extractie ondersteunt:
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcodes extraction.");
    return;
}
```
## Stap 3: Stel opties voor streepjescode-extractie in
Definieer de opties voor het extraheren van streepjescodes. U kunt parameters opgeven zoals streepjescodetypen, kwaliteitsmodus en andere instellingen:
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
## Stap 4: Streepjescodes extraheren
Extraheer nu de streepjescodes uit het document met behulp van de opgegeven opties:
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Stap 5: Streepjescodes herhalen en verwerken
Blader door de geëxtraheerde streepjescodes en verwerk ze allemaal:
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
    Console.WriteLine("Confidence: " + barcode.Confidence.ToString());
}
```

## Conclusie
In deze zelfstudie hebben we gedemonstreerd hoe u GroupDocs.Parser voor .NET kunt gebruiken om streepjescodes uit beschadigde documenten te extraheren. Door deze stappen te volgen, kunt u op een eenvoudige en effectieve manier barcodeinformatie efficiënt ophalen uit verschillende bestandsformaten.

## Veelgestelde vragen
### Kan GroupDocs.Parser meerdere soorten streepjescodes verwerken?
Ja, GroupDocs.Parser ondersteunt een breed scala aan barcodetypen, waaronder QR-codes, PDF417 en meer.
### Welke bestandsformaten ondersteunt GroupDocs.Parser voor het extraheren van streepjescodes?
GroupDocs.Parser kan streepjescodes extraheren uit populaire formaten zoals PDF, DOCX, XLSX en andere.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u heeft toegang tot een gratis proefversie[hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen voor GroupDocs.Parser?
 Voor ondersteuning en discussies kunt u terecht op de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 U kunt een tijdelijke licentie aanschaffen[hier](https://purchase.groupdocs.com/temporary-license/).