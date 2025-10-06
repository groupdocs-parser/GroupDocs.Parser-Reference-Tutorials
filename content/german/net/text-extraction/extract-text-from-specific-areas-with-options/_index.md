---
title: Extrahieren Sie Text aus bestimmten Bereichen mit Optionen
linktitle: Extrahieren Sie Text aus bestimmten Bereichen mit Optionen
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus bestimmten Bereichen in Dokumenten extrahieren. Entdecken Sie in diesem Tutorial erweiterte Optionen zur Textextraktion.
weight: 14
url: /de/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# Extrahieren Sie Text aus bestimmten Bereichen mit Optionen

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus bestimmten Bereichen eines Dokuments mithilfe anpassbarer Optionen extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler mühelos Text aus verschiedenen Dokumentformaten analysieren und extrahieren können.
## Voraussetzungen
Bevor wir mit der Codierung beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Entwicklungsumgebung: Installieren Sie Visual Studio oder eine andere .NET-Entwicklungs-IDE.
2.  GroupDocs.Parser-Bibliothek: Laden Sie GroupDocs.Parser für .NET herunter und installieren Sie es von[Hier](https://releases.groupdocs.com/parser/net/).
3. Beispieldatei: Bereiten Sie ein Beispieldokument (z. B. PDF, DOCX usw.) vor, aus dem Sie Text extrahieren können.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces importieren, um auf die Klassen und Methoden von GroupDocs.Parser zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Initialisieren Sie eine Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrer Beispieldatei angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Der Code zur Textbereichsextraktion wird hier eingefügt
}
```
## Schritt 2: Optionen für die Textbereichsextraktion definieren
 Erstellen`PageTextAreaOptions` um die Kriterien für die Textextraktion festzulegen.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
In diesem Beispiel:
- `"\\s[a-z]{2}\\s"` ist ein reguläres Ausdrucksmuster zum Abgleichen von Textbereichen, die nur Kleinbuchstaben enthalten.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` definiert das Rechteck (Position und Größe) auf der Seite, aus dem Text extrahiert werden soll.
## Schritt 3: Textbereiche extrahieren
Verwenden Sie die definierten Optionen, um Textbereiche zu extrahieren, die die angegebenen Kriterien erfüllen.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## Schritt 4: Extrahierte Textbereiche prüfen und iterieren
Überprüfen Sie, ob die Textbereichsextraktion unterstützt wird, und iterieren Sie dann über die extrahierten Bereiche.
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

## Abschluss
In diesem Tutorial haben wir erläutert, wie Sie mit GroupDocs.Parser für .NET Text aus bestimmten Bereichen eines Dokuments extrahieren. Diese Bibliothek bietet umfangreiche Funktionen zum Parsen verschiedener Dokumentformate und ist somit ein wertvolles Tool für Textextraktionsaufgaben.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Text aus gescannten Dokumenten extrahieren?
Ja, GroupDocs.Parser unterstützt OCR-basierte Textextraktion für gescannte Dokumente.
### Ist GroupDocs.Parser mit mehreren Dokumentformaten kompatibel?
Ja, es kann Text aus PDF, DOCX, XLSX, PPTX und anderen gängigen Formaten analysieren und extrahieren.
### Bietet GroupDocs.Parser Unterstützung für .NET Core?
Ja, GroupDocs.Parser ist sowohl mit .NET Core als auch mit .NET Framework kompatibel.
### Kann ich mit GroupDocs.Parser Metadaten zusammen mit Text extrahieren?
Ja, Sie können sowohl Textinhalte als auch Metadaten aus Dokumenten extrahieren.
### Gibt es eine Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion erhalten von[Hier](https://releases.groupdocs.com/).