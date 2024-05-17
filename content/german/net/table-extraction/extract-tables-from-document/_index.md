---
title: Tabellen aus Dokument extrahieren
linktitle: Tabellen aus Dokument extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit Groupdocs.Parser für .NET Tabellen aus Dokumenten extrahieren. Folgen Sie den Anweisungen für eine detaillierte Anleitung zur Integration dieser Funktion.
type: docs
weight: 10
url: /de/net/table-extraction/extract-tables-from-document/
---
## Einführung
Groupdocs.Parser für .NET ist eine umfassende Bibliothek, die das Parsen von Dokumenten erleichtert und es Ihnen ermöglicht, wertvolle Informationen wie Tabellen, Text, Metadaten und mehr aus Dokumenten zu extrahieren. In diesem Tutorial konzentrieren wir uns speziell auf das Extrahieren von Tabellen aus Dokumenten mithilfe der Groupdocs.Parser-API.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem System installiert.
- .NET Framework oder .NET Core installiert.
- Grundkenntnisse der C#-Programmierung.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces importieren, um auf die Klassen und Methoden von Groupdocs.Parser zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Initialisieren Sie eine neue Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrem Beispieldokument angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ihr Code kommt hier rein
}
```
## Schritt 2: Überprüfen Sie die Unterstützung für die Tabellenextraktion
 Überprüfen Sie, ob das Dokument die Tabellenextraktion unterstützt. Verwenden Sie dazu`Features` Eigentum der`Parser` Klasse.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Schritt 3: Tabellenlayout definieren
Definieren Sie das Layout der Tabellen, die Sie extrahieren möchten, mit`TemplateTableLayout`. Geben Sie Spaltenbreiten und Zeilenhöhen basierend auf der Struktur Ihres Dokuments an.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Schritt 4: Optionen zur Tabellenextraktion festlegen
 Erstellen`PageTableAreaOptions` mit dem definierten Layout, um anzugeben, wie Tabellen extrahiert werden sollen.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Schritt 5: Tabellen extrahieren
 Nutzen Sie die`GetTables` Methode der`Parser` Klasse zum Extrahieren von Tabellen aus dem Dokument basierend auf den angegebenen Optionen.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Schritt 6: Tabellendaten iterieren und darauf zugreifen
Iterieren Sie durch die extrahierten Tabellen und ihre jeweiligen Zeilen und Spalten, um auf die Zellendaten zuzugreifen.
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
## Abschluss
In diesem Tutorial haben wir erläutert, wie Sie mit Groupdocs.Parser für .NET Tabellen effizient aus Dokumenten extrahieren können. Mithilfe der Funktionen dieser Bibliothek können Sie die Tabellenextraktion nahtlos in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Kann Groupdocs.Parser verschiedene Dokumentformate verarbeiten?
Ja, Groupdocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter DOCX, PDF, XLSX und mehr.
### Gibt es eine Testversion für Groupdocs.Parser für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Wie kann ich Unterstützung für Groupdocs.Parser-bezogene Abfragen erhalten?
 Besuchen Sie die[Groupdocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17) zur Hilfe.
### Wo kann ich eine Lizenz für Groupdocs.Parser erwerben?
 Sie können eine Lizenz erwerben bei[Hier](https://purchase.groupdocs.com/buy).
### Wie kann ich eine temporäre Lizenz zu Evaluierungszwecken erhalten?
 Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.groupdocs.com/temporary-license/).