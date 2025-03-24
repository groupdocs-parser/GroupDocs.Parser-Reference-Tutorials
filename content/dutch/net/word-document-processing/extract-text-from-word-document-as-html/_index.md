---
title: Extraheer tekst uit een Word-document als HTML
linktitle: Extraheer tekst uit een Word-document als HTML
second_title: GroupDocs.Parser .NET API
description: Leer hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit Word-documenten te extraheren en op te slaan als HTML. Stapsgewijze zelfstudie met codevoorbeelden.
weight: 16
url: /nl/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Extraheer tekst uit een Word-document als HTML

## Invoering
GroupDocs.Parser voor .NET is een krachtige bibliotheek voor het parseren van documenten waarmee ontwikkelaars naadloos tekst en metagegevens uit verschillende bestandsindelingen kunnen extraheren. In deze zelfstudie concentreren we ons op het gebruik van GroupDocs.Parser om tekst uit Word-documenten te extraheren en op te slaan als HTML. Dit proces is essentieel voor taken zoals inhoudsanalyse, indexering of het converteren van documenten naar webvriendelijke formaten. Aan het einde van deze handleiding heeft u een duidelijk inzicht in hoe u GroupDocs.Parser efficiënt kunt gebruiken in uw .NET-toepassingen.
## Vereisten
Voordat u in deze zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- Basiskennis van programmeren in C#.
- Visual Studio is geïnstalleerd op uw ontwikkelmachine.
-  GroupDocs.Parser voor .NET-bibliotheek. Je kunt het downloaden van[hier](https://releases.groupdocs.com/parser/net/).
- Toegang tot een voorbeeld van een Word-document voor testdoeleinden.
## Naamruimten importeren
Om te beginnen moet u de benodigde naamruimten in uw C#-project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Volg deze gedetailleerde stappen om tekst uit een Word-document te extraheren en op te slaan als HTML met GroupDocs.Parser voor .NET:
## Stap 1: Maak een exemplaar van de parserklasse
 Maak eerst een exemplaar van de`Parser` klasse door het pad naar uw voorbeeld-Word-document op te geven:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ga verder naar stap 2...
}
```
 Vervangen`"YourSampleFile.docx"`met het pad naar uw Word-document.
## Stap 2: Opgemaakte tekst extraheren als HTML
 Gebruik vervolgens de`GetFormattedText` methode mee`FormattedTextOptions`om de tekst in HTML-formaat te extraheren:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraheer een opgemaakte tekst in de reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Ga verder naar stap 3...
    }
}
```
## Stap 3: Lees de uitgepakte HTML en voer deze uit
 Lees ten slotte de geëxtraheerde HTML-inhoud uit het`TextReader` en print het naar de console:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Extraheer een opgemaakte tekst in de reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Druk de opgemaakte tekst af als HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Conclusie
In deze zelfstudie hebben we onderzocht hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit een Word-document te extraheren en op te slaan als HTML. Deze bibliotheek biedt een eenvoudige en efficiënte manier om documentinhoud te ontleden, waardoor het een hulpmiddel van onschatbare waarde is voor documentverwerkingstaken in .NET-toepassingen.

## Veelgestelde vragen
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 Een tijdelijke licentie kunt u aanvragen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik meer documentatie voor GroupDocs.Parser vinden?
 Gedetailleerde documentatie is beschikbaar[hier](https://tutorials.groupdocs.com/parser/net/).
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u heeft toegang tot de gratis proefversie[hier](https://releases.groupdocs.com/).
### Hoe krijg ik ondersteuning voor GroupDocs.Parser?
 Bezoek het ondersteuningsforum[hier](https://forum.groupdocs.com/c/parser/17).
### Welke soorten documenten ondersteunt GroupDocs.Parser?
GroupDocs.Parser ondersteunt verschillende documentformaten, waaronder Word, PDF, Excel, PowerPoint en meer.