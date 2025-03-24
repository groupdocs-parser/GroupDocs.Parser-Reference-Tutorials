---
title: Extraheer tekst van pagina in PDF in Raw-modus
linktitle: Extraheer tekst van pagina in PDF in Raw-modus
second_title: GroupDocs.Parser .NET API
description: Extraheer tekst uit PDF's met GroupDocs.Parser in C#. Leer efficiënte PDF-tekstextractie met deze krachtige .NET-bibliotheek.
weight: 16
url: /nl/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# Extraheer tekst van pagina in PDF in Raw-modus

## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit pagina's in PDF-documenten te extraheren in de onbewerkte modus. GroupDocs.Parser is een krachtige tool waarmee ontwikkelaars programmatisch met verschillende documentformaten kunnen werken.
## Vereisten
Voordat u met deze zelfstudie begint, moet u ervoor zorgen dat u over het volgende beschikt:
- Visual Studio is op uw computer geïnstalleerd.
- Basiskennis van programmeren in C#.
- GroupDocs.Parser voor .NET-bibliotheek, wat u kunt[download hier](https://releases.groupdocs.com/parser/net/).
- Een voorbeeld-PDF-bestand voor testdoeleinden.

## Naamruimten importeren
Zorg er eerst voor dat u de benodigde naamruimten in uw C#-project importeert:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Instantieer om te beginnen de`Parser`klasse door het pad naar uw voorbeeld-PDF-bestand op te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Je code komt hier
}
```
## Stap 2: Documentinformatie ophalen en pagina's herhalen
Haal vervolgens de documentinformatie op en herhaal elke pagina om tekst te extraheren.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Uw code voor tekstextractie komt hier terecht
}
```
## Stap 3: Extraheer tekst van elke pagina
 Gebruik binnen de lus de`GetText` methode om tekst van elke pagina te extraheren en af te drukken.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusie
 In deze zelfstudie hebben we geleerd hoe u tekst uit PDF-pagina's kunt extraheren in de onbewerkte modus met behulp van GroupDocs.Parser voor .NET. Dit proces omvat het maken van een`Parser` bijvoorbeeld het verkrijgen van documentinformatie, het doorlopen van elke pagina en het extraheren van tekst met behulp van de`GetText` methode.

## Veelgestelde vragen
### Wat is GroupDocs.Parser voor .NET?
GroupDocs.Parser voor .NET is een API voor het parseren van documenten waarmee ontwikkelaars programmatisch tekst, metagegevens en andere informatie uit verschillende bestandsindelingen kunnen extraheren.
### Hoe download ik GroupDocs.Parser voor .NET?
 U kunt de bibliotheek downloaden via de[GroupDocs-website](https://releases.groupdocs.com/parser/net/).
### Is er een gratis proefversie beschikbaar?
 Ja, u heeft toegang tot een gratis proefversie van GroupDocs.Parser voor .NET vanaf[hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning vinden voor GroupDocs.Parser voor .NET?
 Voor technische hulp en gemeenschapsondersteuning gaat u naar de[GroupDocs-forum](https://forum.groupdocs.com/c/parser/17).
### Hoe kan ik een licentie kopen voor GroupDocs.Parser voor .NET?
 U kunt een licentie aanschaffen bij de[aankooppagina](https://purchase.groupdocs.com/buy) of een tijdelijke licentie aanschaffen[hier](https://purchase.groupdocs.com/temporary-license/).