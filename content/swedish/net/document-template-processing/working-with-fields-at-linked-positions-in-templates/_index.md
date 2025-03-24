---
title: Arbeta med fält på länkade positioner i mallar
linktitle: Arbeta med fält på länkade positioner i mallar
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar data effektivt från dokument med GroupDocs.Parser för .NET. Steg-för-steg handledning med kodexempel.
weight: 12
url: /sv/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## Introduktion
GroupDocs.Parser för .NET är ett robust bibliotek designat för att underlätta dokumentanalys och dataextrahering. Den stöder ett brett utbud av filformat, inklusive PDF, DOCX, XLSX och mer. En av dess nyckelfunktioner är mallbaserad dataextraktion, som låter dig definiera fält i ett dokument och extrahera specifik data baserat på dessa fördefinierade mallar.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Grundläggande förståelse för C#-programmering
- Visual Studio installerat på ditt system
-  GroupDocs.Parser för .NET-bibliotek (ladda ner från[här](https://releases.groupdocs.com/parser/net/))
- Exempel på dokumentfiler att arbeta med

## Importera namnområden
Börja med att inkludera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Steg 1: Definiera mallfält
Definiera först mallfälten med reguljära uttryck och länkade positioner:
```csharp
// Definiera ett fält med ett reguljärt uttryck
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Definiera ett länkat fält med specifika positionsinställningar
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Steg 2: Skapa en mall
Skapa sedan en mall som innehåller de definierade fälten:
```csharp
// Skapa en mall med de definierade fälten
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Steg 3: Analysera dokument med mall
 Initiera nu`Parser` klass och analysera dokumentet med mallen:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analysera dokumentet efter mallen
    DocumentData data = parser.ParseByTemplate(template);
    // Iterera genom extraherade data och skriv ut resultat
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Slutsats
GroupDocs.Parser för .NET förenklar processen att extrahera strukturerad data från dokument med hjälp av mallar. Genom att definiera fält och använda mallar kan du effektivt extrahera relevant information, vilket förbättrar automatiseringen och produktiviteten i dokumentbearbetningsuppgifter.

## FAQ's
### Kan GroupDocs.Parser extrahera data från krypterade PDF-filer?
Ja, GroupDocs.Parser stöder analys av krypterade PDF-filer genom att ange lösenordet under analysen.
### Vilka filformat stöds för mallbaserad extrahering?
GroupDocs.Parser stöder ett brett utbud av filformat inklusive PDF, DOCX, XLSX, PPTX, TXT och mer.
### Finns det en testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Kan jag använda GroupDocs.Parser för batchbehandling av dokument?
Ja, GroupDocs.Parser tillåter batchbearbetning för att analysera flera dokument samtidigt.
### Var kan jag få teknisk support för GroupDocs.Parser?
 Du kan söka teknisk support och engagera dig i samhället på[GroupDocs forum](https://forum.groupdocs.com/c/parser/17).