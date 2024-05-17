---
title: Text aus Word-Dokument extrahieren
linktitle: Text aus Word-Dokument extrahieren
second_title: GroupDocs.Parser .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Word-Dokumenten extrahieren. Schritt-für-Schritt-Anleitung mit Codebeispielen.
type: docs
weight: 15
url: /de/net/word-document-processing/extract-text-from-word-document/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Parser für .NET Text aus Word-Dokumenten extrahieren. GroupDocs.Parser ist eine leistungsstarke .NET-Bibliothek, mit der Entwickler mit verschiedenen Dokumentformaten arbeiten können, darunter Word-Dokumente, PDFs und mehr. Am Ende dieses Handbuchs können Sie mit einfachem C#-Code effizient Text aus Word-Dateien extrahieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Visual Studio (oder eine beliebige bevorzugte C#-Entwicklungsumgebung)
- GroupDocs.Parser für .NET-Bibliothek installiert (Download[Hier](https://releases.groupdocs.com/parser/net/))
- Grundkenntnisse der C#-Programmierung

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren, um auf die GroupDocs.Parser-Funktionalität zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Schritt 1: Erstellen Sie eine Instanz der Parser-Klasse
 Beginnen Sie mit der Erstellung einer Instanz des`Parser` Klasse, die den Pfad zu Ihrem Word-Dokument bereitstellt.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ihr Code zur Textextraktion kommt hierhin
}
```
 Ersetzen`"YourSampleFile.docx"` durch den Pfad zu Ihrem eigentlichen Word-Dokument.
## Schritt 2: Text in einen TextReader extrahieren
 Innerhalb der`using` Block des`Parser` verwenden Sie beispielsweise die`GetText()` Methode zum Extrahieren des Textinhalts in eine`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    // Ihr Textverarbeitungscode wird hier eingefügt
}
```
## Schritt 3: Extrahierten Text lesen und anzeigen
 Jetzt, im Inneren des`TextReader` Block können Sie den extrahierten Text aus dem Word-Dokument lesen und drucken.
```csharp
using (TextReader reader = parser.GetText())
{
    // Lesen Sie den extrahierten Text und drucken Sie ihn aus
    Console.WriteLine(reader.ReadToEnd());
}
```

## Abschluss
Herzlichen Glückwunsch! Sie haben gelernt, wie Sie mit GroupDocs.Parser für .NET Text aus Word-Dokumenten extrahieren. Mit dieser einfachen, aber leistungsstarken Bibliothek können Sie Textextraktionsfunktionen effizient in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen
### Ist GroupDocs.Parser mit allen Versionen von .NET kompatibel?
Ja, GroupDocs.Parser für .NET ist mit .NET Framework 4.6.1 und späteren Versionen kompatibel.
### Kann ich Text aus verschlüsselten oder kennwortgeschützten Word-Dokumenten extrahieren?
GroupDocs.Parser unterstützt das Extrahieren von Text aus passwortgeschützten Word-Dokumenten.
### Unterstützt GroupDocs.Parser andere Dokumentformate außer Word-Dokumenten?
Ja, GroupDocs.Parser unterstützt eine breite Palette von Dokumentformaten, darunter PDF, Excel, PowerPoint und mehr.
### Wie kann ich eine temporäre Lizenz für GroupDocs.Parser erhalten?
 Sie können eine temporäre Lizenz für GroupDocs.Parser anfordern[Hier](https://purchase.groupdocs.com/temporary-license/).
### Wo kann ich zusätzliche Unterstützung finden oder Fragen zu GroupDocs.Parser stellen?
 Sie können das GroupDocs.Parser-Forum besuchen[Hier](https://forum.groupdocs.com/c/parser/17)für Unterstützung und Diskussionen.