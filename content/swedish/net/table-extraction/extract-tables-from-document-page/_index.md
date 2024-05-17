---
title: Extrahera tabeller från dokumentsidan
linktitle: Extrahera tabeller från dokumentsidan
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du extraherar tabeller från dokument programmatiskt med GroupDocs.Parser för .NET. Denna omfattande handledning ger steg-för-steg-vägledning.
type: docs
weight: 11
url: /sv/net/table-extraction/extract-tables-from-document-page/
---
## Introduktion
I den här handledningen kommer vi att utforska hur man extraherar tabeller från en dokumentsida med GroupDocs.Parser för .NET. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare arbeta med olika dokumentformat som PDF, DOCX, XLSX och mer. Genom att utnyttja dess funktioner kan vi effektivt extrahera strukturerad data som tabeller från dessa dokument, vilket gör det möjligt för oss att manipulera och analysera informationen programmatiskt.
## Förutsättningar
Innan du börjar, se till att du har följande:
- Visual Studio installerat på din dator.
- Grundläggande förståelse för C# och .NET utveckling.
-  GroupDocs.Parser för .NET-bibliotek. Du kan ladda ner den från[här](https://releases.groupdocs.com/parser/net/).
- Tillgång till ett exempeldokument (PDF, DOCX, etc.) som innehåller tabeller för extraktion.

## Importera namnområden
Börja först med att importera de nödvändiga namnrymden i ditt C#-projekt:
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
 Instantiera`Parser` klass genom att ange sökvägen till ditt exempeldokument:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Din kod fortsätter här...
}
```
## Steg 2: Kontrollera stöd för extraktion av dokumentbord
Innan du fortsätter, kontrollera om dokumentet stöder tabellextraktion:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Steg 3: Definiera tabelllayout
Definiera layouten för tabeller som ska extraheras från dokumentet. Ange kolumnbredder och radhöjder enligt dokumentets struktur:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Kolumnbredder
    new double[] { 325, 340, 365, 395 });         // Radhöjder
```
## Steg 4: Konfigurera alternativ för tabellextraktion
Skapa alternativ för tabellextraktion med den angivna layouten:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Steg 5: Hämta dokumentinformation
Hämta information om dokumentet, inklusive antalet sidor:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Steg 6: Iterera över dokumentsidor
Iterera genom varje sida i dokumentet för att extrahera tabeller:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extrahera tabeller från den aktuella sidan
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Iterera över extraherade tabeller
    foreach (PageTableArea table in tables)
    {
        // Iterera över rader i tabellen
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iterera över kolumner i tabellen
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Hämta tabellcellen
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Skriv ut texten i tabellcellen
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Slutsats
den här handledningen täckte vi processen att extrahera tabeller från dokumentsidor med GroupDocs.Parser för .NET. Genom att följa de medföljande stegen kan du sömlöst integrera tabellextraktionsfunktioner i dina .NET-applikationer, vilket möjliggör effektiv hantering och manipulering av strukturerad data i dokument.

## FAQ's
### Kan GroupDocs.Parser extrahera tabeller från alla typer av dokument?
GroupDocs.Parser stöder olika dokumentformat som PDF, DOCX, XLSX och mer, vilket möjliggör tabellextraktion från kompatibla filtyper.
### Är GroupDocs.Parser för .NET lämplig för storskalig dokumentbehandling?
Ja, GroupDocs.Parser är utformad för att hantera stora dokument effektivt, vilket gör den lämplig för bearbetning av omfattande datauppsättningar.
### Behåller GroupDocs.Parser formatering under tabellextraktion?
Ja, GroupDocs.Parser behåller formateringsdetaljer som cellkanter, textstilar och justeringar under tabellextraktion.
### Kan jag extrahera specifika tabeller baserat på innehållskriterier?
GroupDocs.Parser erbjuder flexibla alternativ för att rikta in sig på specifika tabeller baserat på layoutmallar eller innehållsvillkor för extraktion.
### Är GroupDocs.Parser kompatibel med .NET Core?
Ja, GroupDocs.Parser är kompatibel med både .NET Framework- och .NET Core-miljöer.