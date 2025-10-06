---
title: Document uit stroom laden
linktitle: Document uit stroom laden
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit verschillende documentformaten in .NET kunt extraheren met GroupDocs.Parser. Stapsgewijze handleiding met codevoorbeelden.
weight: 12
url: /nl/net/document-loading/load-document-from-stream/
type: docs
---
# Document uit stroom laden

## Invoering
Op het gebied van documentverwerking in .NET-toepassingen is het extraheren van tekst uit verschillende bestandsformaten een veel voorkomende vereiste. GroupDocs.Parser voor .NET biedt een krachtige oplossing voor het naadloos parseren en extraheren van tekst uit een breed scala aan documenten. Deze tutorial begeleidt u stap voor stap bij het gebruik van GroupDocs.Parser om tekst uit documenten te extraheren.
## Vereisten
Voordat u GroupDocs.Parser voor .NET gaat gebruiken, moet u ervoor zorgen dat u het volgende hebt ingesteld:
- Ontwikkelomgeving: Visual Studio of een andere .NET-ontwikkelomgeving.
-  GroupDocs.Parser voor .NET-pakket: download en installeer de GroupDocs.Parser voor .NET-bibliotheek van[hier](https://releases.groupdocs.com/parser/net/).
- Documentvoorbeelden: zorg ervoor dat u voorbeelddocumenten gereed hebt voor tekstextractie.
## Naamruimten importeren
Begin met het importeren van de benodigde naamruimten in uw .NET-project om toegang te krijgen tot de functionaliteiten van GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

De volgende stappen laten zien hoe u tekst uit een document kunt extraheren met GroupDocs.Parser uit een stream.
## Stap 1: Document uit stream laden
```csharp
// Maak de stroom
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Maak een exemplaar van de Parser-klasse met de stream
    using (Parser parser = new Parser(stream))
    {
        // Extraheer tekst in de reader
        using (TextReader reader = parser.GetText())
        {
            // Tekst uit het document afdrukken
            // Als tekstextractie niet wordt ondersteund, is de lezer null
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
In dit voorbeeld:
- We openen een bestandsstroom voor het documentbestand (`YourSampleFile.docx`).
-  Initialiseer een`Parser` bijvoorbeeld met de stream.
-  Gebruik`parser.GetText()` om een op te halen`TextReader` met de geëxtraheerde tekst.
- Druk de geëxtraheerde tekst of een bericht af als tekstextractie niet wordt ondersteund voor de documentindeling.
## Conclusie
GroupDocs.Parser voor .NET vereenvoudigt de tekstextractie uit verschillende documentformaten, waardoor ontwikkelaars tekstuele inhoud efficiënt kunnen verwerken en gebruiken in hun applicaties. Door de stappen in deze zelfstudie te volgen, kunt u de extractiemogelijkheden van documenttekst naadloos integreren in uw .NET-projecten.

## Veelgestelde vragen
### Welke documentformaten worden ondersteund door GroupDocs.Parser voor .NET?
GroupDocs.Parser ondersteunt een breed scala aan documentformaten, waaronder DOCX, PDF, XLSX, PPTX, EPUB en meer.
### Kan GroupDocs.Parser afbeeldingen of metagegevens uit documenten extraheren?
Ja, GroupDocs.Parser kan afbeeldingen, metagegevens en tekst uit verschillende documenttypen extraheren.
### Is GroupDocs.Parser compatibel met .NET Core-applicaties?
Ja, GroupDocs.Parser is compatibel met zowel .NET Framework- als .NET Core-applicaties.
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 Een tijdelijke licentie kunt u verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik meer ondersteuning of documentatie vinden voor GroupDocs.Parser?
 Voor aanvullende ondersteuning kunt u terecht op de[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17) of raadpleeg de[documentatie](https://tutorials.groupdocs.com/parser/net/).
