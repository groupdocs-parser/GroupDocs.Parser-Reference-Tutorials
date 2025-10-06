---
title: Werken met velden op vaste posities in sjablonen
linktitle: Werken met velden op vaste posities in sjablonen
second_title: GroupDocs.Parser .NET API
description: Leer hoe u gegevens uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Uitgebreide tutorial met codevoorbeelden.
weight: 11
url: /nl/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
type: docs
---
# Werken met velden op vaste posities in sjablonen

## Invoering
In deze zelfstudie onderzoeken we hoe u met velden op vaste posities binnen sjablonen kunt werken met behulp van GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige bibliotheek voor het parseren van documenten waarmee ontwikkelaars gegevens kunnen extraheren uit verschillende documentformaten zoals PDF, Word, Excel en meer. We zullen ons specifiek concentreren op het definiëren en gebruiken van sjabloonvelden om gerichte informatie te extraheren op basis van hun vaste posities.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Basiskennis van C# en .NET-ontwikkeling.
- Visual Studio is op uw systeem geïnstalleerd.
- GroupDocs.Parser voor .NET-bibliotheek geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/parser/net/).
- Voorbeelddocumentbestanden voor testen.

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
## Stap 1: Definieer een sjabloonveld
Definieer eerst een veld met een vaste positie binnen een sjabloon. Dit veld vertegenwoordigt het gebied waaruit gegevens worden geëxtraheerd.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Hier:
- `Rectangle` specificeert de positie en grootte van het veld.
- `Point(35, 135)` vertegenwoordigt de coördinaten in de linkerbovenhoek.
- `Size(100, 10)` definieert de breedte en hoogte van het veld.
- `"FromCompany"` is de naam die aan dit veld is toegewezen.
## Stap 2: Maak een sjabloon
Construeer een sjabloon met behulp van het gedefinieerde veld.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 De`Template` object bevat de gedefinieerde velden.
## Stap 3: Document parseren met behulp van de sjabloon
 Instantieer de`Parser` class met het doeldocumentpad en parseer vervolgens het document met behulp van de gemaakte sjabloon.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Herhaal de geëxtraheerde gegevens
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Hier:
- `Parser` wordt geïnitialiseerd met het voorbeelddocumentbestandspad.
- `ParseByTemplate` methode wordt gebruikt om gegevens te extraheren op basis van de meegeleverde sjabloon.
-  Geëxtraheerde gegevens zijn toegankelijk via`DocumentData`waarbij elk item overeenkomt met een gedefinieerd veld.

## Conclusie
In deze zelfstudie hebben we het proces besproken van het werken met velden op vaste posities in sjablonen met behulp van GroupDocs.Parser voor .NET. Door sjablonen met specifieke veldposities te definiëren, kunnen ontwikkelaars nauwkeurig gerichte gegevens uit verschillende documentformaten extraheren.

## Veelgestelde vragen
### Is GroupDocs.Parser compatibel met alle documentformaten?
 GroupDocs.Parser ondersteunt een breed scala aan bestandsindelingen, waaronder PDF, Microsoft Word, Excel, PowerPoint en meer. Verwijs naar de[documentatie](https://tutorials.groupdocs.com/parser/net/) voor een gedetailleerde lijst.
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 U kunt een tijdelijke licentie voor testdoeleinden verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik ondersteuning vinden voor GroupDocs.Parser?
 Voor technische assistentie en discussies kunt u terecht op de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).
### Kan ik GroupDocs.Parser uitproberen voordat ik een aankoop doe?
 Ja, u kunt de bibliotheek verkennen met een gratis proefversie[hier](https://releases.groupdocs.com/).
### Hoe koop ik een licentie voor GroupDocs.Parser?
 Om een licentie te kopen, gaat u naar de[aankooppagina](https://purchase.groupdocs.com/buy).