---
title: Extraheer tekst uit een Word-document
linktitle: Extraheer tekst uit een Word-document
second_title: GroupDocs.Parser .NET API
description: Leer hoe u tekst uit Word-documenten kunt extraheren met GroupDocs.Parser voor .NET. Stapsgewijze handleiding met codevoorbeelden.
weight: 15
url: /nl/net/word-document-processing/extract-text-from-word-document/
---

# Extraheer tekst uit een Word-document

## Invoering
In deze zelfstudie onderzoeken we hoe u tekst uit Word-documenten kunt extraheren met GroupDocs.Parser voor .NET. GroupDocs.Parser is een krachtige .NET-bibliotheek waarmee ontwikkelaars met verschillende documentformaten kunnen werken, waaronder Word-documenten, PDF's en meer. Aan het einde van deze handleiding kunt u efficiënt tekst uit Word-bestanden extraheren met behulp van eenvoudige C#-code.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
- Visual Studio (of een andere C#-ontwikkelomgeving van uw voorkeur)
- GroupDocs.Parser voor .NET-bibliotheek geïnstalleerd (Download[hier](https://releases.groupdocs.com/parser/net/))
- Basiskennis van programmeren in C#

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren om toegang te krijgen tot de GroupDocs.Parser-functionaliteit.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Stap 1: Maak een exemplaar van de parserklasse
 Begin met het maken van een exemplaar van de`Parser` klasse, met het pad naar uw Word-document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Uw code voor tekstextractie komt hier terecht
}
```
 Vervangen`"YourSampleFile.docx"` met het pad naar uw daadwerkelijke Word-document.
## Stap 2: Extraheer tekst in een tekstlezer
 Binnen de`using` blok van de`Parser` Gebruik bijvoorbeeld de`GetText()` methode om de tekstinhoud te extraheren in een`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    // Uw tekstverwerkingscode komt hier terecht
}
```
## Stap 3: Geëxtraheerde tekst lezen en weergeven
 Nu, binnen de`TextReader` blok kunt u de geëxtraheerde tekst uit het Word-document lezen en afdrukken.
```csharp
using (TextReader reader = parser.GetText())
{
    // Lees de geëxtraheerde tekst en druk deze af
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusie
Gefeliciteerd! U hebt geleerd hoe u tekst uit Word-documenten kunt extraheren met GroupDocs.Parser voor .NET. Met deze eenvoudige maar krachtige bibliotheek kunt u tekstextractiemogelijkheden efficiënt in uw .NET-toepassingen integreren.

## Veelgestelde vragen
### Is GroupDocs.Parser compatibel met alle versies van .NET?
Ja, GroupDocs.Parser voor .NET is compatibel met .NET Framework 4.6.1 en latere versies.
### Kan ik tekst extraheren uit gecodeerde of met een wachtwoord beveiligde Word-documenten?
GroupDocs.Parser ondersteunt het extraheren van tekst uit met een wachtwoord beveiligde Word-documenten.
### Ondersteunt GroupDocs.Parser naast Word-documenten ook andere documentformaten?
Ja, GroupDocs.Parser ondersteunt een breed scala aan documentformaten, waaronder PDF, Excel, PowerPoint en meer.
### Hoe kan ik een tijdelijke licentie voor GroupDocs.Parser verkrijgen?
 U kunt een tijdelijke licentie aanvragen voor GroupDocs.Parser[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik aanvullende ondersteuning vinden of vragen stellen over GroupDocs.Parser?
 U kunt het GroupDocs.Parser-forum bezoeken[hier](https://forum.groupdocs.com/c/parser/17)voor ondersteuning en discussies.