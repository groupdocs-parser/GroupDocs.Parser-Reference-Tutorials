---
title: Textsuche nach Stichwort
linktitle: Textsuche nach Stichwort
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET nach Schlüsselwörtern in Dokumenten suchen. Extrahieren Sie effizient und mühelos relevante Inhalte.
weight: 21
url: /de/net/text-extraction/search-text-by-keyword/
---
## Einführung
In diesem Tutorial werden wir uns mit der Verwendung von GroupDocs.Parser für .NET befassen, um Text in Dokumenten nach Schlüsselwörtern zu suchen. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler Text, Metadaten und andere Informationen aus verschiedenen Dateiformaten wie PDFs, Microsoft Office-Dokumenten und mehr extrahieren können. Die Suche nach bestimmten Schlüsselwörtern in diesen Dokumenten kann für Anwendungen, die mit großen Mengen an Textdaten arbeiten, von entscheidender Bedeutung sein.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
1. Entwicklungsumgebung: Visual Studio oder eine bevorzugte .NET IDE.
2.  GroupDocs.Parser für .NET: Laden Sie die Bibliothek herunter von[Hier](https://releases.groupdocs.com/parser/net/).
3. Zugriff auf Beispieldateien: Bereiten Sie eine Beispieldatei (z. B. PDF, DOCX) vor, um die Funktion zur Stichwortsuche zu testen.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr Projekt einbinden.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Schritt 1: Instanziieren der Parser-Klasse
 Beginnen Sie mit der Erstellung einer Instanz des`Parser` Klasse und geben Sie den Pfad zu Ihrer Beispieldatei an.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Suchen Sie nach einem Schlüsselwort
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Durch Suchergebnisse iterieren
    foreach (SearchResult result in searchResults)
    {
        //Drucken Sie den Index und den gefundenen Text
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Schritt 2: Suche nach einem Schlüsselwort
 Innerhalb der`using` Block, rufen Sie die`Search` Methode auf der`parser` Objekt und übergibt das gewünschte Schlüsselwort als Argument.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Ersetzen`"test"` durch das Schlüsselwort, nach dem Sie im Dokument suchen möchten.
## Schritt 3: Suchergebnisse durchlaufen
 Als nächstes iterieren Sie über die Suchergebnisse aus dem`Search` Methode mit einem`foreach` Schleife.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Für jede`SearchResult` Objekt`result` können Sie auf die`Position` (Index) und`Text` (der gefundene Text).

## Abschluss
 In diesem Tutorial haben wir untersucht, wie man mit GroupDocs.Parser für .NET mühelos nach Texten in Dokumenten nach Schlüsselwörtern suchen kann. Durch die Nutzung der`Search` Methode der`Parser` Klasse ermöglicht das effiziente Abrufen relevanter Textausschnitte auf Basis bestimmter Suchbegriffe.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit verschiedenen Dokumentformaten kompatibel?
Ja, GroupDocs.Parser unterstützt eine Vielzahl von Dateiformaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Kann ich mit GroupDocs.Parser erweiterte Textextraktionsvorgänge durchführen?
Auf jeden Fall! Neben der Textsuche ermöglicht GroupDocs.Parser die Extraktion von Metadaten, strukturiertem Text und mehr.
### Wo finde ich eine ausführliche Dokumentation für GroupDocs.Parser?
Entdecken Sie die komplette Dokumentation[Hier](https://tutorials.groupdocs.com/parser/net/).
### Wie kann ich Unterstützung oder Hilfe bei Fragen zu GroupDocs.Parser erhalten?
 Besuchen Sie das GroupDocs-Forum für Support und Diskussionen[Hier](https://forum.groupdocs.com/c/parser/17).
### Gibt es eine Testversion, um GroupDocs.Parser vor dem Kauf auszuwerten?
 Ja, Sie können auf die kostenlose Testversion zugreifen[Hier](https://releases.groupdocs.com/).