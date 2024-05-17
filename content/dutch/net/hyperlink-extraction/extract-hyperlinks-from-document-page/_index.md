---
title: Extraheer hyperlinks uit de documentpagina
linktitle: Extraheer hyperlinks uit de documentpagina
second_title: GroupDocs.Parser .NET API
description: Leer hoe u hyperlinks uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Stapsgewijze handleiding voor het extraheren van hyperlinks in C#.
type: docs
weight: 11
url: /nl/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Invoering
In deze zelfstudie onderzoeken we stap voor stap hoe u GroupDocs.Parser voor .NET kunt gebruiken om hyperlinks uit documenten te extraheren. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars verschillende documentformaten kunnen parseren en tekst, metagegevens en andere elementen kunnen extraheren.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Visual Studio: Installeer Visual Studio op uw ontwikkelmachine.
-  GroupDocs.Parser-bibliotheek: download en raadpleeg de GroupDocs.Parser-bibliotheek. Je kunt het krijgen van[hier](https://releases.groupdocs.com/parser/net/).
- Voorbeelddocument: Bereid een voorbeelddocument voor (bijv. DOCX, PDF) met hyperlinks voor testen.

## Naamruimten importeren
Voeg eerst de benodigde naamruimten toe om de GroupDocs.Parser-functionaliteiten te gebruiken:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Stap 1: Parser-instantie maken
 Instantieer de`Parser` class met het pad naar uw voorbeelddocument.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code komt hier...
}
```
## Stap 2: Controleer de ondersteuning voor hyperlinkextractie
Zorg ervoor dat het document het extraheren van hyperlinks ondersteunt voordat u verdergaat.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Stap 3: Documentinformatie ophalen
Krijg basisinformatie over het document en controleer of het pagina's bevat.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Stap 4: herhaal de documentpagina's
Blader door elke pagina van het document.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraheer hyperlinks van de huidige pagina
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Herhaal de geëxtraheerde hyperlinks
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Lege regel voor leesbaarheid
    }
}
```

## Conclusie
In deze zelfstudie hebben we de basisbeginselen besproken van het gebruik van GroupDocs.Parser voor .NET om hyperlinks uit documenten te extraheren. U hebt geleerd hoe u de parser initialiseert, controleert op ondersteuning voor hyperlinks, documentinformatie ophaalt en door documentpagina's bladert om hyperlinks efficiënt te extraheren.

## Veelgestelde vragen
### Kan ik hyperlinks uit verschillende documentformaten extraheren?
Ja, GroupDocs.Parser ondersteunt verschillende formaten zoals DOCX, PDF, PPTX, enz., voor het extraheren van hyperlinks.
### Is GroupDocs.Parser eenvoudig te integreren in bestaande .NET-applicaties?
Absoluut, GroupDocs.Parser is ontworpen om eenvoudig te zijn en kan eenvoudig worden geïntegreerd in uw .NET-projecten.
### Kan ik andere metagegevens samen met hyperlinks extraheren met GroupDocs.Parser?
Ja, naast hyperlinks kunt u met deze bibliotheek ook tekst, afbeeldingen en metagegevens uit documenten extraheren.
### Verwerkt GroupDocs.Parser gecodeerde of met een wachtwoord beveiligde documenten?
GroupDocs.Parser kan met een wachtwoord beveiligde documenten parseren als het wachtwoord wordt opgegeven.
### Is er een proefversie beschikbaar om te testen voordat u deze aanschaft?
 Ja, u kunt een gratis proefversie downloaden[hier](https://releases.groupdocs.com/).