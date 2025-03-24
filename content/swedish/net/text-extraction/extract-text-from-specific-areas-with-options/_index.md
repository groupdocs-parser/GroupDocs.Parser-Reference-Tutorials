---
title: Extrahera text från specifika områden med alternativ
linktitle: Extrahera text från specifika områden med alternativ
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar text från specifika områden i dokument med GroupDocs.Parser för .NET. Utforska avancerade textextraktionsalternativ med denna handledning.
weight: 14
url: /sv/net/text-extraction/extract-text-from-specific-areas-with-options/
---

# Extrahera text från specifika områden med alternativ

## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att extrahera text från specifika områden i ett dokument med hjälp av anpassningsbara alternativ. GroupDocs.Parser är ett kraftfullt bibliotek som gör det möjligt för utvecklare att analysera och extrahera text från olika dokumentformat utan ansträngning.
## Förutsättningar
Innan vi dyker in i kodningen, se till att du har följande:
1. Utvecklingsmiljö: Installera Visual Studio eller någon annan .NET-utvecklings-IDE.
2.  GroupDocs.Parser Library: Ladda ner och installera GroupDocs.Parser för .NET från[här](https://releases.groupdocs.com/parser/net/).
3. Exempelfil: Förbered ett exempeldokument (t.ex. PDF, DOCX, etc.) att extrahera text från.

## Importera namnområden
Först måste du importera de nödvändiga namnområdena för att komma åt GroupDocs.Parser-klasserna och metoderna.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Skapa en instans av Parser Class
 Initiera en instans av`Parser` klass genom att ange sökvägen till din exempelfil.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Koden för textområdesextraktion kommer hit
}
```
## Steg 2: Definiera textområdesextraktionsalternativ
 Skapa`PageTextAreaOptions` för att ange kriterierna för textextraktion.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
I det här exemplet:
- `"\\s[a-z]{2}\\s"` är ett reguljärt uttrycksmönster för att matcha textområden som endast innehåller gemener.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definierar rektangeln (position och storlek) på sidan som text ska extraheras från.
## Steg 3: Extrahera textområden
Använd de definierade alternativen för att extrahera textområden som uppfyller de angivna kriterierna.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Steg 4: Kontrollera och iterera över extraherade textområden
Kontrollera om textområdesextraktion stöds och iterera sedan över de extraherade områdena.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## Slutsats
I den här handledningen har vi täckt hur man extraherar text från specifika områden i ett dokument med GroupDocs.Parser för .NET. Det här biblioteket erbjuder omfattande möjligheter för att analysera olika dokumentformat, vilket gör det till ett värdefullt verktyg för textextraktionsuppgifter.

## FAQ's
### Kan GroupDocs.Parser extrahera text från skannade dokument?
Ja, GroupDocs.Parser stöder OCR-baserad textextraktion för skannade dokument.
### Är GroupDocs.Parser kompatibel med flera dokumentformat?
Ja, det kan analysera och extrahera text från PDF, DOCX, XLSX, PPTX och andra populära format.
### Ger GroupDocs.Parser stöd för .NET Core?
Ja, GroupDocs.Parser är kompatibel med .NET Core såväl som .NET Framework.
### Kan jag extrahera metadata tillsammans med text med GroupDocs.Parser?
Ja, du kan extrahera både textinnehåll och metadata från dokument.
### Finns det en testversion tillgänglig för GroupDocs.Parser?
 Ja, du kan få en gratis provperiod från[här](https://releases.groupdocs.com/).