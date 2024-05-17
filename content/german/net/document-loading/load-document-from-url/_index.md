---
title: Dokument von URL laden
linktitle: Dokument von URL laden
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Dokumenten extrahieren. Dieses Tutorial beschreibt das Laden eines Dokuments von einer URL und das schrittweise Extrahieren von Text.
type: docs
weight: 13
url: /de/net/document-loading/load-document-from-url/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Dokumenten extrahieren können. GroupDocs.Parser ist ein leistungsstarkes Tool zum Extrahieren von Text, Metadaten und anderen Informationen aus verschiedenen Dokumentformaten wie PDF, Word, Excel und mehr. Wir werden Schritt für Schritt den Prozess des Ladens eines Dokuments von einer URL und des Extrahierens seines Textinhalts behandeln.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Visual Studio: Installieren Sie Visual Studio auf Ihrem System.
2.  GroupDocs.Parser für .NET: Laden Sie GroupDocs.Parser für .NET herunter und installieren Sie es von der[Download-Seite](https://releases.groupdocs.com/parser/net/).
3. Grundlegende Kenntnisse in C#: Vertrautheit mit der Programmiersprache C#.

## Namespaces importieren
Beginnen Sie, indem Sie die erforderlichen Namespaces in Ihren C#-Code einbinden:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Zunächst zeigen wir, wie ein Dokument von einer URL geladen und dessen Textinhalt extrahiert wird.
## Schritt 1: Dokument-URL angeben
Geben Sie die URL des Dokuments an, aus dem Sie Text extrahieren möchten:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Schritt 2: Erstellen einer Parserinstanz
 Instanziieren Sie den`Parser` Klasse mit der Dokument-URL:
```csharp
using (Parser parser = new Parser(uri))
{
    // Ihr Code kommt hier rein
}
```
## Schritt 3: Text aus dem Dokument extrahieren
 Im Inneren des`using`blockieren, verwenden`parser.GetText()` um Text aus dem Dokument zu extrahieren:
```csharp
using (TextReader reader = parser.GetText())
{
    // Ihr Code kommt hier rein
}
```
## Schritt 4: Den extrahierten Text anzeigen
Lesen und drucken Sie den extrahierten Text aus dem Dokument:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Abschluss
In diesem Tutorial haben wir die Grundlagen zum Extrahieren von Text aus einem Dokument mit GroupDocs.Parser für .NET behandelt. Wenn Sie diese Schritte befolgen, können Sie die Funktionen zum Extrahieren von Dokumenttext problemlos in Ihre C#-Anwendungen integrieren.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit verschiedenen Dokumentformaten kompatibel?
Ja, GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter PDF, Word, Excel, PowerPoint und mehr.
### Kann ich mit GroupDocs.Parser Metadaten zusammen mit Text extrahieren?
Ja, mit GroupDocs.Parser können Sie Metadaten, Text und andere Informationen aus Dokumenten extrahieren.
### Gibt es eine Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Parser erhalten von[Hier](https://releases.groupdocs.com/).
### Wo finde ich Dokumentation für GroupDocs.Parser?
 Detaillierte Dokumentation für GroupDocs.Parser ist verfügbar[Hier](https://reference.groupdocs.com/parser/net/).
### Wie erhalte ich technischen Support für GroupDocs.Parser?
Sie können technischen Support anfordern und Fragen im GroupDocs.Parser-Forum stellen[Hier](https://forum.groupdocs.com/c/parser/17).