---
title: Extrahieren Sie Text aus einem Excel-Dokument als HTML
linktitle: Extrahieren Sie Text aus einem Excel-Dokument als HTML
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Excel-Dokumenten extrahieren und in HTML konvertieren.
type: docs
weight: 13
url: /de/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus einem Excel-Dokument extrahieren und in das HTML-Format konvertieren. GroupDocs.Parser ist eine leistungsstarke Bibliothek, mit der Entwickler mit verschiedenen Dokumentformaten arbeiten und Text und Metadaten effizient extrahieren können.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
- Visual Studio ist auf Ihrem System installiert.
- Grundlegende Kenntnisse der C#-Programmierung.
-  GroupDocs.Parser-Bibliothek für .NET. Sie können sie herunterladen von[Hier](https://releases.groupdocs.com/parser/net/).
## Namespaces importieren
Beginnen Sie, indem Sie die erforderlichen Namespaces in Ihr C#-Projekt einbinden, um auf die GroupDocs.Parser-Funktionen zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Instanziieren Sie zunächst die`Parser` Klasse, indem Sie den Pfad zu Ihrem Excel-Dokument angeben.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Der weitere Code kommt hierhin
}
```
 Ersetzen`"YourSampleFile.xlsx"` durch den Pfad zu Ihrer Excel-Datei.
## Schritt 2: Text als HTML extrahieren
 Innerhalb der`using` Block des`Parser` verwenden Sie beispielsweise die`GetFormattedText` Methode zum Extrahieren von formatiertem Text im HTML-Modus.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Der weitere Code kommt hierhin
    }
}
```
## Schritt 3: Extrahierten HTML-Text lesen und drucken
 Lesen Sie anschließend den extrahierten HTML-Text aus dem`TextReader` und drucken Sie es auf der Konsole aus.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Nach der Ausführung extrahiert dieser Code den Text aus dem Excel-Dokument und zeigt ihn im HTML-Format in der Konsole an.
## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Parser für .NET Text aus einem Excel-Dokument extrahiert und in das HTML-Format konvertiert. Diese Bibliothek bietet eine unkomplizierte Möglichkeit, mit verschiedenen Dokumentformaten zu arbeiten, sodass Entwickler Textextraktionsaufgaben in ihren Anwendungen effizient bewältigen können.

## Häufig gestellte Fragen
### Kann GroupDocs.Parser außer Excel auch andere Dokumentformate verarbeiten?
Ja, GroupDocs.Parser unterstützt eine Vielzahl von Dateiformaten, darunter PDF, Word, PowerPoint und mehr.
### Ist GroupDocs.Parser mit .NET Core kompatibel?
Ja, GroupDocs.Parser ist sowohl mit .NET Framework als auch mit .NET Core kompatibel.
### Behält GroupDocs.Parser die Formatierung während der Textextraktion bei?
Ja, GroupDocs.Parser kann während der Textextraktion Formatierungen wie Schriftarten, Stile und Layout beibehalten.
### Kann ich mit GroupDocs.Parser Metadaten aus Dokumenten extrahieren?
Ja, GroupDocs.Parser ermöglicht das Extrahieren von Metadaten wie Autor, Erstellungsdatum und mehr aus unterstützten Dokumenttypen.
### Gibt es eine kostenlose Testversion für GroupDocs.Parser?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).