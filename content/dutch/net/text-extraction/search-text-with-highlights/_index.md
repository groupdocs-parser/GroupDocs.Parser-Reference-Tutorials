---
title: Zoek tekst met hoogtepunten
linktitle: Zoek tekst met hoogtepunten
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst in documenten kunt zoeken en markeren met GroupDocs.Parser voor .NET. Haal op efficiënte wijze waardevolle inzichten eruit.
weight: 24
url: /nl/net/text-extraction/search-text-with-highlights/
type: docs
---
# Zoek tekst met hoogtepunten

## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om naar tekst in een document te zoeken en de zoekresultaten te markeren. GroupDocs.Parser is een krachtige bibliotheek waarmee u met verschillende documentformaten kunt werken en tekst, metagegevens en meer kunt extraheren.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1.  GroupDocs.Parser voor .NET: Download en installeer de bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
2. IDE: Gebruik Visual Studio of een andere IDE van uw voorkeur voor .NET-ontwikkeling.
3. Voorbeeldbestand: bereid een voorbeelddocument voor (bijvoorbeeld PDF, DOCX) voor tekstzoeken.

## Naamruimten importeren
Begin eerst met het importeren van de benodigde naamruimten in uw .NET-project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Parser-instantie maken
 Begin met het instantiëren van de`Parser` class met het pad naar uw voorbeeldbestand:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Jouw code hier
}
```
## Stap 2: Markeeropties definiëren
 Specificeer de`HighlightOptions` om te configureren hoe zoekresultaten moeten worden gemarkeerd. Als u bijvoorbeeld een contextvenster van 15 tekens instelt:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Stap 3: Zoek tekst
Voer nu een tekstzoekopdracht uit in het document. Geef het trefwoord op waarnaar u wilt zoeken (bijvoorbeeld 'lorem'):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Stap 4: Zoekresultaten verwerken
Blader door de zoekresultaten en geef de gevonden tekst samen met de hoogtepunten weer:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusie
In deze zelfstudie hebt u geleerd hoe u GroupDocs.Parser voor .NET kunt gebruiken om naar tekst in documenten te zoeken en de zoekresultaten te markeren. Deze functionaliteit kan enorm nuttig zijn voor tekstextractie en -analyse in uw .NET-applicaties.

## Veelgestelde vragen
### Is GroupDocs.Parser geschikt voor het verwerken van verschillende documentformaten?
Ja, GroupDocs.Parser ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Kan ik GroupDocs.Parser gebruiken om metagegevens uit documenten te extraheren?
Absoluut! Met GroupDocs.Parser kunt u metagegevens, tekst en gestructureerde gegevens uit documenten extraheren.
### Waar kan ik ondersteuning vinden of vragen stellen over GroupDocs.Parser?
 U kunt een bezoek brengen aan de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) voor alle ondersteuningsgerelateerde vragen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u heeft toegang tot a[gratis proefperiode](https://releases.groupdocs.com/) van GroupDocs.Parser om de functies ervan te evalueren.
### Hoe kan ik een licentie kopen voor GroupDocs.Parser?
 U kunt een licentie kopen bij[hier](https://purchase.groupdocs.com/buy) en ook tijdelijke licenties verkrijgen[hier](https://purchase.groupdocs.com/temporary-license/).