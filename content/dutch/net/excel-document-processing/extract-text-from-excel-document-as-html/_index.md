---
title: Extraheer tekst uit Excel-document als HTML
linktitle: Extraheer tekst uit Excel-document als HTML
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit Excel-documenten kunt extraheren en deze naar HTML kunt converteren met GroupDocs.Parser voor .NET.
weight: 13
url: /nl/net/excel-document-processing/extract-text-from-excel-document-as-html/
---

# Extraheer tekst uit Excel-document als HTML

## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit een Excel-document te extraheren en naar HTML-indeling te converteren. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars met verschillende documentformaten kunnen werken, waarbij tekst en metagegevens efficiënt kunnen worden geëxtraheerd.
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende hebt ingesteld:
- Visual Studio is op uw systeem geïnstalleerd.
- Basiskennis van programmeren in C#.
-  GroupDocs.Parser-bibliotheek voor .NET. Je kunt het downloaden van[hier](https://releases.groupdocs.com/parser/net/).
## Naamruimten importeren
Begin met het opnemen van de benodigde naamruimten in uw C#-project om toegang te krijgen tot de GroupDocs.Parser-functionaliteiten.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Instantieer eerst de`Parser` klasse door het pad naar uw Excel-document op te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Verdere code komt hier terecht
}
```
 Vervangen`"YourSampleFile.xlsx"` met het pad naar uw Excel-bestand.
## Stap 2: Tekst extraheren als HTML
 Binnen de`using` blok van de`Parser` Gebruik bijvoorbeeld de`GetFormattedText` methode om opgemaakte tekst in HTML-modus te extraheren.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Verdere code komt hier terecht
    }
}
```
## Stap 3: Geëxtraheerde HTML-tekst lezen en afdrukken
 Lees vervolgens de geëxtraheerde HTML-tekst uit het`TextReader` en print het naar de console.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Eenmaal uitgevoerd, haalt deze code de tekst uit het Excel-document en geeft deze als HTML-indeling weer in de console.
## Conclusie
In deze zelfstudie hebben we geleerd hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit een Excel-document te extraheren en naar HTML-indeling te converteren. Deze bibliotheek biedt een eenvoudige manier om met verschillende documentformaten te werken, waardoor ontwikkelaars tekstextractietaken in hun applicaties efficiënt kunnen afhandelen.

## Veelgestelde vragen
### Kan GroupDocs.Parser naast Excel ook andere documentformaten verwerken?
Ja, GroupDocs.Parser ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, Word, PowerPoint en meer.
### Is GroupDocs.Parser compatibel met .NET Core?
Ja, GroupDocs.Parser is compatibel met zowel .NET Framework als .NET Core.
### Behoudt GroupDocs.Parser de opmaak tijdens het extraheren van tekst?
Ja, GroupDocs.Parser kan opmaak, zoals lettertypen, stijlen en lay-out, behouden tijdens het extraheren van tekst.
### Kan ik metagegevens uit documenten extraheren met GroupDocs.Parser?
Ja, met GroupDocs.Parser kunt u metagegevens zoals auteur, aanmaakdatum en meer extraheren uit ondersteunde documenttypen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).