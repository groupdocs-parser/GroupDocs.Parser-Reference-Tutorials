---
title: Werken met velden op gekoppelde posities in sjablonen
linktitle: Werken met velden op gekoppelde posities in sjablonen
second_title: GroupDocs.Parser .NET API
description: Leer hoe u gegevens efficiënt uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Stapsgewijze zelfstudie met codevoorbeelden.
weight: 12
url: /nl/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# Werken met velden op gekoppelde posities in sjablonen

## Invoering
GroupDocs.Parser voor .NET is een robuuste bibliotheek die is ontworpen om het parseren van documenten en gegevensextractietaken te vergemakkelijken. Het ondersteunt een breed scala aan bestandsformaten, waaronder PDF, DOCX, XLSX en meer. Een van de belangrijkste functies is op sjablonen gebaseerde gegevensextractie, waarmee u velden binnen een document kunt definiëren en specifieke gegevens kunt extraheren op basis van deze vooraf gedefinieerde sjablonen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Basiskennis van programmeren in C#
- Visual Studio is op uw systeem geïnstalleerd
-  GroupDocs.Parser voor .NET-bibliotheek (downloaden van[hier](https://releases.groupdocs.com/parser/net/))
- Voorbeelddocumentbestanden om mee te werken

## Naamruimten importeren
Begin met het opnemen van de benodigde naamruimten in uw C#-project:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Stap 1: Definieer sjabloonvelden
Definieer eerst de sjabloonvelden met behulp van reguliere expressies en gekoppelde posities:
```csharp
// Definieer een veld met een reguliere expressie
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Definieer een gekoppeld veld met specifieke positie-instellingen
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Stap 2: Maak een sjabloon
Maak vervolgens een sjabloon met de gedefinieerde velden:
```csharp
// Maak een sjabloon met de gedefinieerde velden
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Stap 3: Document analyseren met sjabloon
 Initialiseer nu de`Parser` class en parseer het document met behulp van de sjabloon:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Parseer het document op basis van de sjabloon
    DocumentData data = parser.ParseByTemplate(template);
    // Herhaal de geëxtraheerde gegevens en printresultaten
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusie
GroupDocs.Parser voor .NET vereenvoudigt het proces van het extraheren van gestructureerde gegevens uit documenten met behulp van sjablonen. Door velden te definiëren en sjablonen toe te passen, kunt u op efficiënte wijze relevante informatie extraheren, waardoor de automatisering en productiviteit bij documentverwerkingstaken wordt verbeterd.

## Veelgestelde vragen
### Kan GroupDocs.Parser gegevens extraheren uit gecodeerde PDF-bestanden?
Ja, GroupDocs.Parser ondersteunt het parseren van gecodeerde PDF-bestanden door tijdens het parseren het wachtwoord op te geven.
### Welke bestandsformaten worden ondersteund voor op sjablonen gebaseerde extractie?
GroupDocs.Parser ondersteunt een breed scala aan bestandsformaten, waaronder PDF, DOCX, XLSX, PPTX, TXT en meer.
### Is er een proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Kan ik GroupDocs.Parser gebruiken voor batchverwerking van documenten?
Ja, GroupDocs.Parser maakt batchverwerking mogelijk om meerdere documenten gelijktijdig te parseren.
### Waar kan ik technische ondersteuning krijgen voor GroupDocs.Parser?
 U kunt technische ondersteuning zoeken en in contact komen met de community op[GroupDocs-forum](https://forum.groupdocs.com/c/parser/17).