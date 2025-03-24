---
title: Extraheer tekst uit specifieke gebieden met opties
linktitle: Extraheer tekst uit specifieke gebieden met opties
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit specifieke gebieden in documenten kunt extraheren met GroupDocs.Parser voor .NET. Ontdek geavanceerde opties voor tekstextractie met deze tutorial.
weight: 14
url: /nl/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit specifieke gebieden in een document te extraheren met behulp van aanpasbare opties. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars moeiteloos tekst uit verschillende documentformaten kunnen ontleden en extraheren.
## Vereisten
Voordat we ingaan op de codering, zorg ervoor dat je over het volgende beschikt:
1. Ontwikkelomgeving: Installeer Visual Studio of een andere .NET-ontwikkelings-IDE.
2.  GroupDocs.Parser-bibliotheek: Download en installeer GroupDocs.Parser voor .NET van[hier](https://releases.groupdocs.com/parser/net/).
3. Voorbeeldbestand: Bereid een voorbeelddocument voor (bijvoorbeeld PDF, DOCX, enz.) waaruit u tekst kunt extraheren.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten importeren om toegang te krijgen tot de GroupDocs.Parser-klassen en -methoden.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Initialiseer een exemplaar van de`Parser` class door het pad naar uw voorbeeldbestand op te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code voor extractie van tekstgebieden komt hier terecht
}
```
## Stap 2: Definieer opties voor tekstgebiedextractie
 Creëren`PageTextAreaOptions` om de criteria voor tekstextractie te specificeren.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
In dit voorbeeld:
- `"\\s[a-z]{2}\\s"` is een reguliere-expressiepatroon dat overeenkomt met tekstgebieden die alleen kleine letters bevatten.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definieert de rechthoek (positie en grootte) op de pagina waaruit tekst moet worden geëxtraheerd.
## Stap 3: Tekstgebieden extraheren
Gebruik de gedefinieerde opties om tekstgebieden te extraheren die aan de opgegeven criteria voldoen.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Stap 4: Controleer en herhaal de geëxtraheerde tekstgebieden
Controleer of extractie van tekstgebieden wordt ondersteund en herhaal vervolgens de geëxtraheerde gebieden.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Conclusie
In deze zelfstudie hebben we besproken hoe u tekst uit specifieke gebieden in een document kunt extraheren met GroupDocs.Parser voor .NET. Deze bibliotheek biedt uitgebreide mogelijkheden voor het parseren van verschillende documentformaten, waardoor het een waardevol hulpmiddel is voor tekstextractietaken.

## Veelgestelde vragen
### Kan GroupDocs.Parser tekst extraheren uit gescande documenten?
Ja, GroupDocs.Parser ondersteunt op OCR gebaseerde tekstextractie voor gescande documenten.
### Is GroupDocs.Parser compatibel met meerdere documentformaten?
Ja, het kan tekst ontleden en extraheren uit PDF, DOCX, XLSX, PPTX en andere populaire formaten.
### Biedt GroupDocs.Parser ondersteuning voor .NET Core?
Ja, GroupDocs.Parser is compatibel met .NET Core en .NET Framework.
### Kan ik metagegevens samen met tekst extraheren met GroupDocs.Parser?
Ja, u kunt zowel tekstuele inhoud als metagegevens uit documenten halen.
### Is er een proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt een gratis proefperiode krijgen van[hier](https://releases.groupdocs.com/).