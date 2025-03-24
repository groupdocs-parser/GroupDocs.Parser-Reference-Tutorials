---
title: Erkennen von Text in rechteckigen Bereichen
linktitle: Erkennen von Text in rechteckigen Bereichen
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET mit OCR-Funktionen Text in bestimmten Bereichen von Dokumenten erkennen.
weight: 14
url: /de/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---

# Erkennen von Text in rechteckigen Bereichen

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text in bestimmten rechteckigen Bereichen von Dokumenten erkennen können. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler Text, Metadaten und mehr aus verschiedenen Dateiformaten extrahieren können, darunter PDF, Word, Excel und PowerPoint.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
-  GroupDocs.Parser für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/parser/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET IDE.
- Beispieldokument: Halten Sie eine Beispieldatei (z. B. PDF, DOCX) bereit, die den zu erkennenden Text enthält.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren:
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
## Schritt 1: Parser-Einstellungen initialisieren
 Beginnen Sie mit der Einrichtung des`ParserSettings` mit dem OCR-Connector. Hier verwenden wir den Aspose OCR On-Premise-Connector:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Schritt 2: Parserinstanz erstellen
 Als nächstes instantiieren Sie den`Parser` Klasse mit den zuvor definierten Einstellungen:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Der Code wird hier fortgesetzt
}
```
 Ersetzen`"YourSampleFile.pdf"` durch den Pfad zu Ihrem Dokument.
## Schritt 3: OCR-Rechteck definieren
 Definieren Sie ein Rechteck innerhalb des Dokuments, in dem die Texterkennung durchgeführt wird. Beispielsweise ein Rechteck beginnend bei`(0, 0)` mit Breite`400` und Höhe`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Schritt 4: Konfigurieren Sie die Texterkennungsoptionen
 Erstellen`TextOptions` um die OCR-Verwendung zusammen mit dem definierten Rechteck anzugeben:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Schritt 5: Text mit OCR extrahieren
 Verwenden Sie die`GetText` Methode der`Parser` Instanz mit der konfigurierten`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Extrahierten Text lesen oder Fall „nicht unterstützt“ behandeln
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Abschluss
In diesem Tutorial haben wir gezeigt, wie Sie GroupDocs.Parser für .NET nutzen können, um mithilfe von OCR Text aus bestimmten rechteckigen Bereichen in Dokumenten zu extrahieren. Dieser Prozess kann weiter angepasst und in verschiedene Anwendungen für automatisierte Textextraktionsaufgaben integriert werden.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Text aus gescannten Dokumenten extrahieren?
Ja, GroupDocs.Parser unterstützt OCR (Optical Character Recognition) zum Extrahieren von Text aus gescannten Dokumenten.
### Welche Dateiformate unterstützt GroupDocs.Parser?
GroupDocs.Parser unterstützt eine Vielzahl von Dateiformaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Wie kann ich mit Dokumenten umgehen, deren Textextraktion nicht unterstützt wird?
 Sie können überprüfen, ob die Textextraktion unterstützt wird, indem Sie`TextReader` Instanz zurückgegeben von`parser.GetText(options)`.
### Ist GroupDocs.Parser für umfangreiche Textextraktionsaufgaben geeignet?
Ja, GroupDocs.Parser ist für die effiziente Bewältigung umfangreicher Textextraktionsaufgaben konzipiert.
### Wo erhalte ich Unterstützung bei Problemen mit GroupDocs.Parser?
 Für Unterstützung und Diskussionen besuchen Sie die[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17).