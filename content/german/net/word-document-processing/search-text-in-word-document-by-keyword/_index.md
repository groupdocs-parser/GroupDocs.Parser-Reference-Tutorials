---
title: Textsuche im Word-Dokument nach Stichwort
linktitle: Textsuche im Word-Dokument nach Stichwort
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET nach Text in Word-Dokumenten suchen. Extrahieren Sie effizient bestimmte Schlüsselwörter.
weight: 18
url: /de/net/word-document-processing/search-text-in-word-document-by-keyword/
---

# Textsuche im Word-Dokument nach Stichwort

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET mithilfe von C# nach bestimmtem Text in einem Word-Dokument suchen können. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler Text und Metadaten aus verschiedenen Dokumentformaten, einschließlich Word-Dokumenten, extrahieren können.
## Voraussetzungen
Stellen Sie vor dem Start sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Entwicklungsumgebung: Installieren Sie Visual Studio oder eine andere kompatible IDE.
2.  GroupDocs.Parser-Bibliothek: Laden Sie die GroupDocs.Parser-Bibliothek für .NET herunter und installieren Sie sie von der[Webseite](https://releases.groupdocs.com/parser/net/).
3. Beispiel-Word-Dokument: Bereiten Sie ein Beispiel-Word-Dokument vor, das Sie für die Textsuche verwenden können.

## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Erstellen Sie zunächst eine Instanz des`Parser` Klasse, indem Sie den Pfad zu Ihrem Word-Beispieldokument übergeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Code kommt hier rein
}
```
## Schritt 2: Suche nach einem Schlüsselwort
 Verwenden Sie als nächstes die`Search` Methode der`Parser` Klasse, um im Dokument nach einem bestimmten Schlüsselwort zu suchen.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Ersetzen`"keyword"` mit dem Text, nach dem Sie im Dokument suchen möchten.
## Schritt 3: Über Suchergebnisse iterieren
 Iterieren Sie über die Suchergebnisse mit einem`foreach` Schleife zum Zugriff auf alle`SearchResult` Objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    //Code zur Verarbeitung der einzelnen Suchergebnisse
}
```
## Schritt 4: Zugriff auf Suchergebnisdetails
 Innerhalb der Schleife können Sie die Position und den Text jedes Suchergebnisses über den`Position` Und`Text` Eigenschaften der`SearchResult` Objekt.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Dieser Codeausschnitt druckt den Index (`Position`) und der gefundene Text (`Text`) für jedes Suchergebnis an die Konsole.

## Abschluss
In diesem Tutorial haben Sie gelernt, wie Sie mit GroupDocs.Parser für .NET nach bestimmtem Text in einem Word-Dokument suchen. Diese Bibliothek bietet eine praktische Möglichkeit, Inhalte aus verschiedenen Dokumentformaten programmgesteuert zu extrahieren und zu bearbeiten.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser außer Word auch andere Dokumentformate verarbeiten?
Ja, GroupDocs.Parser unterstützt eine Vielzahl von Formaten, darunter PDF, Excel, PowerPoint und mehr.
### Ist GroupDocs.Parser mit .NET Core kompatibel?
Ja, GroupDocs.Parser ist sowohl mit .NET Framework als auch mit .NET Core kompatibel.
### Wie erhalte ich eine temporäre Lizenz für GroupDocs.Parser?
 Sie können eine temporäre Lizenz anfordern bei der[GroupDocs-Kaufseite](https://purchase.groupdocs.com/temporary-license/).
### Wo kann ich zusätzliche Unterstützung finden oder Fragen zu GroupDocs.Parser stellen?
 Besuche den[GroupDocs.Parser-Forum](https://forum.groupdocs.com/c/parser/17) für Community-Unterstützung und Diskussionen.
### Kann ich GroupDocs.Parser vor dem Kauf kostenlos testen?
 Ja, Sie können eine kostenlose Testversion herunterladen von der[GroupDocs-Veröffentlichungsseite](https://releases.groupdocs.com/).