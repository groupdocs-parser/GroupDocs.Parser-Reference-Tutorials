---
title: Herkennen van tekst in rechthoekige gebieden
linktitle: Herkennen van tekst in rechthoekige gebieden
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst in specifieke delen van documenten kunt herkennen met behulp van GroupDocs.Parser voor .NET met OCR-mogelijkheden.
weight: 14
url: /nl/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst in specifieke rechthoekige gebieden van documenten te herkennen. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars tekst, metagegevens en meer kunnen extraheren uit verschillende bestandsindelingen, waaronder PDF, Word, Excel en PowerPoint.
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende hebt ingesteld:
-  GroupDocs.Parser voor .NET: Download en installeer de bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
- Ontwikkelomgeving: Visual Studio of een andere .NET IDE.
- Voorbeelddocument: Zorg voor een voorbeeldbestand (bijvoorbeeld PDF, DOCX) dat tekst bevat die moet worden herkend.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-code importeren:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Initialiseer de parserinstellingen
 Begin met het instellen van de`ParserSettings` met de OCR-connector. Hier gebruiken we de Aspose OCR on-premise connector:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Stap 2: Parser-instantie maken
 Instantieer vervolgens de`Parser` klasse met de eerder gedefinieerde instellingen:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Code gaat hier verder
}
```
 Vervangen`"YourSampleFile.pdf"` met het pad naar uw document.
## Stap 3: Definieer de OCR-rechthoek
 Definieer een rechthoek binnen het document waar tekstherkenning zal worden uitgevoerd. Bijvoorbeeld een rechthoek die begint bij`(0, 0)` met breedte`400` en hoogte`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Stap 4: Configureer opties voor tekstherkenning
 Creëren`TextOptions` om het OCR-gebruik samen met de gedefinieerde rechthoek op te geven:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Stap 5: Tekst extraheren met OCR
 Gebruik de`GetText` werkwijze van de`Parser` exemplaar met de geconfigureerde`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Lees de geëxtraheerde tekst of handel 'niet ondersteund' geval af
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Conclusie
In deze zelfstudie hebben we gedemonstreerd hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit specifieke rechthoekige gebieden in documenten te extraheren met behulp van OCR. Dit proces kan verder worden aangepast en geïntegreerd in verschillende toepassingen voor geautomatiseerde tekstextractietaken.

## Veelgestelde vragen
### Kan GroupDocs.Parser tekst extraheren uit gescande documenten?
Ja, GroupDocs.Parser ondersteunt OCR (Optical Character Recognition) voor het extraheren van tekst uit gescande documenten.
### Welke bestandsformaten ondersteunt GroupDocs.Parser?
GroupDocs.Parser ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Hoe kan ik omgaan met documenten die niet worden ondersteund voor tekstextractie?
 U kunt controleren of tekstextractie wordt ondersteund met behulp van`TextReader` exemplaar geretourneerd door`parser.GetText(options)`.
### Is GroupDocs.Parser geschikt voor grootschalige tekstextractietaken?
Ja, GroupDocs.Parser is ontworpen om grootschalige tekstextractietaken efficiënt af te handelen.
### Waar kan ik ondersteuning krijgen voor problemen met GroupDocs.Parser?
 Voor ondersteuning en discussies kunt u terecht op de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).