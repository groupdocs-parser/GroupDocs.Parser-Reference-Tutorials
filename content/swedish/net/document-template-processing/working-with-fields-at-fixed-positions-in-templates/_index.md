---
title: Arbeta med fält på fasta positioner i mallar
linktitle: Arbeta med fält på fasta positioner i mallar
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar data från dokument med GroupDocs.Parser för .NET. Omfattande handledning med kodexempel.
weight: 11
url: /sv/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# Arbeta med fält på fasta positioner i mallar

## Introduktion
I den här handledningen kommer vi att utforska hur man arbetar med fält på fasta positioner inom mallar med hjälp av GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt dokumentanalysbibliotek som gör det möjligt för utvecklare att extrahera data från olika dokumentformat som PDF, Word, Excel och mer. Specifikt kommer vi att fokusera på att definiera och använda mallfält för att extrahera riktad information baserat på deras fasta positioner.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Grundläggande förståelse för C# och .NET utveckling.
- Visual Studio installerat på ditt system.
- GroupDocs.Parser för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
- Exempel på dokumentfiler för testning.

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
## Steg 1: Definiera ett mallfält
Definiera först ett fält med en fast position i en mall. Detta fält representerar området från vilket data kommer att extraheras.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Här:
- `Rectangle` anger fältets position och storlek.
- `Point(35, 135)` representerar koordinaterna i det övre vänstra hörnet.
- `Size(100, 10)` definierar fältets bredd och höjd.
- `"FromCompany"` är namnet som tilldelats detta fält.
## Steg 2: Skapa en mall
Konstruera en mall med det definierade fältet.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 De`Template` objektet innehåller de definierade fälten.
## Steg 3: Analysera dokument med hjälp av mallen
 Instantiera`Parser` klass med måldokumentets sökväg och analysera sedan dokumentet med den skapade mallen.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterera genom extraherade data
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Här:
- `Parser` initieras med sökvägen till exempeldokumentfilen.
- `ParseByTemplate` metod används för att extrahera data baserat på den tillhandahållna mallen.
-  Extraherade data nås med hjälp av`DocumentData`där varje objekt motsvarar ett definierat fält.

## Slutsats
I den här handledningen täckte vi processen att arbeta med fält på fasta positioner i mallar med hjälp av GroupDocs.Parser för .NET. Genom att definiera mallar med specifika fältpositioner kan utvecklare extrahera riktad data exakt från olika dokumentformat.

## FAQ's
### Är GroupDocs.Parser kompatibel med alla dokumentformat?
 GroupDocs.Parser stöder ett brett utbud av filformat, inklusive PDF, Microsoft Word, Excel, PowerPoint och mer. Referera till[dokumentation](https://tutorials.groupdocs.com/parser/net/) för en detaljerad lista.
### Hur kan jag få en tillfällig licens för GroupDocs.Parser?
 Du kan få en tillfällig licens för teständamål från[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag hitta support för GroupDocs.Parser?
 För teknisk hjälp och diskussioner, besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).
### Kan jag prova GroupDocs.Parser innan jag köper?
 Ja, du kan utforska biblioteket med en gratis provperiod tillgänglig[här](https://releases.groupdocs.com/).
### Hur köper jag en licens för GroupDocs.Parser?
 För att köpa en licens, besök[köpsidan](https://purchase.groupdocs.com/buy).