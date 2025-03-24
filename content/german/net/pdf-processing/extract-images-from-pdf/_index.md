---
title: Bilder aus PDF extrahieren
linktitle: Bilder aus PDF extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Bilder aus PDF-Dokumenten extrahieren. Schritt-für-Schritt-Anleitung mit Codebeispielen.
weight: 12
url: /de/net/pdf-processing/extract-images-from-pdf/
---

# Bilder aus PDF extrahieren

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Bilder aus PDF-Dokumenten extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, in einer .NET-Umgebung mit verschiedenen Dokumentformaten wie PDF, DOCX, PPTX und mehr zu arbeiten. Wenn Sie diese Schritte befolgen, können Sie mühelos Bilder aus PDF-Dateien extrahieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
- Visual Studio auf Ihrem System installiert
- Grundkenntnisse der C#-Programmierung
-  GroupDocs.Parser für .NET-Bibliothek (Download[Hier](https://releases.groupdocs.com/parser/net/))

## Namespaces importieren
Fügen Sie zunächst die erforderlichen Namespaces in Ihre C#-Codedatei ein.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Erstellen Sie zunächst eine Instanz des`Parser`Klasse, indem Sie den Pfad zu Ihrer Beispiel-PDF-Datei angeben.
```csharp
// Erstellen Sie eine Instanz der Parser-Klasse
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Der Code zum Extrahieren von Bildern wird hier eingefügt
}
```
## Schritt 2: Bilder aus PDF extrahieren
 Innerhalb der`using` blockieren, nutzen Sie die`GetImages` Methode der`Parser` Instanz, um eine Sammlung von Bildern aus dem PDF-Dokument abzurufen.
```csharp
// Extrahieren Sie Bilder aus dem PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Schritt 3: Optionen zum Speichern von Bildern konfigurieren
Definieren Sie die Optionen, um anzugeben, wie die extrahierten Bilder gespeichert werden sollen. Hier speichern wir die Bilder im PNG-Format.
```csharp
// Erstellen Sie Optionen zum Speichern von Bildern im PNG-Format
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Schritt 4: Über extrahierte Bilder iterieren und speichern
 Durchlaufen Sie jedes Bild im`images` Sammlung und speichern Sie sie nacheinander als PNG-Dateien.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Speichern Sie das Bild als PNG-Datei
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## Abschluss
In diesem Tutorial haben wir gezeigt, wie Sie mit GroupDocs.Parser für .NET Bilder aus PDF-Dokumenten extrahieren. Indem Sie diese Schritte befolgen, können Sie die Bildextraktionsfunktion nahtlos in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit anderen Dokumentformaten kompatibel?
Ja, GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Kann ich die Optionen zur Bildextraktion ändern?
Auf jeden Fall! GroupDocs.Parser bietet verschiedene Optionen zum Anpassen der Bildextraktion, wie z. B. Bildformat und Qualitätseinstellungen.
### Benötigt GroupDocs.Parser eine Lizenz für die kommerzielle Nutzung?
 Ja, für die Verwendung von GroupDocs.Parser in Produktionsumgebungen ist eine kommerzielle Lizenz erforderlich. Mehr erfahren[Hier](https://purchase.groupdocs.com/buy).
### Wo finde ich zusätzliche Unterstützung oder Hilfe?
 Besuchen Sie den GroupDocs.Parser[Forum](https://forum.groupdocs.com/c/parser/17) für die Unterstützung und Anleitung der Community.
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion erhalten von[Hier](https://releases.groupdocs.com/) um die Funktionen von GroupDocs.Parser zu erkunden.