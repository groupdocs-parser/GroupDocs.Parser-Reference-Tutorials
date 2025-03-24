---
title: Tabellen uit document extraheren
linktitle: Tabellen uit document extraheren
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tabellen uit documenten kunt extraheren met Groupdocs.Parser voor .NET. Volg ons voor een gedetailleerde handleiding over het integreren van deze functionaliteit.
weight: 10
url: /nl/net/table-extraction/extract-tables-from-document/
---

# Tabellen uit document extraheren

## Invoering
Groupdocs.Parser voor .NET is een uitgebreide bibliotheek die het parseren van documenten vergemakkelijkt, waardoor u waardevolle informatie zoals tabellen, tekst, metagegevens en meer uit documenten kunt extraheren. In deze zelfstudie richten we ons specifiek op het extraheren van tabellen uit documenten met behulp van de Groupdocs.Parser API.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Visual Studio is op uw systeem geïnstalleerd.
- .NET Framework of .NET Core geïnstalleerd.
- Basiskennis van programmeren in C#.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten importeren om toegang te krijgen tot de Groupdocs.Parser-klassen en -methoden.
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
 Initialiseer een nieuw exemplaar van het`Parser` klasse door het pad naar uw voorbeelddocument op te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Je code komt hier
}
```
## Stap 2: Controleer de ondersteuning voor tabelextractie
 Controleer of het document tabelextractie ondersteunt met behulp van de`Features` eigendom van de`Parser` klas.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Stap 3: Definieer de tabelindeling
Definieer de lay-out van de tabellen die u wilt extraheren`TemplateTableLayout`. Geef kolombreedtes en rijhoogtes op op basis van de structuur van uw document.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Stap 4: Stel opties voor tabelextractie in
 Creëren`PageTableAreaOptions` met de gedefinieerde lay-out om te specificeren hoe tabellen moeten worden geëxtraheerd.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Stap 5: Tabellen extraheren
 Maak gebruik van de`GetTables` werkwijze van de`Parser` class om tabellen uit het document te extraheren op basis van de opgegeven opties.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Stap 6: Tabelgegevens herhalen en openen
Blader door de geëxtraheerde tabellen en hun respectievelijke rijen en kolommen om toegang te krijgen tot celgegevens.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Conclusie
In deze zelfstudie hebben we besproken hoe u Groupdocs.Parser voor .NET kunt gebruiken om tabellen efficiënt uit documenten te extraheren. Door gebruik te maken van de mogelijkheden van deze bibliotheek kunt u tabelextractie naadloos integreren in uw .NET-toepassingen.

## Veelgestelde vragen
### Kan Groupdocs.Parser verschillende documentformaten verwerken?
Ja, Groupdocs.Parser ondersteunt een breed scala aan documentformaten, waaronder DOCX, PDF, XLSX en meer.
### Is er een proefversie beschikbaar voor Groupdocs.Parser voor .NET?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor Groupdocs.Parser-gerelateerde vragen?
 U kunt een bezoek brengen aan de[Groupdocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) Voor assistentie.
### Waar kan ik een licentie voor Groupdocs.Parser kopen?
 U kunt een licentie kopen bij[hier](https://purchase.groupdocs.com/buy).
### Hoe kan ik een tijdelijke licentie verkrijgen voor evaluatiedoeleinden?
 U kunt een tijdelijke licentie verkrijgen[hier](https://purchase.groupdocs.com/temporary-license/).