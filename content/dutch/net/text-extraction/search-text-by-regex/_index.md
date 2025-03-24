---
title: Tekst zoeken op reguliere expressie (Regex)
linktitle: Tekst zoeken op reguliere expressie (Regex)
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst kunt doorzoeken met behulp van reguliere expressies in documenten met GroupDocs.Parser voor .NET. Extraheer specifieke inhoud moeiteloos.
weight: 23
url: /nl/net/text-extraction/search-text-by-regex/
---

# Tekst zoeken op reguliere expressie (Regex)

## Invoering
In deze zelfstudie gaan we dieper in op het gebruik van GroupDocs.Parser voor .NET om tekst te zoeken op reguliere expressie (Regex) in documenten. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars tekst en metagegevens kunnen extraheren uit verschillende bestandsformaten zoals PDF, DOCX, XLSX en meer. Zoeken naar tekst met behulp van reguliere expressies is vooral handig om op efficiënte wijze patronen of specifieke inhoud in documenten te vinden.
## Vereisten
Voordat u in deze zelfstudie duikt, moet u ervoor zorgen dat u over het volgende beschikt:
1. Visual Studio: Installeer Visual Studio IDE voor .NET-ontwikkeling.
2.  GroupDocs.Parser voor .NET: Download en installeer GroupDocs.Parser voor .NET vanaf[hier](https://releases.groupdocs.com/parser/net/).
3. Voorbeeldbestand: bereid een voorbeelddocument voor (PDF, DOCX, enz.) om de zoekfunctionaliteit te testen.

## Naamruimten importeren
Begin eerst met het opnemen van de benodigde naamruimten in uw C#-code:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Instantieer de`Parser` class door het pad naar uw voorbeeldbestand op te geven:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code komt hier
}
```
 Vervangen`"YourSampleFile.pdf"` met het pad naar uw daadwerkelijke bestand.
## Stap 2: Zoeken met reguliere expressie
Definieer en voer de zoekopdracht uit met behulp van een reguliere-expressiepatroon. Om bijvoorbeeld numerieke reeksen (bijvoorbeeld gehele getallen) in het document te vinden:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 In dit voorbeeld`[0-9]+` is een reguliere-expressiepatroon dat overeenkomt met een of meer cijfers.
## Stap 3: Controleer zoekondersteuning
Controleer of de zoekbewerking wordt ondersteund voor het documenttype:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Stap 4: herhaal de zoekresultaten
Blader door de zoekresultaten en verwerk elke overeenkomst:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Deze lus drukt de positie en de overeenkomende tekst in het document af.

## Conclusie
Kortom, het gebruik van GroupDocs.Parser voor .NET maakt efficiënt zoeken naar tekst mogelijk met behulp van reguliere expressies in verschillende documentformaten. Door deze handleiding te volgen, kunnen ontwikkelaars het parseren van documenten en op regex gebaseerde tekstextractie naadloos integreren in hun .NET-applicaties.

## Veelgestelde vragen
### Kan GroupDocs.Parser zoeken in gecodeerde documenten?
Nee, GroupDocs.Parser kan niet zoeken in gecodeerde of met een wachtwoord beveiligde documenten.
### Ondersteunt GroupDocs.Parser OCR (Optical Character Recognition)?
Nee, GroupDocs.Parser voert geen OCR uit. Het is afhankelijk van tekstextractie uit de interne structuur van het document.
### Kan ik met reguliere expressies naar complexe patronen zoeken?
Ja, GroupDocs.Parser ondersteunt volwaardige reguliere expressies, waardoor complexe patroonmatching binnen documenten mogelijk wordt.
### Welke documentformaten worden ondersteund voor tekstextractie?
GroupDocs.Parser ondersteunt een breed scala aan formaten, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Is GroupDocs.Parser compatibel met .NET Core?
Ja, GroupDocs.Parser is compatibel met .NET Core voor platformonafhankelijke ontwikkeling.