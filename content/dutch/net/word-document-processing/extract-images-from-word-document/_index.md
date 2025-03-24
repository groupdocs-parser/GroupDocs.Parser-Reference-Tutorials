---
title: Afbeeldingen extraheren uit een Word-document
linktitle: Afbeeldingen extraheren uit een Word-document
second_title: GroupDocs.Parser .NET API
description: Leer hoe u afbeeldingen uit een Word-document kunt extraheren met GroupDocs.Parser voor .NET. Deze tutorial biedt stapsgewijze begeleiding voor het integreren van image in uw .NET.
weight: 11
url: /nl/net/word-document-processing/extract-images-from-word-document/
---

# Afbeeldingen extraheren uit een Word-document

## Invoering
In deze zelfstudie leert u hoe u afbeeldingen uit een Word-document kunt extraheren met GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige .NET-bibliotheek waarmee u tekst, metagegevens, afbeeldingen en meer kunt ontleden en extraheren uit verschillende documentindelingen, waaronder Word (DOCX).
## Vereisten
Voordat u begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- Visual Studio is op uw computer geïnstalleerd.
- Basiskennis van programmeren in C#.
- GroupDocs.Parser voor .NET-bibliotheek geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/parser/net/).
## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren om de functionaliteiten van GroupDocs.Parser te kunnen gebruiken:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Laten we nu het proces van het extraheren van afbeeldingen uit een Word-document in eenvoudige stappen opsplitsen:
## Stap 1: Maak een exemplaar van de parserklasse
 U begint met het maken van een exemplaar van de`Parser`class, waarbij u het pad naar uw Word-document als invoer opgeeft.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code voor het extraheren van afbeeldingen vindt u hier
}
```
## Stap 2: Extraheer afbeeldingen uit het Word-document
 Gebruik vervolgens de`GetImages()` werkwijze van de`Parser` object om afbeeldingen uit het document te extraheren.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Stap 3: Definieer opties voor het opslaan van afbeeldingen
Geef de opties op voor het opslaan van de geëxtraheerde afbeeldingen. U kunt bijvoorbeeld het afbeeldingsformaat kiezen (bijvoorbeeld PNG) en andere instellingen configureren.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Stap 4: Herhaal de geëxtraheerde afbeeldingen en sla deze op
Doorloop elke geëxtraheerde afbeelding en sla deze op in een bestand met behulp van de opgegeven opties.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Sla de afbeelding op in een PNG-bestand
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Conclusie
In deze zelfstudie hebt u geleerd hoe u afbeeldingen uit een Word-document kunt extraheren met GroupDocs.Parser voor .NET. Door deze stappen te volgen, kunt u eenvoudig mogelijkheden voor het parseren van documenten en het extraheren van afbeeldingen integreren in uw .NET-toepassingen.

## Veelgestelde vragen
### Kan GroupDocs.Parser afbeeldingen extraheren uit andere documentformaten dan Word?
Ja, GroupDocs.Parser ondersteunt verschillende documentformaten, waaronder PDF, PowerPoint, Excel en meer.
### Hoe kan ik een tijdelijke licentie krijgen voor GroupDocs.Parser?
 Een tijdelijke licentie voor testdoeleinden kunt u verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik meer documentatie vinden over GroupDocs.Parser voor .NET?
 U kunt de volledige documentatie raadplegen[hier](https://tutorials.groupdocs.com/parser/net/).
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt de functies van GroupDocs.Parser verkennen met een gratis proefversie[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen of vragen stellen met betrekking tot GroupDocs.Parser?
 U kunt uw vragen op de website plaatsen[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).