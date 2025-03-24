---
title: Document laden vanaf lokale schijf
linktitle: Document laden vanaf lokale schijf
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit verschillende documentformaten kunt extraheren met GroupDocs.Parser voor .NET. Gemakkelijke en efficiënte tekstextractie met C#.
weight: 11
url: /nl/net/document-loading/load-document-from-local-disk/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit documenten te extraheren. GroupDocs.Parser is een krachtige bibliotheek waarmee ontwikkelaars verschillende documentformaten kunnen parseren en tekstinhoud programmatisch kunnen extraheren. We bespreken de noodzakelijke stappen om aan de slag te gaan met tekstextractie met behulp van deze bibliotheek.
## Vereisten
Voordat we beginnen, zorg ervoor dat u de volgende vereisten hebt geïnstalleerd:
- Visual Studio is op uw systeem geïnstalleerd.
- Basiskennis van de programmeertaal C#.
-  GroupDocs.Parser voor .NET-bibliotheek geïnstalleerd (download[hier](https://releases.groupdocs.com/parser/net/)).

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Stap 1: Document laden vanaf lokale schijf
 Begin met het laden van een document vanaf uw lokale schijf. Vervangen`"Your Sample File"` met het pad naar uw doeldocument.
```csharp
// Stel het bestandspad in
string filePath = "Your Sample File";
// Maak een exemplaar van de Parser-klasse met de filePath
using (Parser parser = new Parser(filePath))
{
    // Extraheer tekst in de reader
    using (TextReader reader = parser.GetText())
    {
        //Druk de geëxtraheerde tekst uit het document af
        // Als tekstextractie niet wordt ondersteund, is de lezer null
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Uitleg van de stappen
1. Bestandspad instellen: begin met het opgeven van het pad naar het document waaruit u tekst wilt extraheren (`filePath` variabel).
2.  Parser-instantie maken: Instantie van de`Parser` klasse door het passeren van de`filePath`.
3.  Tekst extraheren: gebruik de`GetText()` werkwijze van de`Parser` bijvoorbeeld om een`TextReader` object dat de geëxtraheerde tekst uit het document bevat.
4.  Geëxtraheerde tekst lezen: gebruik de`ReadToEnd()` werkwijze van de`TextReader` om de volledige tekstinhoud uit het document op te halen.
5.  Omgaan met niet-ondersteunde formaten: Als het documentformaat geen tekstextractie ondersteunt, wordt het`reader` voorwerp zal zijn`null`, en u kunt dit scenario dienovereenkomstig afhandelen.

## Conclusie
In deze zelfstudie hebben we de eerste stappen besproken om tekst uit een document te extraheren met GroupDocs.Parser voor .NET. Deze bibliotheek biedt uitgebreide functies voor het parseren van documenten, waardoor ontwikkelaars binnen hun applicaties efficiënt met verschillende bestandsformaten kunnen werken.

## Veelgestelde vragen
### Is GroupDocs.Parser compatibel met alle documentformaten?
GroupDocs.Parser ondersteunt een breed scala aan formaten, waaronder PDF, Microsoft Office-documenten (Word, Excel, PowerPoint) en meer.
### Kan ik metagegevens samen met tekst extraheren met GroupDocs.Parser?
Ja, GroupDocs.Parser maakt extractie van zowel tekstinhoud als metagegevens uit ondersteunde documentformaten mogelijk.
### Waar kan ik meer bronnen en ondersteuning voor GroupDocs.Parser vinden?
 Bezoek de[GroupDocs.Parser-documentatie](https://tutorials.groupdocs.com/parser/net/) voor gedetailleerde API-referentie en verken de[GroupDocs-forum](https://forum.groupdocs.com/c/parser/17) voor gemeenschapssteun.
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 U kunt een aanvraag indienen voor een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) voor evaluatie- en testdoeleinden.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt een downloaden[gratis proefperiode](https://releases.groupdocs.com/) versie van GroupDocs.Parser.