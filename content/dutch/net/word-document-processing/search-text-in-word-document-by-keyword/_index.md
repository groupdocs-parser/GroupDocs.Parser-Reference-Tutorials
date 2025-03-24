---
title: Zoek tekst in Word-document op trefwoord
linktitle: Zoek tekst in Word-document op trefwoord
second_title: GroupDocs.Parser .NET API
description: Leer hoe u naar tekst in Word-documenten kunt zoeken met GroupDocs.Parser voor .NET. Extraheer specifieke trefwoorden efficiënt.
weight: 18
url: /nl/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# Zoek tekst in Word-document op trefwoord

## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om met C# naar specifieke tekst in een Word-document te zoeken. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars tekst en metagegevens uit verschillende documentformaten kunnen extraheren, waaronder Word-documenten.
## Vereisten
Voordat u aan de slag gaat, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Ontwikkelomgeving: Installeer Visual Studio of een andere compatibele IDE.
2.  GroupDocs.Parser-bibliotheek: Download en installeer de GroupDocs.Parser voor .NET-bibliotheek vanaf de[website](https://releases.groupdocs.com/parser/net/).
3. Voorbeeld van een Word-document: bereid een voorbeeld van een Word-document voor dat u kunt gebruiken voor het zoeken naar tekst.

## Naamruimten importeren
Begin met het importeren van de benodigde naamruimten in uw C#-project:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Maak eerst een exemplaar van de`Parser` klasse door het pad naar uw voorbeeld-Word-document door te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code komt hier
}
```
## Stap 2: Zoek naar een trefwoord
 Gebruik vervolgens de`Search` werkwijze van de`Parser` class om te zoeken naar een specifiek trefwoord in het document.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Vervangen`"keyword"` met de tekst waarnaar u wilt zoeken in het document.
## Stap 3: Herhaal de zoekresultaten
 Herhaal de zoekresultaten met behulp van a`foreach` lus om toegang te krijgen tot elk`SearchResult` voorwerp.
```csharp
foreach (SearchResult result in searchResults)
{
    //Code om elk zoekresultaat te verwerken
}
```
## Stap 4: Toegang tot details van zoekresultaten
 Binnen de lus heeft u toegang tot de positie en tekst van elk zoekresultaat met behulp van de`Position` En`Text` eigenschappen van de`SearchResult` voorwerp.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Met dit codefragment wordt de index afgedrukt (`Position`) en de gevonden tekst (`Text`) voor elk zoekresultaat naar de console.

## Conclusie
In deze zelfstudie hebt u geleerd hoe u GroupDocs.Parser voor .NET kunt gebruiken om naar specifieke tekst in een Word-document te zoeken. Deze bibliotheek biedt een handige manier om programmatisch inhoud uit verschillende documentformaten te extraheren en te manipuleren.

## Veelgestelde vragen
### Kan GroupDocs.Parser naast Word ook andere documentformaten verwerken?
Ja, GroupDocs.Parser ondersteunt een breed scala aan indelingen, waaronder PDF, Excel, PowerPoint en meer.
### Is GroupDocs.Parser compatibel met .NET Core?
Ja, GroupDocs.Parser is compatibel met zowel .NET Framework als .NET Core.
### Hoe verkrijg ik een tijdelijke licentie voor GroupDocs.Parser?
 Een tijdelijke vergunning kunt u aanvragen bij de[GroupDocs-aankooppagina](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik aanvullende ondersteuning vinden of vragen stellen over GroupDocs.Parser?
 Bezoek de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) voor gemeenschapsondersteuning en discussies.
### Kan ik GroupDocs.Parser gratis uitproberen voordat ik een aankoop doe?
 Ja, u kunt een gratis proefversie downloaden van de[GroupDocs-releasepagina](https://releases.groupdocs.com/).