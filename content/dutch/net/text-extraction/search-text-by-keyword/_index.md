---
title: Zoek tekst op trefwoord
linktitle: Zoek tekst op trefwoord
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst kunt zoeken op trefwoord in documenten met GroupDocs.Parser voor .NET. Haal op een efficiënte manier relevante inhoud eruit.
weight: 21
url: /nl/net/text-extraction/search-text-by-keyword/
---

# Zoek tekst op trefwoord

## Invoering
In deze zelfstudie gaan we dieper in op het gebruik van GroupDocs.Parser voor .NET om tekst op trefwoord in documenten te zoeken. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars tekst, metagegevens en andere informatie kunnen extraheren uit verschillende bestandsindelingen, zoals pdf's, Microsoft Office-documenten en meer. Het zoeken naar specifieke trefwoorden in deze documenten kan essentieel zijn voor toepassingen die te maken hebben met grote hoeveelheden tekstuele gegevens.
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende hebt ingesteld:
1. Ontwikkelomgeving: Visual Studio of een .NET IDE van uw voorkeur.
2.  GroupDocs.Parser voor .NET: Download de bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
3. Toegang tot voorbeeldbestanden: bereid een voorbeeldbestand voor (bijvoorbeeld PDF, DOCX) om de zoekfunctionaliteit op trefwoorden te testen.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw project opnemen.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Stap 1: Instantie van de parserklasse
 Begin met het maken van een exemplaar van de`Parser` class en geef het pad naar uw voorbeeldbestand op.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Zoek een trefwoord
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Herhaal de zoekresultaten
    foreach (SearchResult result in searchResults)
    {
        //Druk de index en gevonden tekst af
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Stap 2: Zoek naar een trefwoord
 Binnen de`using` blokkeren, bel de`Search` methode op de`parser` object, waarbij het gewenste trefwoord als argument wordt doorgegeven.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Vervangen`"test"` met het trefwoord waarnaar u in het document wilt zoeken.
## Stap 3: Herhaal de zoekresultaten
 Herhaal vervolgens de zoekresultaten die zijn verkregen uit de`Search` methode met behulp van een`foreach` lus.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Voor elk`SearchResult` voorwerp`result` , je hebt er toegang toe`Position` (index) en`Text` (de gevonden tekst).

## Conclusie
 In deze zelfstudie hebben we onderzocht hoe u GroupDocs.Parser voor .NET kunt gebruiken om moeiteloos tekst op trefwoord in documenten te zoeken. Het benutten van de`Search` werkwijze van de`Parser` class zorgt voor het efficiënt ophalen van relevante tekstfragmenten op basis van specifieke zoektermen.

## Veelgestelde vragen
### Is GroupDocs.Parser compatibel met verschillende documentformaten?
Ja, GroupDocs.Parser ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Kan ik geavanceerde tekstextractiebewerkingen uitvoeren met GroupDocs.Parser?
Absoluut! Naast tekstzoeken maakt GroupDocs.Parser extractie van metagegevens, gestructureerde tekstextractie en meer mogelijk.
### Waar kan ik gedetailleerde documentatie voor GroupDocs.Parser vinden?
Ontdek de volledige documentatie[hier](https://tutorials.groupdocs.com/parser/net/).
### Hoe kan ik ondersteuning of assistentie krijgen bij vragen over GroupDocs.Parser?
 Bezoek het GroupDocs-forum voor ondersteuning en discussies[hier](https://forum.groupdocs.com/c/parser/17).
### Is er een proefversie beschikbaar om GroupDocs.Parser te evalueren voordat u het aanschaft?
 Ja, u heeft toegang tot de gratis proefperiode[hier](https://releases.groupdocs.com/).