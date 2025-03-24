---
title: Haal tabellen uit de documentpagina
linktitle: Haal tabellen uit de documentpagina
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tabellen programmatisch uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Deze uitgebreide tutorial biedt stapsgewijze begeleiding.
weight: 11
url: /nl/net/table-extraction/extract-tables-from-document-page/
---

# Haal tabellen uit de documentpagina

## Invoering
In deze zelfstudie onderzoeken we hoe u tabellen uit een documentpagina kunt extraheren met GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars met verschillende documentformaten kunnen werken, zoals PDF, DOCX, XLSX en meer. Door gebruik te maken van de functies ervan kunnen we op efficiënte wijze gestructureerde gegevens zoals tabellen uit deze documenten extraheren, waardoor we de informatie programmatisch kunnen manipuleren en analyseren.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u begint:
- Visual Studio is op uw computer geïnstalleerd.
- Basiskennis van C# en .NET-ontwikkeling.
-  GroupDocs.Parser voor .NET-bibliotheek. Je kunt het downloaden van[hier](https://releases.groupdocs.com/parser/net/).
- Toegang tot een voorbeelddocument (PDF, DOCX, enz.) met tabellen voor extractie.

## Naamruimten importeren
Begin eerst met het importeren van de benodigde naamruimten in uw C#-project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Instantieer de`Parser` klasse door het pad naar uw voorbeelddocument op te geven:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Uw code gaat hier verder...
}
```
## Stap 2: Controleer de ondersteuning voor het extraheren van documenttabellen
Voordat u doorgaat, controleert u of het document tabelextractie ondersteunt:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Stap 3: Definieer de tabelindeling
Definieer de lay-out van de tabellen die uit het document moeten worden geëxtraheerd. Geef kolombreedtes en rijhoogtes op volgens de structuur van uw document:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Kolombreedtes
    new double[] { 325, 340, 365, 395 });         // Rij hoogten
```
## Stap 4: Configureer opties voor tabelextractie
Creëer opties voor tabelextractie met behulp van de opgegeven lay-out:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Stap 5: Documentinformatie ophalen
Informatie over het document ophalen, inclusief het aantal pagina's:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Stap 6: herhaal de documentpagina's
Blader door elke pagina van het document om tabellen te extraheren:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraheer tabellen van de huidige pagina
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Herhaal de geëxtraheerde tabellen
    foreach (PageTableArea table in tables)
    {
        // Herhaal de rijen van de tabel
        for (int row = 0; row < table.RowCount; row++)
        {
            // Herhaal de kolommen van de tabel
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Haal de tabelcel op
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Druk de tekst van de tabelcel af
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Conclusie
In deze zelfstudie hebben we het proces besproken van het extraheren van tabellen uit documentpagina's met behulp van GroupDocs.Parser voor .NET. Door de aangegeven stappen te volgen, kunt u de functionaliteit voor het extraheren van tabellen naadloos integreren in uw .NET-toepassingen, waardoor een efficiënte verwerking en manipulatie van gestructureerde gegevens in documenten mogelijk wordt.

## Veelgestelde vragen
### Kan GroupDocs.Parser tabellen extraheren uit alle soorten documenten?
GroupDocs.Parser ondersteunt verschillende documentformaten zoals PDF, DOCX, XLSX en meer, waardoor tabelextractie uit compatibele bestandstypen mogelijk wordt.
### Is GroupDocs.Parser voor .NET geschikt voor grootschalige documentverwerking?
Ja, GroupDocs.Parser is ontworpen om grote documenten efficiënt te verwerken, waardoor het geschikt is voor het verwerken van uitgebreide datasets.
### Behoudt GroupDocs.Parser de opmaak tijdens het extraheren van tabellen?
Ja, GroupDocs.Parser behoudt opmaakdetails zoals celranden, tekststijlen en uitlijningen tijdens het extraheren van tabellen.
### Kan ik specifieke tabellen extraheren op basis van inhoudscriteria?
GroupDocs.Parser biedt flexibele opties om specifieke tabellen te targeten op basis van lay-outsjablonen of inhoudsvoorwaarden voor extractie.
### Is GroupDocs.Parser compatibel met .NET Core?
Ja, GroupDocs.Parser is compatibel met zowel .NET Framework- als .NET Core-omgevingen.