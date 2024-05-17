---
title: Iterera genom fält
linktitle: Iterera genom fält
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar strukturerad data från dokument med GroupDocs.Parser för .NET. Förbättra dina .NET-applikationer med extraheringsmöjligheter för dokumentdata.
type: docs
weight: 11
url: /sv/net/data-extraction-from-templates/iterate-through-fields/
---
## Introduktion
GroupDocs.Parser för .NET är ett kraftfullt bibliotek som låter utvecklare extrahera data från olika dokumentformat som PDF, Microsoft Word, Excel och PowerPoint. Denna handledning guidar dig genom processen att använda GroupDocs.Parser för att iterera genom dokumentfält och extrahera specifik data med hjälp av mallar. I slutet av denna handledning kommer du att effektivt kunna extrahera strukturerad data från dokument i dina .NET-applikationer.
## Förutsättningar
Innan vi börjar, se till att du har ställt in följande förutsättningar:
- Grundläggande kunskaper i C#-programmering.
- Visual Studio installerat på din dator.
- GroupDocs.Parser för .NET-biblioteket installerat och refererat till i ditt projekt.

## Importera namnområden
För att komma igång, lägg till de nödvändiga namnområdena till din C#-fil:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Låt oss dela upp processen i steg-för-steg-instruktioner.
## Steg 1: Definiera mallfält
Först definierar du fälten du vill extrahera från dokumentet med hjälp av reguljära uttryck.
```csharp
// Definiera ett "pris"-fält
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Definiera ett "e-post"-fält
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Skapa en mall med definierade fält
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
det här steget har vi definierat två fält: ett för att extrahera priser (identifieras med dollartecknet och siffror) och ett annat för att extrahera e-postadresser.
## Steg 2: Analysera dokumentet
 Använd sedan`Parser` klass för att analysera dokumentet med den definierade mallen.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analysera dokumentet efter mallen
    DocumentData data = parser.ParseByTemplate(template);
    // Iterera genom extraherade data
    for (int i = 0; i < data.Count; i++)
    {
        // Skriv ut fältnamn
        Console.Write(data[i].Name + ": ");
        // Kontrollera om det extraherade området är text
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Här initierar vi`Parser` med sökvägen till ditt exempeldokument och analysera sedan dokumentet med den definierade mallen. Vi itererar sedan igenom de extraherade uppgifterna och skriver ut fältnamnen tillsammans med den extraherade texten.
## Slutsats
I den här handledningen har vi utforskat hur man använder GroupDocs.Parser för .NET för att extrahera specifik data från dokument med hjälp av mallar. Genom att utnyttja reguljära uttryck och mallar kan du effektivt extrahera strukturerad information från olika dokumentformat. Experimentera med olika mallar och dokumenttyper för att passa dina specifika extraheringsbehov.

## FAQ's
### Kan GroupDocs.Parser extrahera data från skannade dokument?
Ja, GroupDocs.Parser kan extrahera text och metadata från både skannade och sökbara PDF-dokument.
### Är GroupDocs.Parser kompatibel med .NET Core-applikationer?
Ja, GroupDocs.Parser stöder .NET Core tillsammans med .NET Framework.
### Vilka dokumentformat stöder GroupDocs.Parser?
GroupDocs.Parser stöder ett brett utbud av format inklusive PDF, Microsoft Word, Excel, PowerPoint och mer.
### Hur kan jag hantera stora dokument med GroupDocs.Parser?
GroupDocs.Parser erbjuder alternativ för att extrahera data från specifika sidor eller delar av stora dokument, vilket säkerställer effektiv bearbetning.
### Kan jag använda GroupDocs.Parser endast för textextraktion?
Ja, du kan extrahera oformaterad text från dokument med hjälp av GroupDocs.Parser utan behov av komplex formatering.