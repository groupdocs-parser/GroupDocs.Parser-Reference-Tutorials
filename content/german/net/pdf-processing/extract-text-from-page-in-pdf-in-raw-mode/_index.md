---
title: Extrahieren Sie Text aus einer PDF-Seite im Raw-Modus
linktitle: Extrahieren Sie Text aus einer PDF-Seite im Raw-Modus
second_title: GroupDocs.Parser .NET API
description: Extrahieren Sie Text aus PDFs mit GroupDocs.Parser in C#. Lernen Sie die effiziente PDF-Textextraktion mit dieser leistungsstarken .NET-Bibliothek.
weight: 16
url: /de/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# Extrahieren Sie Text aus einer PDF-Seite im Raw-Modus

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Seiten in PDF-Dokumenten im Raw-Modus extrahieren. GroupDocs.Parser ist ein leistungsstarkes Tool, mit dem Entwickler programmgesteuert mit verschiedenen Dokumentformaten arbeiten können.
## Voraussetzungen
Stellen Sie vor dem Starten dieses Tutorials sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem Computer installiert.
- Grundkenntnisse der C#-Programmierung.
- GroupDocs.Parser für .NET-Bibliothek, die Sie[Hier herunterladen](https://releases.groupdocs.com/parser/net/).
- Eine Beispiel-PDF-Datei zu Testzwecken.

## Namespaces importieren
Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Instanziieren Sie zunächst die`Parser`Klasse, indem Sie den Pfad zu Ihrer Beispiel-PDF-Datei angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ihr Code kommt hier rein
}
```
## Schritt 2: Dokumentinformationen abrufen und über Seiten iterieren
Rufen Sie als Nächstes die Dokumentinformationen ab und durchlaufen Sie jede Seite, um Text zu extrahieren.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Ihr Code zur Textextraktion kommt hierhin
}
```
## Schritt 3: Text von jeder Seite extrahieren
 Innerhalb der Schleife verwenden Sie die`GetText` Methode, um Text von jeder Seite zu extrahieren und auszudrucken.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Abschluss
 In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Parser für .NET Text aus PDF-Seiten im Rohmodus extrahiert. Dieser Prozess beinhaltet die Erstellung eines`Parser` Instanz, Abrufen von Dokumentinformationen, Durchlaufen jeder Seite und Extrahieren von Text mithilfe der`GetText` Methode.

## Häufig gestellte Fragen
### Was ist GroupDocs.Parser für .NET?
GroupDocs.Parser für .NET ist eine API zur Dokumentanalyse, die es Entwicklern ermöglicht, programmgesteuert Text, Metadaten und andere Informationen aus verschiedenen Dateiformaten zu extrahieren.
### Wie lade ich GroupDocs.Parser für .NET herunter?
 Sie können die Bibliothek herunterladen von der[GroupDocs-Website](https://releases.groupdocs.com/parser/net/).
### Gibt es eine kostenlose Testversion?
 Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Parser für .NET zugreifen von[Hier](https://releases.groupdocs.com/).
### Wo finde ich Unterstützung für GroupDocs.Parser für .NET?
 Technische Hilfe und Community-Support erhalten Sie unter[GroupDocs-Forum](https://forum.groupdocs.com/c/parser/17).
### Wie kann ich eine Lizenz für GroupDocs.Parser für .NET erwerben?
 Sie können eine Lizenz erwerben bei der[Kaufseite](https://purchase.groupdocs.com/buy) oder erwerben Sie eine temporäre Lizenz[Hier](https://purchase.groupdocs.com/temporary-license/).