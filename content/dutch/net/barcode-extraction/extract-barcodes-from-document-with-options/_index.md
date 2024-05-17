---
title: Extraheer streepjescodes uit document met opties
linktitle: Extraheer streepjescodes uit document met opties
second_title: GroupDocs.Parser .NET API
description: Leer hoe u streepjescodes uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Uitgebreide tutorial met codevoorbeelden en veelgestelde vragen.
type: docs
weight: 14
url: /nl/net/barcode-extraction/extract-barcodes-from-document-with-options/
---
## Invoering
In deze zelfstudie doorlopen we het proces van het extraheren van streepjescodes uit een document met behulp van GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige bibliotheek waarmee u tekst, metagegevens en streepjescodes kunt extraheren uit verschillende documentformaten zoals PDF, Microsoft Word, Excel en meer.
## Vereisten
Voordat u begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Ontwikkelomgeving: Zorg ervoor dat Visual Studio op uw computer is geïnstalleerd.
2.  GroupDocs.Parser-bibliotheek: Download en installeer de GroupDocs.Parser voor .NET-bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
3. Voorbeelddocument: maak een voorbeelddocument (bijv. PDF, DOCX) met streepjescodes voor extractie.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren om de GroupDocs.Parser-functionaliteiten te kunnen gebruiken.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Om aan de slag te gaan, maakt u een exemplaar van de`Parser` klasse door het pad naar uw voorbeelddocument door te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code die in de volgende stappen moet worden toegevoegd
}
```
## Stap 2: Controleer ondersteuning voor streepjescode-extractie
 Controleer vervolgens of het document streepjescode-extractie ondersteunt met behulp van de`Features` eigendom van de`Parser` voorbeeld.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Stap 3: Definieer opties voor streepjescode-extractie
 Geef nu de opties voor streepjescode-extractie op met behulp van`BarcodeOptions`. U kunt parameters instellen zoals kwaliteitsmodi en barcodetypen.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Stap 4: Extraheer streepjescodes uit het document
 Gebruik de`GetBarcodes` werkwijze van de`Parser` klasse om streepjescodes te extraheren op basis van de gedefinieerde opties.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Stap 5: Herhaal en geef geëxtraheerde streepjescodes weer
Herhaal ten slotte de geëxtraheerde streepjescodes en geef hun pagina-index en waarden weer.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusie
 In deze zelfstudie hebben we geleerd hoe u streepjescodes uit een document kunt extraheren met GroupDocs.Parser voor .NET. Dit proces omvat het maken van een`Parser` bijvoorbeeld door extractieopties te definiëren en door de geëxtraheerde streepjescodes te bladeren. GroupDocs.Parser vereenvoudigt de taak van het extraheren van streepjescodes uit verschillende documentformaten, waardoor efficiënte documentverwerking binnen uw .NET-toepassingen mogelijk wordt.

## Veelgestelde vragen
### Kan GroupDocs.Parser streepjescodes uit PDF-documenten extraheren?
Ja, GroupDocs.Parser ondersteunt streepjescode-extractie uit PDF-documenten samen met andere formaten zoals DOCX, XLSX, enz.
### Welke typen streepjescodes ondersteunt GroupDocs.Parser?
GroupDocs.Parser ondersteunt verschillende typen streepjescodes, waaronder QR-codes, Code 39, Code 128 en meer.
### Heeft GroupDocs.Parser een licentie nodig voor commercieel gebruik?
 Ja, voor commercieel gebruik is een geldige licentie vereist. Een licentie kunt u verkrijgen bij[hier](https://purchase.groupdocs.com/buy).
### Is GroupDocs.Parser geschikt voor batchverwerking van documenten?
Ja, GroupDocs.Parser kan op efficiënte wijze batchverwerking van documenten verwerken voor tekstextractie, ophalen van metagegevens en extractie van streepjescodes.
### Waar kan ik technische ondersteuning vinden voor GroupDocs.Parser?
 U kunt technische ondersteuning krijgen of vragen stellen over de[GroupDocs-forum](https://forum.groupdocs.com/c/parser/17).