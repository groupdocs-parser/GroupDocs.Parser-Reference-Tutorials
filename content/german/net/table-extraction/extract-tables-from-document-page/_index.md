---
title: Tabellen aus der Dokumentseite extrahieren
linktitle: Tabellen aus der Dokumentseite extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET programmgesteuert Tabellen aus Dokumenten extrahieren. Dieses umfassende Tutorial bietet eine Schritt-für-Schritt-Anleitung.
weight: 11
url: /de/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# Tabellen aus der Dokumentseite extrahieren

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Tabellen aus einer Dokumentseite extrahieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, mit verschiedenen Dokumentformaten wie PDF, DOCX, XLSX und mehr zu arbeiten. Indem wir seine Funktionen nutzen, können wir strukturierte Daten wie Tabellen effizient aus diesen Dokumenten extrahieren und die Informationen programmgesteuert bearbeiten und analysieren.
## Voraussetzungen
Stellen Sie vor dem Start sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem Computer installiert.
- Grundlegende Kenntnisse der C#- und .NET-Entwicklung.
-  GroupDocs.Parser für .NET-Bibliothek. Sie können es herunterladen von[Hier](https://releases.groupdocs.com/parser/net/).
- Zugriff auf ein Beispieldokument (PDF, DOCX usw.) mit Tabellen zur Extraktion.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:
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
 Instanziieren Sie den`Parser` Klasse, indem Sie den Pfad zu Ihrem Beispieldokument angeben:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Ihr Code wird hier fortgesetzt ...
}
```
## Schritt 2: Überprüfen Sie die Unterstützung für die Extraktion von Dokumenttabellen
Bevor Sie fortfahren, überprüfen Sie, ob das Dokument die Tabellenextraktion unterstützt:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Schritt 3: Tabellenlayout definieren
Definieren Sie das Layout der Tabellen, die aus dem Dokument extrahiert werden sollen. Geben Sie Spaltenbreiten und Zeilenhöhen entsprechend der Struktur Ihres Dokuments an:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Spaltenbreiten
    new double[] { 325, 340, 365, 395 });         // Zeilenhöhen
```
## Schritt 4: Konfigurieren Sie die Optionen zur Tabellenextraktion
Erstellen Sie Optionen zur Tabellenextraktion unter Verwendung des angegebenen Layouts:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Schritt 5: Dokumentinformationen abrufen
Holen Sie sich Informationen zum Dokument, einschließlich der Seitenzahl:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Schritt 6: Über Dokumentseiten iterieren
Durchlaufen Sie jede Seite des Dokuments, um Tabellen zu extrahieren:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Tabellen aus der aktuellen Seite extrahieren
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Über extrahierte Tabellen iterieren
    foreach (PageTableArea table in tables)
    {
        // Über die Zeilen der Tabelle iterieren
        for (int row = 0; row < table.RowCount; row++)
        {
            // Über Spalten der Tabelle iterieren
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Abrufen der Tabellenzelle
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Drucken Sie den Text der Tabellenzelle
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

## Abschluss
In diesem Tutorial haben wir den Prozess des Extrahierens von Tabellen aus Dokumentseiten mithilfe von GroupDocs.Parser für .NET behandelt. Indem Sie die angegebenen Schritte befolgen, können Sie die Tabellenextraktionsfunktion nahtlos in Ihre .NET-Anwendungen integrieren und so strukturierte Daten in Dokumenten effizient verarbeiten und bearbeiten.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser Tabellen aus allen Dokumenttypen extrahieren?
GroupDocs.Parser unterstützt verschiedene Dokumentformate wie PDF, DOCX, XLSX und mehr und ermöglicht die Tabellenextraktion aus kompatiblen Dateitypen.
### Ist GroupDocs.Parser für .NET für die Dokumentenverarbeitung im großen Maßstab geeignet?
Ja, GroupDocs.Parser ist für die effiziente Handhabung großer Dokumente konzipiert und eignet sich daher für die Verarbeitung umfangreicher Datensätze.
### Behält GroupDocs.Parser die Formatierung während der Tabellenextraktion bei?
Ja, GroupDocs.Parser behält während der Tabellenextraktion Formatierungsdetails wie Zellränder, Textstile und Ausrichtungen bei.
### Kann ich bestimmte Tabellen anhand inhaltlicher Kriterien extrahieren?
GroupDocs.Parser bietet flexible Optionen, um bestimmte Tabellen basierend auf Layoutvorlagen oder Inhaltsbedingungen für die Extraktion anzusprechen.
### Ist GroupDocs.Parser mit .NET Core kompatibel?
Ja, GroupDocs.Parser ist sowohl mit .NET Framework- als auch mit .NET Core-Umgebungen kompatibel.