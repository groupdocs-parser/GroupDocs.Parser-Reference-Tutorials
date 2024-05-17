---
title: Text mit Hervorhebungen durchsuchen
linktitle: Text mit Hervorhebungen durchsuchen
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text in Dokumenten suchen und hervorheben. Extrahieren Sie effizient wertvolle Erkenntnisse.
type: docs
weight: 24
url: /de/net/text-extraction/search-text-with-highlights/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET nach Text in einem Dokument suchen und die Suchergebnisse hervorheben können. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Sie mit verschiedenen Dokumentformaten arbeiten und Text, Metadaten und mehr extrahieren können.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Parser für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/parser/net/).
2. IDE: Verwenden Sie Visual Studio oder eine beliebige bevorzugte IDE für die .NET-Entwicklung.
3. Beispieldatei: Bereiten Sie ein Beispieldokument (z. B. PDF, DOCX) für die Textsuche vor.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr .NET-Projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Parserinstanz erstellen
 Beginnen Sie mit der Instanziierung des`Parser` Klasse mit dem Pfad zu Ihrer Beispieldatei:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ihr Code hier
}
```
## Schritt 2: Hervorhebungsoptionen definieren
 Präzisiere das`HighlightOptions` um zu konfigurieren, wie Suchergebnisse hervorgehoben werden sollen. Beispielsweise das Festlegen eines Kontextfensters von 15 Zeichen:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Schritt 3: Text suchen
Führen Sie nun eine Textsuche im Dokument durch. Geben Sie das Schlüsselwort ein, nach dem Sie suchen möchten (z. B. „lorem“):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Schritt 4: Suchergebnisse verarbeiten
Durchlaufen Sie die Suchergebnisse und zeigen Sie den gefundenen Text zusammen mit den Markierungen an:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Abschluss
In diesem Tutorial haben Sie gelernt, wie Sie mit GroupDocs.Parser für .NET nach Text in Dokumenten suchen und die Suchergebnisse hervorheben. Diese Funktion kann für die Textextraktion und -analyse in Ihren .NET-Anwendungen äußerst nützlich sein.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser für die Verarbeitung verschiedener Dokumentformate geeignet?
Ja, GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Kann ich GroupDocs.Parser verwenden, um Metadaten aus Dokumenten zu extrahieren?
Auf jeden Fall! Mit GroupDocs.Parser können Sie Metadaten, Text und strukturierte Daten aus Dokumenten extrahieren.
### Wo kann ich Unterstützung finden oder Fragen zu GroupDocs.Parser stellen?
 Besuchen Sie die[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17) für Supportanfragen.
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie haben Zugriff auf eine[Kostenlose Testphase](https://releases.groupdocs.com/) von GroupDocs.Parser, um seine Funktionen zu bewerten.
### Wie kann ich eine Lizenz für GroupDocs.Parser erwerben?
 Sie können eine Lizenz erwerben bei[Hier](https://purchase.groupdocs.com/buy) und erhalten Sie auch temporäre Lizenzen[Hier](https://purchase.groupdocs.com/temporary-license/).