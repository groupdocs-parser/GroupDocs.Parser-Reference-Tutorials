---
title: Textsuche nach regulären Ausdrücken (Regex)
linktitle: Textsuche nach regulären Ausdrücken (Regex)
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET mithilfe regulärer Ausdrücke nach Text in Dokumenten suchen. Extrahieren Sie mühelos spezifische Inhalte.
weight: 23
url: /de/net/text-extraction/search-text-by-regex/
---

# Textsuche nach regulären Ausdrücken (Regex)

## Einführung
In diesem Tutorial beschäftigen wir uns mit der Verwendung von GroupDocs.Parser für .NET, um Text in Dokumenten mit regulären Ausdrücken (Regex) zu suchen. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler Text und Metadaten aus verschiedenen Dateiformaten wie PDF, DOCX, XLSX und mehr extrahieren können. Die Textsuche mit regulären Ausdrücken ist besonders nützlich, um Muster oder bestimmte Inhalte in Dokumenten effizient zu finden.
## Voraussetzungen
Bevor Sie mit diesem Tutorial beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Visual Studio: Installieren Sie Visual Studio IDE für die .NET-Entwicklung.
2.  GroupDocs.Parser für .NET: Laden Sie GroupDocs.Parser für .NET herunter und installieren Sie es von[Hier](https://releases.groupdocs.com/parser/net/).
3. Beispieldatei: Bereiten Sie ein Beispieldokument (PDF, DOCX usw.) vor, um die Suchfunktion zu testen.

## Namespaces importieren
Beginnen Sie zunächst damit, die erforderlichen Namespaces in Ihren C#-Code einzubinden:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Instanziieren Sie den`Parser` Klasse, indem Sie den Pfad zu Ihrer Beispieldatei angeben:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Code kommt hier rein
}
```
 Ersetzen`"YourSampleFile.pdf"` durch den Pfad zu Ihrer eigentlichen Datei.
## Schritt 2: Suche mit regulären Ausdrücken
Definieren und führen Sie die Suche mithilfe eines regulären Ausdrucksmusters aus. So finden Sie beispielsweise numerische Sequenzen (z. B. Ganzzahlen) im Dokument:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 In diesem Beispiel`[0-9]+` ist ein reguläres Ausdrucksmuster, das mit einer oder mehreren Ziffern übereinstimmt.
## Schritt 3: Suchunterstützung prüfen
Überprüfen Sie, ob der Suchvorgang für den Dokumenttyp unterstützt wird:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Schritt 4: Suchergebnisse durchlaufen
Durchlaufen Sie die Suchergebnisse und verarbeiten Sie jede Übereinstimmung:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Diese Schleife druckt die Position und den passenden Text, der im Dokument gefunden wurde.

## Abschluss
Zusammenfassend lässt sich sagen, dass die Nutzung von GroupDocs.Parser für .NET eine effiziente Textsuche mit regulären Ausdrücken in verschiedenen Dokumentformaten ermöglicht. Mit diesem Leitfaden können Entwickler die Dokumentanalyse und die auf regulären Ausdrücken basierende Textextraktion nahtlos in ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser in verschlüsselten Dokumenten suchen?
Nein, GroupDocs.Parser kann nicht in verschlüsselten oder passwortgeschützten Dokumenten suchen.
### Unterstützt GroupDocs.Parser OCR (Optical Character Recognition)?
Nein, GroupDocs.Parser führt keine OCR durch. Es basiert auf der Textextraktion aus der internen Struktur des Dokuments.
### Kann ich mit regulären Ausdrücken nach komplexen Mustern suchen?
Ja, GroupDocs.Parser unterstützt vollwertige reguläre Ausdrücke und ermöglicht so komplexe Mustervergleiche innerhalb von Dokumenten.
### Welche Dokumentformate werden für die Textextraktion unterstützt?
GroupDocs.Parser unterstützt eine Vielzahl von Formaten, darunter PDF, DOCX, XLSX, PPTX und mehr.
### Ist GroupDocs.Parser mit .NET Core kompatibel?
Ja, GroupDocs.Parser ist für plattformübergreifende Entwicklung mit .NET Core kompatibel.