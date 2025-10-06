---
title: Opgemaakte tekst uit document extraheren
linktitle: Opgemaakte tekst uit document extraheren
second_title: GroupDocs.Parser .NET API
description: Leer hoe u opgemaakte tekst uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Eenvoudige en efficiënte tekstextractie voor uw toepassingen.
weight: 10
url: /nl/net/formatted-text-extraction/extract-formatted-text-from-document/
type: docs
---
# Opgemaakte tekst uit document extraheren

## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om opgemaakte tekst uit verschillende soorten documenten te extraheren. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars op een vereenvoudigde en efficiënte manier met documenten kunnen werken. Aan het einde van deze handleiding kunt u de mogelijkheden voor tekstextractie naadloos integreren in uw .NET-toepassingen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
- Visual Studio: Zorg ervoor dat Visual Studio op uw systeem is geïnstalleerd.
-  GroupDocs.Parser voor .NET: Download en installeer de GroupDocs.Parser-bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
- Documentvoorbeelden: Bereid voorbeelddocumenten voor (bijvoorbeeld PDF, DOCX) voor tekstextractie.
## Naamruimten importeren
Neem eerst de benodigde naamruimten op in uw C#-code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Begin met het initialiseren van a`Parser` object met het pad naar uw voorbeelddocument.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tekstextractiecode komt hier terecht
}
```
 Vervangen`"YourSampleFile.pdf"` met het pad naar uw documentbestand.

## Stap 2: Opgemaakte tekst extraheren
 Binnen de`using` blokkeren, gebruik de`GetFormattedText` methode om opgemaakte tekst uit het document te extraheren. Geef het gewenste uitvoerformaat (bijvoorbeeld HTML) op met behulp van`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Extraheer opgemaakte tekst in de reader
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Controleer of extractie wordt ondersteund
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Lees en toon de geëxtraheerde tekst
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Conclusie
Gefeliciteerd! U hebt geleerd hoe u opgemaakte tekst uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Deze veelzijdige bibliotheek opent mogelijkheden voor tekstverwerking en analyse binnen uw applicaties.

## Veelgestelde vragen
### Vraag: Kan GroupDocs.Parser tekst extraheren uit met een wachtwoord beveiligde documenten?
A: Ja, GroupDocs.Parser ondersteunt het extraheren van tekst uit met een wachtwoord beveiligde documenten.
### Vraag: Welke documentformaten worden ondersteund door GroupDocs.Parser?
A: GroupDocs.Parser ondersteunt een breed scala aan formaten, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Vraag: Hoe kan ik een tijdelijke licentie krijgen voor GroupDocs.Parser?
 A: U kunt een tijdelijke licentie verkrijgen via[hier](https://purchase.groupdocs.com/temporary-license/).
### Vraag: Biedt GroupDocs.Parser ondersteuning voor het extraheren van afbeeldingen uit documenten?
A: Ja, GroupDocs.Parser ondersteunt zowel afbeeldingsextractie als tekstextractie.
### Vraag: Waar kan ik aanvullende ondersteuning vinden of vragen stellen over GroupDocs.Parser?
 A: Bezoek de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17)voor ondersteuning en discussies.