---
title: Känna igen text i rektangulära områden
linktitle: Känna igen text i rektangulära områden
second_title: GroupDocs.Parser .NET API
description: Lär dig hur du känner igen text i specifika delar av dokument med GroupDocs.Parser för .NET med OCR-funktioner.
weight: 14
url: /sv/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---

# Känna igen text i rektangulära områden

## Introduktion
I den här handledningen kommer vi att utforska hur du använder GroupDocs.Parser för .NET för att känna igen text inom specifika rektangulära områden i dokument. GroupDocs.Parser är ett kraftfullt bibliotek som låter utvecklare extrahera text, metadata och mer från olika filformat, inklusive PDF, Word, Excel och PowerPoint.
## Förutsättningar
Innan vi börjar, se till att du har följande inställning:
-  GroupDocs.Parser för .NET: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/parser/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan .NET IDE.
- Exempeldokument: Ha en exempelfil (t.ex. PDF, DOCX) som innehåller text som ska kännas igen.

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till din C#-kod:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Steg 1: Initiera parserinställningar
 Börja med att ställa in`ParserSettings` med OCR-kontakten. Här kommer vi att använda Aspose OCR-kontakten på plats:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Steg 2: Skapa Parser-instans
 Nästa, instansiera`Parser` klass med de tidigare definierade inställningarna:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Koden fortsätter här
}
```
 Byta ut`"YourSampleFile.pdf"` med sökvägen till ditt dokument.
## Steg 3: Definiera OCR-rektangel
 Definiera en rektangel i dokumentet där textigenkänning ska utföras. Till exempel en rektangel som börjar kl`(0, 0)` med bredd`400` och höjd`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Steg 4: Konfigurera alternativ för textigenkänning
 Skapa`TextOptions` för att ange OCR-användning tillsammans med den definierade rektangeln:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Steg 5: Extrahera text med OCR
 Använd`GetText` metod för`Parser` instans med den konfigurerade`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Läs utdragen text eller hantera skiftlägen som inte stöds
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Slutsats
den här självstudien har vi demonstrerat hur man använder GroupDocs.Parser för .NET för att extrahera text från specifika rektangulära områden i dokument med OCR. Denna process kan ytterligare anpassas och integreras i olika applikationer för automatiska textextraktionsuppgifter.

## FAQ's
### Kan GroupDocs.Parser extrahera text från skannade dokument?
Ja, GroupDocs.Parser stöder OCR (Optical Character Recognition) för att extrahera text från skannade dokument.
### Vilka filformat stöder GroupDocs.Parser?
GroupDocs.Parser stöder ett brett utbud av filformat, inklusive PDF, DOCX, XLSX, PPTX och mer.
### Hur kan jag hantera dokument som inte stöds för textextraktion?
 Du kan kontrollera om textextraktion stöds med`TextReader` instans returnerad av`parser.GetText(options)`.
### Är GroupDocs.Parser lämplig för storskaliga textextraktionsuppgifter?
Ja, GroupDocs.Parser är utformad för att hantera storskaliga textextraktionsuppgifter effektivt.
### Var kan jag få support för GroupDocs.Parser-relaterade problem?
 För support och diskussioner, besök[GroupDocs.Parser-forum](https://forum.groupdocs.com/c/parser/17).