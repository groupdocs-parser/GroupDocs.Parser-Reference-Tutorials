---
title: Extrahera tabeller från dokument
linktitle: Extrahera tabeller från dokument
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar tabeller från dokument med Groupdocs.Parser för .NET. Följ med för en detaljerad guide om hur du integrerar den här funktionen.
weight: 10
url: /sv/net/table-extraction/extract-tables-from-document/
type: docs
---
# Extrahera tabeller från dokument

## Introduktion
Groupdocs.Parser för .NET är ett omfattande bibliotek som underlättar dokumentanalys, så att du kan extrahera värdefull information som tabeller, text, metadata och mer från dokument. I den här handledningen fokuserar vi specifikt på att extrahera tabeller från dokument med hjälp av Groupdocs.Parser API.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio installerat på ditt system.
- .NET Framework eller .NET Core installerat.
- Grundläggande kunskaper i C#-programmering.

## Importera namnområden
Först måste du importera de nödvändiga namnområdena för att komma åt Groupdocs.Parser-klasserna och -metoderna.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Steg 1: Skapa en instans av Parser Class
 Initiera en ny instans av`Parser` klass genom att ange sökvägen till ditt exempeldokument.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Din kod kommer hit
}
```
## Steg 2: Kontrollera stöd för bordsextraktion
 Verifiera om dokumentet stöder tabellextraktion med hjälp av`Features` egendom av`Parser` klass.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Steg 3: Definiera tabelllayout
Definiera layouten för de tabeller du vill extrahera med`TemplateTableLayout`. Ange kolumnbredder och radhöjder baserat på dokumentets struktur.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Steg 4: Ställ in alternativ för tabellextraktion
 Skapa`PageTableAreaOptions` med den definierade layouten för att specificera hur tabeller ska extraheras.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Steg 5: Extrahera tabeller
 Använd`GetTables` metod för`Parser` klass för att extrahera tabeller från dokumentet baserat på de angivna alternativen.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Steg 6: Iterera och få åtkomst till tabelldata
Iterera genom de extraherade tabellerna och deras respektive rader och kolumner för att komma åt celldata.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Slutsats
I den här handledningen har vi täckt hur du använder Groupdocs.Parser för .NET för att extrahera tabeller från dokument effektivt. Genom att utnyttja funktionerna i detta bibliotek kan du integrera tabellextraktion i dina .NET-applikationer sömlöst.

## FAQ's
### Kan Groupdocs.Parser hantera olika dokumentformat?
Ja, Groupdocs.Parser stöder ett brett utbud av dokumentformat inklusive DOCX, PDF, XLSX och mer.
### Finns det en testversion tillgänglig för Groupdocs.Parser för .NET?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få support för Groupdocs.Parser-relaterade frågor?
 Du kan besöka[Groupdocs.Parser forum](https://forum.groupdocs.com/c/parser/17) för assistens.
### Var kan jag köpa en licens för Groupdocs.Parser?
 Du kan köpa en licens från[här](https://purchase.groupdocs.com/buy).
### Hur kan jag få en tillfällig licens för utvärderingsändamål?
 Du kan få en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).