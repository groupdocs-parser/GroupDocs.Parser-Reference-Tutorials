---
title: Document laden vanaf URL
linktitle: Document laden vanaf URL
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit documenten kunt extraheren met GroupDocs.Parser voor .NET. Deze tutorial behandelt stap voor stap het laden van een document vanaf een URL en het extraheren van tekst.
type: docs
weight: 13
url: /nl/net/document-loading/load-document-from-url/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u GroupDocs.Parser voor .NET kunt gebruiken om tekst uit documenten te extraheren. GroupDocs.Parser is een krachtig hulpmiddel voor het extraheren van tekst, metagegevens en andere informatie uit verschillende documentformaten, zoals PDF, Word, Excel en meer. We behandelen stap voor stap het proces van het laden van een document vanaf een URL en het extraheren van de tekstinhoud.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1. Visual Studio: Installeer Visual Studio op uw systeem.
2.  GroupDocs.Parser voor .NET: Download en installeer GroupDocs.Parser voor .NET vanaf de[downloadpagina](https://releases.groupdocs.com/parser/net/).
3. Basiskennis van C#: Bekendheid met de programmeertaal C#.

## Naamruimten importeren
Begin met het opnemen van de benodigde naamruimten in uw C#-code:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Eerst laten we zien hoe u een document vanaf een URL kunt laden en de tekstinhoud ervan kunt extraheren.
## Stap 1: Geef de document-URL op
Geef de URL op van het document waaruit u tekst wilt extraheren:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Stap 2: Maak een parserinstantie
 Instantieer de`Parser` klasse met de document-URL:
```csharp
using (Parser parser = new Parser(uri))
{
    // Je code komt hier
}
```
## Stap 3: Extraheer tekst uit het document
 Binnen in de`using`blokkeren, gebruiken`parser.GetText()` om tekst uit het document te extraheren:
```csharp
using (TextReader reader = parser.GetText())
{
    // Je code komt hier
}
```
## Stap 4: Geef de geëxtraheerde tekst weer
Lees en druk de geëxtraheerde tekst uit het document af:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Conclusie
In deze zelfstudie hebben we de basisbeginselen besproken van het extraheren van tekst uit een document met GroupDocs.Parser voor .NET. Door deze stappen te volgen, kunt u eenvoudig de mogelijkheden voor documenttekstextractie integreren in uw C#-toepassingen.

## Veelgestelde vragen
### Is GroupDocs.Parser compatibel met verschillende documentformaten?
Ja, GroupDocs.Parser ondersteunt een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer.
### Kan ik metagegevens samen met tekst extraheren met GroupDocs.Parser?
Ja, met GroupDocs.Parser kunt u metagegevens, tekst en andere informatie uit documenten extraheren.
### Is er een proefversie beschikbaar voor GroupDocs.Parser?
 Ja, u kunt een gratis proefversie van GroupDocs.Parser downloaden[hier](https://releases.groupdocs.com/).
### Waar kan ik documentatie voor GroupDocs.Parser vinden?
 Er is gedetailleerde documentatie voor GroupDocs.Parser beschikbaar[hier](https://reference.groupdocs.com/parser/net/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Parser?
 kunt technische ondersteuning zoeken en vragen stellen op het GroupDocs.Parser-forum[hier](https://forum.groupdocs.com/c/parser/17).