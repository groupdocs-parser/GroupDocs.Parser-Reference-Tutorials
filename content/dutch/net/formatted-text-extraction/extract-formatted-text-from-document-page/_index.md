---
title: Extraheer opgemaakte tekst uit de documentpagina
linktitle: Extraheer opgemaakte tekst uit de documentpagina
second_title: GroupDocs.Parser .NET API
description: Extraheer opgemaakte tekst uit documentpagina's met GroupDocs.Parser voor .NET. Efficiënte en betrouwbare oplossing voor tekstextractie.
type: docs
weight: 11
url: /nl/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Invoering
In deze zelfstudie begeleiden we u bij het extraheren van opgemaakte tekst uit documentpagina's met behulp van GroupDocs.Parser voor .NET. Met deze bibliotheek kunt u tekst efficiënt ontleden en extraheren uit verschillende documentformaten, zoals PDF, Word, Excel en meer.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Visual Studio is op uw systeem geïnstalleerd.
- Basiskennis van programmeren in C#.
-  GroupDocs.Parser voor .NET-bibliotheek. Je kunt het downloaden[hier](https://releases.groupdocs.com/parser/net/).

## Naamruimten importeren
Begin eerst met het importeren van de benodigde naamruimten in uw C#-project.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Begin met het maken van een exemplaar van de`Parser` class door het pad naar uw voorbeeldbestand op te geven.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code komt hier terecht
}
```
## Stap 2: Controleer of geformatteerde tekstextractie wordt ondersteund
Voordat u doorgaat met tekstextractie, controleert u of het document geformatteerde tekstextractie ondersteunt.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Stap 3: Documentinformatie ophalen
Haal informatie op over het document, zoals het aantal pagina's.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Stap 4: Herhaal de documentpagina's en extraheer de opgemaakte tekst
Blader door elke pagina van het document en extraheer opgemaakte tekst met behulp van de opgegeven opties (bijvoorbeeld Markdown-indeling).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusie
Nu weet u hoe u opgemaakte tekst uit documentpagina's kunt extraheren met GroupDocs.Parser voor .NET. Deze bibliotheek biedt een krachtige en gebruiksvriendelijke oplossing voor tekstextractie uit verschillende bestandsformaten.

## Veelgestelde vragen
### Kan GroupDocs.Parser verschillende bestandsformaten verwerken?
Ja, GroupDocs.Parser ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Is GroupDocs.Parser compatibel met .NET Core?
Ja, GroupDocs.Parser ondersteunt .NET Core en .NET Framework.
### Behoudt GroupDocs.Parser de tekstopmaak tijdens het uitpakken?
Ja, GroupDocs.Parser kan opmaak zoals stijlen en lettertypen behouden bij het extraheren van tekst.
### Kan ik afbeeldingen en metagegevens extraheren met GroupDocs.Parser?
Ja, GroupDocs.Parser maakt het extraheren van afbeeldingen, metagegevens en tekst uit documenten mogelijk.
### Hoe kan ik ondersteuning krijgen voor GroupDocs.Parser?
 U kunt ondersteuning krijgen van de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).